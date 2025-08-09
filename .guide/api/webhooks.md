# Webhooks

## Supported Events

- note.created
- note.updated
- project.archived
- user.invited

## Delivery

- HTTPS POST to registered endpoint
- Retries with exponential backoff
- Signed payloads for security

## Example Payload

```json
{
  "event": "note.created",
  "data": {
    "note_id": "note123",
    "project_id": "proj1",
    "created": "2025-08-09T12:00:00Z"
  }
}
```

---

For webhook setup, see `integration_enterprise.md`.
