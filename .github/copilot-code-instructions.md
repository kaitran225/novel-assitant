# COPILOT_GUIDE.md — Novel Architect (WPF / .NET 9 / Markdig / ASP.NET Web API)

## Purpose
Provide Co-Pilot with a compact, unambiguous coding brief so it generates code that matches our architecture, standards, and integration patterns. Paste this into your workspace as COPILOT_GUIDE.md and use the example prompts below when requesting code from Co-Pilot.

---

## Project Constraints (Do Not Deviate)

### Platform
- **WPF (.NET 9)** — MVVM pattern required.

### Markdown
- **Markdig NuGet** for rendering.

### Metadata/YAML
- **YamlDotNet** for front matter parsing.

### Backend
- **ASP.NET Web API** (local hostable) to wrap AI (Ollama) and auxiliary services.

### Storage
- Local-first vault (filesystem). No cloud by default.

### Concurrency
- async/await everywhere for IO and HTTP.

### DI
- Microsoft.Extensions.DependencyInjection used app-wide (including WPF bootstrap).

### Tests
- Unit tests for services (Markdown parsing, AI prompt builder, file IO).

---

## High-Level Architecture (One-Liner)
WPF (UI + ViewModels) ⇄ Local ASP.NET Web API (AI & tooling) ⇄ Local files (vault/*.md).
AI calls via HttpClient to API which proxies to Ollama/local LLM.

---

## Folder Layout (Enforce)
```bash
/NovelArchitect/
  /src/
    /NovelArchitect.UI/          # WPF app (Views, App.xaml)
    /NovelArchitect.Core/        # Models, Interfaces, Services
    /NovelArchitect.Data/        # File IO, Vault abstractions
    /NovelArchitect.API/         # ASP.NET Web API project (AI proxy)
    /NovelArchitect.Tests/       # Unit tests (xUnit/NUnit)
  /vault/                        # user markdown files (characters, scenes)
  /docs/
```

---

## Key Domain Models (C# Skeletons)

### /NovelArchitect.Core/Models/Character.cs
```csharp
public record Character(
    string Id,
    string Name,
    string Role,
    IDictionary<string,string> Metadata,
    string BodyMarkdown
);
```

### /NovelArchitect.Core/Models/Scene.cs
Similar, keep immutable records.

---

## Required Services (Single-Responsibility)

### IVaultService
Enumerate/load/save .md files; expose file change notifications.

### IMarkdownService
Render Markdig HTML and extract YAML front matter via YamlDotNet.

### IAssistantPromptBuilder
Build SYSTEM+CONTEXT prompts from Character/Scene metadata.

### IAIApiClient
Proxy client to ASP.NET Web API (not directly to LLM). Uses HttpClientFactory.

### IAssistantService
Orchestration: given Character + userMessage → returns assistant reply (calls IAssistantPromptBuilder → IApiClient).

### IGraphService
Build graph nodes/edges for connections (for UI).

**All interfaces must be asynchronous and DI-ready.**

---

## DI Registration Example (Program.cs / WPF Bootstrap)
```csharp
var services = new ServiceCollection();
// Core
services.AddSingleton<IVaultService, FileVaultService>();
services.AddSingleton<IMarkdownService, MarkdigMarkdownService>();
services.AddScoped<IAssistantPromptBuilder, AssistantPromptBuilder>();
// HTTP
services.AddHttpClient("NovelApi", c => { c.BaseAddress = new Uri("http://localhost:5000/"); });
// API client uses named client
services.AddScoped<IAIApiClient, AIApiClient>();
// ViewModels
services.AddTransient<MainViewModel>();
...
var provider = services.BuildServiceProvider();
```

---

## Markdown + YAML Front Matter Pattern

### Example vault/Characters/Cybria.md
```markdown
---
type: character
id: cybria
name: Cybria
role: protagonist
personality: "Tactical, paranoid, methodical"
backstory: "Former KVI operative, betrayed, seeks revenge"
ai_behavior: "in-character"
---
# Cybria Anastasia

Short bio here...
```

### IMarkdownService Must Return
Parsed YAML as `IDictionary<string,string>` + `string BodyMarkdown`.

---

## Markdig Rendering Rules

Use Markdig with `UseAdvancedExtensions()` and custom pipeline:

- Enable YAML front matter parsing (but still parse with YamlDotNet).
- Sanitize output if rendering to UI WebView.
- Provide both: `string RenderToHtml(string markdown)` and `FlowDocument ConvertToFlowDocument(string markdown)` for native WPF preview.

---

## ASP.NET Web API (NovelArchitect.API)

### Purpose
Centralize LLM calls, rate-limiting, auth if needed, and local testing.

### Key Endpoints

#### POST /api/ai/chat
Body: `{ "characterId": "cybria", "userMessage": "...", "mode":"in-character" }`
Response: `{ "reply": "...", "meta": {...} }`

#### GET /api/health

### Implementation Notes
- Use `IAIApiService` that wraps calls to Ollama (or other local LLMs).
- Respect cancellation tokens.
- Validate prompt length; truncate context intelligently.

---

## Assistant Prompt Strategy

### SYSTEM Prompt
Built from Character YAML (`ai_behavior`, `personality`, `backstory`).

### CONTEXT
Last N linked notes: relevant character, current scene, timeline events.

### USER
Writer's direct request.

### Return Response
With both text and structured suggestions (optional JSON with plot-beats).

**Keep prompt builder deterministic and testable — unit tests must ensure specific metadata yields expected prompt excerpts.**

---

## UI & MVVM Expectations

- Views are dumb — binding only.
- ViewModels contain commands and observable collections.
- No business logic in code-behind; only view bootstrapping and visual-only concerns (animations).
- File watchers in `IVaultService` should notify ViewModels to refresh.

---

## Async Patterns & Cancellation

- All public service methods accept `CancellationToken`.
- Use `ConfigureAwait(false)` in library code.
- In UI layer, use `Task.Run` only for CPU-bound preprocessing (e.g., heavy markdown conversion to FlowDocument).

---

## Security & Privacy

- Vault is local; do not leak files to remote by default.
- API should run locally on loopback and require a simple token in `appsettings.Development.json` if exposed beyond localhost.
- Logs should never include full prompt content by default — only hashes for debugging.

---

## Testing & CI

### Unit Tests
- MarkdownService
- VaultService
- AssistantPromptBuilder
- AIApiClient (use HttpMessageHandler mocks).

### Integration Tests
Validate end-to-end: load character → build prompt → mock API returns expected roleplay reply.

### Tools
- Use xUnit + FluentAssertions.
- Add `dotnet format` + `dotnet test` to CI pipeline.

---

## PR / Commit Checklist for Co-Pilot to Follow

When generating code, ensure:

- Methods are documented with XML comments.
- Public APIs are async and cancellation-friendly.
- No magic strings for paths or endpoints — use `IOptions<T>` pattern.
- Add unit tests for all non-trivial logic.
- Keep methods < 60 LOC; split responsibilities.

---

## Example Co-Pilot Prompts (Copy/Paste Friendly)

### Generate Service
"Generate a WPF-ready FileVaultService implementing IVaultService that enumerates vault/Characters and parses YAML front matter using YamlDotNet. Use async file IO and expose `IAsyncEnumerable<Character> GetCharactersAsync(CancellationToken)`. Include XML comments."

### Markdown Service
"Create MarkdigMarkdownService implementing IMarkdownService. Provide `Task<(IDictionary<string,string> meta, string body)> ParseFrontMatterAsync(string file, CancellationToken)` and `Task<string> RenderToHtmlAsync(string markdown, CancellationToken)`. Use Markdig's advanced extensions."

### Assistant Orchestration
"Write AssistantPromptBuilder that takes a Character model and optional `IEnumerable<Scene>` context and returns a string `BuildSystemPrompt(Character c)` applying personality and backstory. Include unit tests that assert the builder contains certain keywords from metadata."

### API Endpoint
"Add ASP.NET controller AiController with POST /api/ai/chat that validates input, uses IAIApiService to talk to local Ollama, and returns `{ reply, tokensUsed }`. Ensure CancellationToken propagation."

### ViewModel
"Create CharacterChatViewModel with `ObservableCollection<ChatMessage> Messages`, `ICommand SendCommand`, and method that calls `IAssistantService.GetReplyAsync(Character, string userMessage, CancellationToken)` and appends result. Ensure UI-friendly error handling."

---

## UX Behavior Rules for the In-Story AI

### Default Mode
In-character (responds as the character).

### Writer/Meta Mode
`/meta` prefix or UI toggle — AI gives out-of-character writing advice in a neutral tone, but retaining persona context.

### Confidence & Explain Toggle
Replies include short reasoning about suggested changes.

### Export Suggestions
Optional export suggestion as scene action that creates a new `vault/Scenes/*.md` file.

---

## Quick Examples & Snippets (For Co-Pilot to Reuse)

### HttpClientFactory Usage (AIApiClient)
```csharp
public class AIApiClient : IAIApiClient
{
    private readonly HttpClient _http;
    public AIApiClient(IHttpClientFactory factory) => _http = factory.CreateClient("NovelApi");
    public async Task<string> SendChatAsync(object payload, CancellationToken ct)
    {
        using var res = await _http.PostAsJsonAsync("api/ai/chat", payload, ct);
        res.EnsureSuccessStatusCode();
        var dto = await res.Content.ReadFromJsonAsync<AiResponseDto>(cancellationToken: ct);
        return dto!.Reply;
    }
}
```

### Markdig Pipeline
```csharp
var pipeline = new MarkdownPipelineBuilder()
    .UseAdvancedExtensions()
    .Build();
var html = Markdown.ToHtml(markdown, pipeline);
```

---

## Final Instructions for Co-Pilot

- Always ask: “Which project folder should this file go in?” when uncertain.
- Favor composition over inheritance unless a design pattern explicitly demands subclassing.
- When generating UI XAML, include minimal responsive layout (Grid with RowDefinitions) and bindings to ViewModel properties that Co-Pilot should also scaffold.
- Add TODO comments for security-sensitive choices (e.g., prompt length strategy) so humans review.