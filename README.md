# Eventually OKR Project Setup Guide

This document explains how to set up and run the Eventually OKR project locally.

---

## Prerequisites

Make sure the following are installed:

- **Node.js v25.3.0**
- **Docker** or **Podman**
- **pnpm**

If `pnpm` is not installed:

```bash
npm install -g pnpm
```

## Clone the Repository

```bash
git clone <your-repo-url>
cd <project-folder>
```

## Backend Setup

The backend lives in `eventually-backend` and uses PostgreSQL + Prisma.

1. Install backend dependencies:

```bash
cd eventually-backend
pnpm install
```

2. Start PostgreSQL with Docker/Podman:

```bash
docker compose up -d
```

3. Create/update `.env` in `eventually-backend`:

```env
DATABASE_URL="postgresql://postgres:postgres@localhost:5433/okrs"
PORT=3001
```

4. Run Prisma migrations:

```bash
pnpx prisma generate
pnpx prisma db push
```

5. Start the backend server:

```bash
pnpm run start:dev
```

Backend runs on: `http://localhost:3001`

## Frontend Setup

The frontend lives in `eventually-okr`.

1. Open a new terminal and install dependencies:

```bash
cd eventually-okr
pnpm install
```

2. Start the frontend:

```bash
pnpm run dev
```

Frontend runs on: `http://localhost:5173`

## Run the Full App

- Keep backend running in one terminal (`eventually-backend`)
- Keep frontend running in another terminal (`eventually-okr`)
- Open `http://localhost:5173` in your browser

## Useful Commands

Backend (`eventually-backend`):

```bash
pnpm run test
pnpm run test:e2e
pnpm run build
```

Frontend (`eventually-okr`):

```bash
pnpm run lint
pnpm run build
pnpm run preview
```
