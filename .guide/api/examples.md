# API Usage Examples

## Example: Get Project List

```http
GET /api/projects
Authorization: Bearer <token>
```

Response:

```json
[
  {"id": "proj1", "name": "My Novel", "created": "2025-01-01"},
  {"id": "proj2", "name": "Short Story", "created": "2025-03-15"}
]
```

## Example: Create Note

```http
POST /api/notes
Authorization: Bearer <token>
Content-Type: application/json
{
  "title": "Chapter 1",
  "content": "Once upon a time..."
}
```

Response:

```json
{"id": "note123", "status": "created"}
```

---

For more, see `openapi.yaml`.
