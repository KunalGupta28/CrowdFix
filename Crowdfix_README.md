# 🚀 Crowdfix Backend — API Documentation

This is the backend server for **Crowdfix**, a crowdsourced local issue reporting system.

Tech stack:
- **Node.js + Express**
- **Prisma ORM**
- **PostgreSQL (Neon DB)**
- **JWT Authentication**
- **Role-Based Access Control (User / Admin / Authority)**

---

## ✅ Base URL (Local)
```
http://localhost:4000
```

---

# 📌 AUTH ROUTES

### ✅ Register User
`POST /auth/register`

#### Request Body
```json
{
  "name": "Sarthak",
  "email": "test@test.com",
  "password": "123456",
  "role": "USER"
}
```

---

### ✅ Login
`POST /auth/login`

#### Request Body
```json
{
  "email": "test@test.com",
  "password": "123456"
}
```

---

### ✅ Get Profile (Requires Token)
`GET /auth/me`

Header:
```
Authorization: Bearer <token>
```

---

# 📌 ISSUE ROUTES

### ✅ Create Issue
`POST /issues`

Body:
```json
{
  "title": "Street light not working",
  "description": "Street light near gate 2 is dead for 3 weeks",
  "city": "Delhi",
  "latitude": 28.7041,
  "longitude": 77.1025,
  "tags": ["electricity", "public safety"]
}
```

---

### ✅ List Issues (Pagination + Sorting + Filters)
`GET /issues?page=1&limit=10&city=delhi&sort=recent`

| Query Parameter | Values | Meaning |
|----------------|--------|---------|
| `page` | `1` | Page number |
| `limit` | `10` | Issues per page |
| `sort` | `recent` / `top` | Sort by time or upvotes |
| `city` | `Delhi` | Filter by city |

---

### ✅ List My Issues
`GET /issues/my`

---

### ✅ Get Issue Details
`GET /issues/:id`

---

### ✅ Upvote Issue / Remove Upvote
`POST /issues/:id/upvote`

---

### ✅ Update Issue Status (Authority / Admin)
`PATCH /issues/:id/status`

Body:
```json
{
  "status": "RESOLVED"
}
```

---

### ✅ Delete Issue
`DELETE /issues/:id`

---

# 📌 TAG ROUTES

### ✅ Get Tags
`GET /tags`

### ✅ Create Tag (Admin Only)
`POST /tags`

Body:
```json
{
  "name": "Road Blocked"
}
```

---

# 🛠 How to Run Locally

```
npm install
npx prisma migrate dev
npm run dev
```

---

# ✅ Remaining Work

| Feature | Status |
|----------|--------|
| Comment system | ⏳ Pending |
| Notifications | ⏳ Pending |
| Admin dashboard routes | 🔴 Not started |
| Image Upload (S3 / Cloudinary) | 🔴 Not started |

---

> If you want Swagger docs or Postman collection, ask: **`Generate API docs`** or **`Generate Postman collection`**
