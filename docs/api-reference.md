---
layout: page
title: API Reference
---

# API Reference

Complete reference documentation for our REST API.

## Base URL

```
https://api.yourcompany.com/v1
```

## Authentication

All API requests require authentication using an API key in the Authorization header:

```
Authorization: Bearer YOUR_API_KEY
```

## Endpoints

### Status

#### Get API Status

```http
GET /status
```

Returns the current status of the API.

**Response:**
```json
{
  "status": "operational",
  "version": "1.0.0",
  "timestamp": "2025-11-29T12:00:00Z"
}
```

---

### Projects

#### List Projects

```http
GET /projects
```

Retrieve a list of all projects.

**Query Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `page` | integer | Page number (default: 1) |
| `per_page` | integer | Items per page (default: 20, max: 100) |
| `sort` | string | Sort field (default: created_at) |
| `order` | string | Sort order: asc or desc (default: desc) |

**Example Request:**
```bash
curl -X GET "https://api.yourcompany.com/v1/projects?page=1&per_page=20" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "data": [
    {
      "id": "proj_abc123",
      "name": "My Project",
      "description": "Project description",
      "created_at": "2025-11-01T10:00:00Z",
      "updated_at": "2025-11-29T12:00:00Z"
    }
  ],
  "pagination": {
    "total": 45,
    "page": 1,
    "per_page": 20,
    "total_pages": 3
  }
}
```

#### Create Project

```http
POST /projects
```

Create a new project.

**Request Body:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | Project name |
| `description` | string | No | Project description |
| `settings` | object | No | Project settings |

**Example Request:**
```bash
curl -X POST https://api.yourcompany.com/v1/projects \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "New Project",
    "description": "A new project",
    "settings": {
      "visibility": "private"
    }
  }'
```

**Response:**
```json
{
  "id": "proj_xyz789",
  "name": "New Project",
  "description": "A new project",
  "settings": {
    "visibility": "private"
  },
  "created_at": "2025-11-29T12:00:00Z",
  "updated_at": "2025-11-29T12:00:00Z"
}
```

#### Get Project

```http
GET /projects/{id}
```

Retrieve details of a specific project.

**Path Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Project ID |

**Example Request:**
```bash
curl -X GET https://api.yourcompany.com/v1/projects/proj_abc123 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "id": "proj_abc123",
  "name": "My Project",
  "description": "Project description",
  "settings": {
    "visibility": "private"
  },
  "created_at": "2025-11-01T10:00:00Z",
  "updated_at": "2025-11-29T12:00:00Z"
}
```

#### Update Project

```http
PUT /projects/{id}
```

Update an existing project.

**Path Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Project ID |

**Request Body:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | No | Project name |
| `description` | string | No | Project description |
| `settings` | object | No | Project settings |

**Example Request:**
```bash
curl -X PUT https://api.yourcompany.com/v1/projects/proj_abc123 \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Updated Project Name"
  }'
```

#### Delete Project

```http
DELETE /projects/{id}
```

Delete a project.

**Path Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Project ID |

**Example Request:**
```bash
curl -X DELETE https://api.yourcompany.com/v1/projects/proj_abc123 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "success": true,
  "message": "Project deleted successfully"
}
```

---

### Data

#### Upload Data

```http
POST /data/upload
```

Upload data to a project.

**Request Body (multipart/form-data):**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `file` | file | Yes | Data file to upload |
| `project_id` | string | Yes | Target project ID |
| `format` | string | No | File format (auto-detected if not provided) |

**Example Request:**
```bash
curl -X POST https://api.yourcompany.com/v1/data/upload \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -F "file=@data.csv" \
  -F "project_id=proj_abc123"
```

**Response:**
```json
{
  "id": "data_def456",
  "project_id": "proj_abc123",
  "filename": "data.csv",
  "size": 1024000,
  "rows": 5000,
  "status": "processing",
  "created_at": "2025-11-29T12:00:00Z"
}
```

#### Get Data

```http
GET /data/{id}
```

Retrieve uploaded data details.

**Example Request:**
```bash
curl -X GET https://api.yourcompany.com/v1/data/data_def456 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

### Users

#### Get Current User

```http
GET /users/me
```

Get information about the authenticated user.

**Example Request:**
```bash
curl -X GET https://api.yourcompany.com/v1/users/me \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "id": "user_123",
  "email": "user@example.com",
  "name": "John Doe",
  "created_at": "2025-01-15T10:00:00Z",
  "plan": "professional"
}
```

#### Update User

```http
PUT /users/me
```

Update the current user's profile.

**Request Body:**

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | No | User's name |
| `email` | string | No | User's email |

---

### Analytics

#### Get Usage Stats

```http
GET /analytics/usage
```

Get usage statistics for your account.

**Query Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `start_date` | string | Start date (ISO 8601 format) |
| `end_date` | string | End date (ISO 8601 format) |
| `granularity` | string | Data granularity: hour, day, week, month |

**Example Request:**
```bash
curl -X GET "https://api.yourcompany.com/v1/analytics/usage?start_date=2025-11-01&end_date=2025-11-30&granularity=day" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Response:**
```json
{
  "data": [
    {
      "date": "2025-11-01",
      "api_calls": 1250,
      "data_processed": 5242880,
      "projects_created": 3
    },
    {
      "date": "2025-11-02",
      "api_calls": 1150,
      "data_processed": 4718592,
      "projects_created": 1
    }
  ],
  "summary": {
    "total_api_calls": 35000,
    "total_data_processed": 157286400,
    "total_projects": 45
  }
}
```

---

## Error Responses

All error responses follow this format:

```json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable error message",
    "field": "field_name",
    "request_id": "req_abc123"
  }
}
```

### Common Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `INVALID_API_KEY` | 401 | The API key is invalid or expired |
| `INSUFFICIENT_PERMISSIONS` | 403 | You don't have permission for this action |
| `RESOURCE_NOT_FOUND` | 404 | The requested resource doesn't exist |
| `VALIDATION_ERROR` | 400 | Request validation failed |
| `RATE_LIMIT_EXCEEDED` | 429 | You've exceeded your rate limit |
| `INTERNAL_ERROR` | 500 | An internal server error occurred |

## Rate Limiting

Rate limits are enforced per API key:

| Plan | Requests per Hour |
|------|-------------------|
| Free | 1,000 |
| Professional | 10,000 |
| Enterprise | Custom |

Rate limit information is included in response headers:

```
X-RateLimit-Limit: 10000
X-RateLimit-Remaining: 9950
X-RateLimit-Reset: 1640995200
```

## Pagination

List endpoints support pagination using these parameters:

- `page`: Page number (default: 1)
- `per_page`: Items per page (default: 20, max: 100)

Pagination info is included in the response:

```json
{
  "data": [...],
  "pagination": {
    "total": 150,
    "page": 1,
    "per_page": 20,
    "total_pages": 8
  },
  "links": {
    "next": "/v1/projects?page=2",
    "prev": null
  }
}
```

## Webhooks

Subscribe to events using webhooks. See the [User Guide](/docs/user-guide/#webhooks) for setup instructions.

### Available Events

- `project.created`
- `project.updated`
- `project.deleted`
- `data.uploaded`
- `data.processed`
- `user.invited`

---

## SDKs and Libraries

Official SDKs are available for:

- [Python](https://github.com/yourcompany/python-sdk)
- [JavaScript/TypeScript](https://github.com/yourcompany/js-sdk)
- [Go](https://github.com/yourcompany/go-sdk)
- [Ruby](https://github.com/yourcompany/ruby-sdk)

## Support

Need help?

- [Getting Started Guide](/docs/getting-started/)
- [User Guide](/docs/user-guide/)
- [Code Examples](https://github.com/yourcompany/examples)
- [Contact Support](/contact/)
