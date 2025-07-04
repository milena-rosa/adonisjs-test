
# AdonisJs API Example

This project is a simple API server built with [AdonisJs 4.1](https://adonisjs.com/), featuring:

- User registration and authentication (JWT)
- Tweet CRUD (create, read, delete) with user association
- RESTful routing and controllers
- Lucid ORM with migrations for users, tokens, and tweets
- Middleware for request processing

---

## Features

- **Register**: Create a new user (`/register`)
- **Authenticate**: Obtain a JWT token (`/authenticate`)
- **Tweets**: Authenticated users can create, list, view, and delete tweets (`/tweets`)

## Getting Started

### 1. Clone and Install

```bash
git clone <this-repo-url>
cd adonisjs-test
npm install
```

### 2. Environment Setup

Copy `.env.example` to `.env` and set your `APP_KEY`:

```bash
cp .env.example .env
# Generate a key (or set your own 32-char string)
node -e "console.log(require('crypto').randomBytes(16).toString('hex'))"
# Paste the result into APP_KEY in .env
```

### 3. Run Migrations

```bash
npm run start
# In another terminal:
node ace migration:run
```

### 4. Start the Server

```bash
npm start
# or
node server.js
```

Server runs on `http://127.0.0.1:3333` by default.

---

## API Endpoints

### Auth

- `POST /register` — `{ username, email, password }`
- `POST /authenticate` — `{ email, password }` (returns JWT token)

### Tweets (require JWT in Authorization header)

- `GET /tweets` — List all tweets (with user info)
- `POST /tweets` — Create tweet `{ content }`
- `GET /tweets/:id` — Get tweet by ID
- `DELETE /tweets/:id` — Delete tweet (only by owner)

---

## Project Structure

- `app/Controllers/Http/` — Controllers for auth and tweets
- `app/Models/` — Lucid models: User, Tweet, Token
- `database/migrations/` — Table schemas for users, tokens, tweets
- `start/routes.js` — Route definitions
- `start/kernel.js` — Middleware registration

---

## Development

- Edit controllers/models to add features
- Add more routes in `start/routes.js`
- Use AdonisJS docs: <https://adonisjs.com/docs/4.1/>

---

## License

UNLICENSED (for demo purposes)
