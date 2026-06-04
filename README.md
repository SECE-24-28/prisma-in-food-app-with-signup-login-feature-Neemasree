# 🍕 Food App — Signup & Login with Prisma

A full-stack food application with user authentication built using **Next.js**, **Express**, **Prisma ORM**, and **PostgreSQL**.

## Tech Stack

- **Frontend** — Next.js 16, React 19, Tailwind CSS
- **Backend** — Express.js
- **ORM** — Prisma
- **Database** — PostgreSQL
- **Auth** — JWT (jsonwebtoken) + bcrypt

## Features

- User Signup with hashed passwords
- User Login with JWT token generation
- Protected Dashboard route (JWT middleware)
- Prisma ORM for database operations

## Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment

Create a `.env` file in the root:

```env
DATABASE_URL="postgresql://<user>:<password>@<host>:<port>/<database>"
JWT_SECRET="your_secret_key"
```

### 3. Run Prisma migrations

```bash
npx prisma migrate dev
```

### 4. Start the backend server

```bash
node index.js
```

### 5. Start the Next.js frontend

```bash
npm run dev
```

Frontend runs on `http://localhost:3000` and backend on `http://localhost:3000`.

## API Endpoints

| Method | Endpoint     | Description              | Auth Required |
|--------|-------------|--------------------------|---------------|
| GET    | `/`         | Health check             | No            |
| POST   | `/signup`   | Register a new user      | No            |
| POST   | `/login`    | Login and receive token  | No            |
| GET    | `/dashboard`| Access protected route   | Yes (Bearer)  |

### Signup Request Body

```json
{
  "username": "Neema",
  "email": "neema@example.com",
  "password": "yourpassword"
}
```

### Login Request Body

```json
{
  "email": "neema@example.com",
  "password": "yourpassword"
}
```

## Database Schema

```prisma
model User {
  id        Int      @id @default(autoincrement())
  username  String
  email     String   @unique
  password  String
  createdAt DateTime @default(now())
}
```
