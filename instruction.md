# PDFCraft — How to Launch

Quick reference for running this repo locally or with Docker.

## Prerequisites

- **Node.js** 18.17 or later
- **npm**, **yarn**, or **pnpm**
- Optional: **Docker** for containerized runs
- Optional: **Rust + Tauri** for the desktop app (`npm run dev:tauri`)

---

## Local development (recommended)

From the project root:

```bash
npm install
npm run dev
```

Open **[http://localhost:3000](http://localhost:3000)** in your browser.

### Other npm scripts

| Command | What it does |
|---------|----------------|
| `npm run dev` | Development server (Turbopack) |
| `npm run build` | Production static build → `out/` |
| `npm run start` | Serve production build (run `build` first) |
| `npm run lint` | ESLint |
| `npm run test` | Vitest |
| `npm run dev:tauri` | Tauri desktop dev (requires Tauri toolchain) |
| `npm run build:tauri` | Build Tauri desktop app |

---

## Docker

### Development (hot reload)

```bash
docker compose --profile dev up
```

App: **[http://localhost:3000](http://localhost:3000)**

### Production (static build + Nginx)

```bash
docker compose --profile prod up --build
```

App: **[http://localhost:8080](http://localhost:8080)**

Stop containers:

```bash
docker compose down
```

### Pre-built image (no clone required)

```bash
docker pull ghcr.io/pdfcrafttool/pdfcraft:latest
docker run -d -p 8080:80 --name pdfcraft ghcr.io/pdfcrafttool/pdfcraft:latest
```

Open **[http://localhost:8080](http://localhost:8080)**.

---

## Live demo

Hosted instance: [https://pdfcraft.devtoolcafe.com/en/](https://pdfcraft.devtoolcafe.com/en/)

---

## Troubleshooting

- Confirm Node version: `node -v` (must be ≥ 18.17).
- After changing dependencies, run `npm install` again.
- If port 3000 is in use, Next.js will prompt for another port or you can set one explicitly, e.g. `npm run dev -- -p 3001`.
- For full deployment options, see [README.md](README.md) and [DEPLOYMENT.md](DEPLOYMENT.md).
