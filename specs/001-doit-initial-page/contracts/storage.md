# storage.md

## localStorage contract

- Key: `doit:goals:v1`
- Type: JSON array

### Item schema (Goal)

```json
{
  "id": "string",
  "title": "string",
  "end_date": "2026-04-09",
  "status": "active|completed|expired",
  "created_at": "2026-04-09T12:00:00.000Z",
  "completed_at": null,
  "archived": false
}
```

Clients SHOULD preserve unknown fields to support future schema evolution.
