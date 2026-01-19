# GitHub Leaderboard

A small web app that pulls issue data from the **GitHub REST API**, stores it in a database, calculates useful metrics, and displays a simple dashboard.

## Features

- **GitHub API integration** using a Personal Access Token (PAT)
- Fetches repository **issues with pagination** (up to 100 per page)
- **Rate-limit friendly** (adds a short delay between requests)
- Saves data to a database with an `Issue` model:
  - `title`
  - `author`
  - `created_at`
  - `closed_at`
- Calculates metrics:
  - **Time to close (hours)** for each closed issue
  - Flags issues taking **> 24 hours** as **Slow**
  - **Average time to close** across all closed issues
  - **Top 5 contributors** by number of opened issues
- Simple UI dashboard (Flask + Jinja templates)

## Tech Stack

- Python
- Flask
- requests
- SQLAlchemy / Flask-SQLAlchemy
- SQLite (default)
- python-dotenv

## Setup

### 1) Clone & enter the project
```bash
git clone <your-repo-url>
cd github-leaderboard
