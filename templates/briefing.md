# Template: API Documentation

## Base URL

```
Production: https://api.example.com/v1
Staging:    https://staging-api.example.com/v1
Local:      http://localhost:3000/api/v1
```

---

## Authentication

### Headers

```
Authorization: Bearer <access_token>
Content-Type: application/json
```

### Login

```http
POST /auth/login
```

**Request:**
```json
{
  "email": "user@example.com",
  "password": "securepassword"
}
```

**Response (200):**
```json
{
  "success": true,
  "data": {
    "accessToken": "eyJhbGciOiJIUzI1NiIs...",
    "refreshToken": "eyJhbGciOiJIUzI1NiIs...",
    "user": {
      "id": "uuid",
      "email": "user@example.com",
      "name": "User Name"
    }
  }
}
```

### Refresh Token

```http
POST /auth/refresh
```

**Request:**
```json
{
  "refreshToken": "eyJhbGciOiJIUzI1NiIs..."
}
```

---

## Response Format

### Success

```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 150,
    "totalPages": 8
  }
}
```

### Error

```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message",
    "details": [
      {
        "field": "email",
        "message": "Email is required"
      }
    ]
  }
}
```

### Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `VALIDATION_ERROR` | 400 | Input validation failed |
| `UNAUTHORIZED` | 401 | Authentication required |
| `FORBIDDEN` | 403 | Permission denied |
| `NOT_FOUND` | 404 | Resource not found |
| `CONFLICT` | 409 | Resource already exists |
| `RATE_LIMITED` | 429 | Too many requests |
| `INTERNAL_ERROR` | 500 | Server error |

---

## Endpoints

### Users

#### List Users

```http
GET /users
```

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| page | number | 1 | Page number |
| limit | number | 20 | Items per page (max: 100) |
| search | string | - | Search by name or email |
| sort | string | createdAt | Sort field |
| order | string | desc | Sort order (asc/desc) |

**Response (200):**
```json
{
  "success": true,
  "data": [
    {
      "id": "uuid",
      "email": "user@example.com",
      "name": "User Name",
      "createdAt": "2024-01-15T10:30:00Z"
    }
  ],
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 150
  }
}
```

#### Get User

```http
GET /users/:id
```

**Response (200):**
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "User Name",
    "role": "user",
    "createdAt": "2024-01-15T10:30:00Z",
    "updatedAt": "2024-01-20T14:00:00Z"
  }
}
```

#### Create User

```http
POST /users
```

**Request:**
```json
{
  "email": "newuser@example.com",
  "name": "New User",
  "password": "securepassword"
}
```

**Validation:**
- `email`: Required, valid email, unique
- `name`: Required, 2-100 characters
- `password`: Required, min 8 characters

**Response (201):**
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "email": "newuser@example.com",
    "name": "New User",
    "createdAt": "2024-01-15T10:30:00Z"
  }
}
```

#### Update User

```http
PATCH /users/:id
```

**Request:**
```json
{
  "name": "Updated Name"
}
```

**Response (200):**
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "email": "user@example.com",
    "name": "Updated Name",
    "updatedAt": "2024-01-20T14:00:00Z"
  }
}
```

#### Delete User

```http
DELETE /users/:id
```

**Response (204):** No content

---

### Health Check

```http
GET /health
```

**Response (200):**
```json
{
  "status": "healthy",
  "timestamp": "2024-01-15T10:30:00Z",
  "version": "1.0.0",
  "services": {
    "database": true,
    "cache": true
  }
}
```

---

## Rate Limiting

| Endpoint | Limit | Window |
|----------|-------|--------|
| `/auth/*` | 10 | 1 minute |
| `/api/*` | 100 | 1 minute |
| `/api/upload` | 10 | 1 hour |

**Headers:**
```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1705312200
```

---

## Webhooks

### Event Types

| Event | Description |
|-------|-------------|
| `user.created` | New user registered |
| `user.updated` | User profile updated |
| `order.created` | New order placed |
| `payment.completed` | Payment processed |

### Payload

```json
{
  "id": "webhook-uuid",
  "type": "user.created",
  "timestamp": "2024-01-15T10:30:00Z",
  "data": {
    "id": "user-uuid",
    "email": "user@example.com"
  }
}
```

### Signature Verification

```typescript
import crypto from 'crypto';

function verifyWebhook(payload: string, signature: string, secret: string): boolean {
  const expected = crypto
    .createHmac('sha256', secret)
    .update(payload)
    .digest('hex');

  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(expected)
  );
}
```

---

## SDK Usage

### TypeScript/JavaScript

```typescript
import { ApiClient } from '@example/sdk';

const client = new ApiClient({
  baseUrl: 'https://api.example.com/v1',
  apiKey: 'your-api-key',
});

// List users
const users = await client.users.list({ page: 1, limit: 20 });

// Get user
const user = await client.users.get('user-uuid');

// Create user
const newUser = await client.users.create({
  email: 'new@example.com',
  name: 'New User',
  password: 'secure123',
});
```

---

## Changelog

### v1.1.0 (2024-02-01)
- Added webhook support
- New `/users/search` endpoint
- Improved rate limiting

### v1.0.0 (2024-01-15)
- Initial release
- Authentication endpoints
- User CRUD operations
