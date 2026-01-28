# Employee List – React + Vite + MySQL (XAMPP)

A simple React app that fetches and displays employee data from the `emp_list` table in the `adrian_hrms` MySQL database on XAMPP.

## Prerequisites

- **Node.js** (v18+)
- **XAMPP** with MySQL running (default port 3306)
- Database **`adrian_hrms`** with table **`emp_list`** and columns: `emp_id`, `emp_firstname`, `emp_lastname`, `emp_city`

## Setup

### 1. Database

Ensure XAMPP MySQL is running and that `adrian_hrms` exists with `emp_list`:

```sql
SELECT emp_id, emp_firstname, emp_lastname, emp_city FROM emp_list;
```

### 2. Backend (server)

```bash
cd server
copy .env.example .env   # Windows
# cp .env.example .env  # macOS / Linux
```

Edit `server/.env` if needed (defaults: `root` user, no password, `adrian_hrms`).

```bash
npm install
npm run dev
```

API runs at **http://localhost:3001**. `GET /api/employees` returns the employee list as JSON.

### 3. Frontend (client)

In a separate terminal:

```bash
cd client
npm install
npm run dev
```

App runs at **http://localhost:5173**. The Vite dev server proxies `/api` to the backend, so the app fetches from `/api/employees`.

## Run both

From the project root:

```bash
npm run dev:server   # terminal 1
npm run dev:client   # terminal 2
```

## Project structure

- **`server/`** – Express API, `mysql2`, connects to XAMPP MySQL and exposes `GET /api/employees`
- **`client/`** – Vite + React app, fetches `/api/employees` and renders a simple table (ID, First name, Last name, City)

## Environment (server)

| Variable      | Default       | Description     |
| ------------- | ------------- | --------------- |
| `DB_HOST`     | `localhost`   | MySQL host      |
| `DB_USER`     | `root`        | MySQL user      |
| `DB_PASSWORD` | _(empty)_     | MySQL password  |
| `DB_NAME`     | `adrian_hrms` | Database name   |
| `PORT`        | `3001`        | API server port |
