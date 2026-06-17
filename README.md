# Bug Report

[Bug Report Google Doc](https://docs.google.com/document/d/1bjBPinDobbGGYf21VBRReUQeBDufZeWl0uk8loJuOFI/edit?usp=sharing)

---

# TECH ASSESSMENT - IMDB Clone

This repository contains both the frontend (React/Vite) and the backend (Node.js/Express) for the IMDB Clone application.

## Directory Structure

- `client/` - Frontend application
- `src/` - Backend source code
- `config/` - Configuration files
- `database/` - Database seeds, migrations, and SQLite file
- `logs/` - Application logs
- `uploads/` - User-uploaded files

## Prerequisites

- Node.js (v16+)
- npm

## Installation & Running Locally

1. Clone the repository and navigate to the project root.

2. Copy `.env.example` to `.env` and fill in your variables:
   ```bash
   cp .env.example .env
   ```

3. Install root and client dependencies:
   ```bash
   npm install
   cd client && npm install && cd ..
   ```

4. Create the local SQLite database file:
   - **Windows (PowerShell):**
     ```powershell
     New-Item dev.sqlite3 -Type File
     ```
   - **Mac/Linux:**
     ```bash
     touch dev.sqlite3
     ```

5. Set up the database schema and mock data:
   ```bash
   npx knex migrate:latest
   npm run seed
   ```

6. Run both the backend and frontend concurrently:
   ```bash
   npm run dev
   ```
   The frontend will start at `http://localhost:5173` (or the next available port) and the backend at `http://localhost:3000`.

7. If the frontend starts on a different port (e.g., 5174), update the `CLIENT_URL` in `.env`:
   ```
   CLIENT_URL=http://localhost:5174
   ```
   Then restart the backend.

## Environment Variables (`.env`)

```
PORT=3000
JWT_SECRET=your_jwt_secret_here
CLIENT_URL=http://localhost:5173
VITE_APP_API_URL=http://localhost:3000/api
```

## API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/api/auth/register` | No | Register a new user |
| POST | `/api/auth/login` | No | Login |
| POST | `/api/movies/get-all` | Yes | List movies (paginated) |
| GET | `/api/movies/:id` | Yes | Get movie by ID |
| POST | `/api/movies` | Yes | Create movie |
| PUT | `/api/movies/:id` | Yes | Update movie |
| DELETE | `/api/movies/:id` | Yes | Delete movie |
| POST | `/api/actors/get-all` | Yes | List actors |
| POST | `/api/actors` | Yes | Create actor |
| PUT | `/api/actors/:id` | Yes | Update actor |
| DELETE | `/api/actors/:id` | Yes | Delete actor |
| POST | `/api/producers/get-all` | Yes | List producers |
| POST | `/api/producers` | Yes | Create producer |
| PUT | `/api/producers/:id` | Yes | Update producer |
| DELETE | `/api/producers/:id` | Yes | Delete producer |

## Assumptions

- SQLite is used for local development (no external DB setup needed).
- Pre-seeded data with 5 users, 41 producers, 142 actors, and 93 movies.
- User passwords in seed data are pre-hashed with bcrypt — register a new account to log in.
- Soft-delete is used for movies (`deleted_at` column).

## Bugs Fixed

All 16 identified bugs have been fixed. See the [Bug Report Google Doc](https://docs.google.com/document/d/1bjBPinDobbGGYf21VBRReUQeBDufZeWl0uk8loJuOFI/edit?usp=sharing) for full details.
