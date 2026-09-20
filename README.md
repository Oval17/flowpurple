# FlowPurple — personal purple-and-white workflow platform

> Personal-use fork of [Windmill](https://github.com/windmill-labs/windmill) (via `Oval17/windmill`), rebranded and rethemed in **purple + white** for my own self-hosted use. Not affiliated with Windmill Labs.

**What changed vs upstream:**
- New name/identity: **FlowPurple** (`@flowpurple/components`)
- Full purple-and-white theme: light surfaces are white / `#F5F3FF`, accents are `#7C3AED → #6D28D9 → #5B21B6`, dark mode is a deep purple (`#1E1B2E`)
- Purple logo + loading screen (`frontend/static/logo.svg`, `frontend/src/app.html`)
- Design tokens in `frontend/src/lib/assets/tokens/tokens.json` (light, dark, dark-3)

**Upstream credit:** all workflow engine, backend (Rust), and app logic is Windmill's work under `LICENSE-AGPL`. This repo keeps all license notices intact. See `LICENSE`, `LICENSE-AGPL`, `NOTICE`.

## Self-host with Docker (local)

Requirements: Docker + Docker Compose.

```bash
cd /Users/anuragsingh/Desktop/windmill
docker compose up -d
# open http://localhost  (login: admin@windmill.dev / changeme)
```

Useful commands:

```bash
docker compose ps
docker compose logs -f windmill_server
docker compose down        # stop (keeps data)
docker compose down -v     # stop + delete all data
```

The compose stack runs: Postgres (`db`), `windmill_server`, 3× `windmill_worker`, 1× native worker, `windmill_extra` (LSP/debugger), and `caddy` on port 80.

## See the purple theme

The official `ghcr.io/windmill-labs/windmill:main` image ships upstream's built frontend, so the Docker containers above still show default colors. To run **this repo's purple frontend** against the same local backend:

```bash
cd frontend
npm install
REMOTE=http://localhost:8000 npm run dev
# open the printed http://localhost:3000 URL
```

To bake the theme into a Docker image, rebuild the full image (`docker build -t flowpurple:latest .` from repo root — needs ~8GB RAM, takes a long time) and set `WM_IMAGE=flowpurple:latest` in `.env`, then `docker compose up -d`.

## Personal notes

- Local checkout lives only at `/Users/anuragsingh/Desktop/windmill` (shallow clone, `main` branch).
- Public mirror for personal use: `https://github.com/Oval17/flowpurple`.
- License: AGPLv3 for code built from this source (see `LICENSE-AGPL`). Keep the license files if you share or deploy this.
