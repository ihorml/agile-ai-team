# API Contracts

## Convention

- Base URL: `[BASE_URL]/api/v1`
- Format: JSON
- Authentication: Bearer token in `Authorization` header
- Pagination: `?page=1&limit=20` (default limit: 20, max: 100)
- Error format: Consistent across all endpoints (see Error Handling section)

## Endpoint Format

Every endpoint must follow this format:

```
### [METHOD] /api/v1/[path]
**Summary**: [What this endpoint does]
**Auth Required**: Yes / No
**Related Story**: US-XXX-XX

**Request**:
- Headers: [any special headers]
- Path Params: [if any]
- Query Params: [if any]
- Body:
  ```json
  {
    "field": "type — description"
  }
  ```

**Response (200)**:
  ```json
  {
    "field": "type — description"
  }
  ```

**Error Responses**:
| Status | Code | Message |
|---|---|---|
| 400 | VALIDATION_ERROR | [Description] |
| 401 | UNAUTHORIZED | [Description] |
| 404 | NOT_FOUND | [Description] |
```

## Error Handling Standard

All errors follow this format:

```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "details": {}
  }
}
```

### Standard Error Codes

| HTTP Status | Code | When to Use |
|---|---|---|
| 400 | VALIDATION_ERROR | Invalid input data |
| 401 | UNAUTHORIZED | Missing or invalid auth token |
| 403 | FORBIDDEN | Valid auth but insufficient permissions |
| 404 | NOT_FOUND | Resource does not exist |
| 409 | CONFLICT | Duplicate resource or state conflict |
| 422 | UNPROCESSABLE | Valid format but cannot process |
| 429 | RATE_LIMITED | Too many requests |
| 500 | INTERNAL_ERROR | Unexpected server error |

## Defined Endpoints

(Fill in as the project takes shape.)

### Authentication

### [POST] /api/v1/auth/register
(Use template above)

### [POST] /api/v1/auth/login
(Use template above)

### Resources

(Add resource endpoints here)
