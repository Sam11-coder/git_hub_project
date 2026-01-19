# GitHub Leaderboard (Mini Project)

A weekend-sized project that builds a full **data pipeline** using the GitHub API:
**Authenticate → Fetch paginated data → Store in DB → Analyze metrics → Show results on a web page.**

This is designed to mirror real-world API + dashboard work (similar to what you’ll face in roles like ZipHQ).

---

## What this app does

- Connects to the **GitHub REST API** using a **Personal Access Token (PAT)**
- Fetches **issues** from a repository (handles **pagination**)
- Saves issues into a database (schema: `Issue`)
- Calculates:
  - **Time to close** (hours)
  - Flags issues taking **> 24 hours** as **Slow**
- Displays a simple dashboard:
  - **Top 5 contributors** (who opened the most issues)
  - **Average time to close** (across all closed issues)

---

## Tech Stack (recommended)

- Python
- Flask (web app)
- Requests (API calls)
- SQLAlchemy (database)
- SQLite (local dev DB)
- Jinja2 (templates)

> You can swap SQLite for Postgres later if you want.

---

## Project Roadmap

### Phase 1 — Authentication (The Handshake)
- Create a GitHub **Personal Access Token (PAT)**
- Call GitHub API with the token
- If you see JSON back from the API: ✅ success

### Phase 2 — Pagination (The Harvest)
- GitHub returns up to **100 items per page**
- Loop over pages: `page=1, page=2, ...` until no results
- Add `sleep(1)` between requests to avoid rate-limits

### Phase 3 — Database (The Vault)
Create a table/model: `Issue` with only:

- `title` (string)
- `author` (string)
- `created_at` (datetime)
- `closed_at` (datetime)

### Phase 4 — Metrics (The Calculator)
- Compute `time_to_close_hours = closed_at - created_at`
- Mark issues **Slow** if `time_to_close_hours > 24`

### Phase 5 — Frontend (The Showroom)
Build a page showing:

- **Leaderboard**: Top 5 issue creators
- **Big Number**: Average time to close (hours)

---

## Setup

### 1) Clone and enter the project
```bash
git clone <your-repo-url>
cd github-leaderboard
