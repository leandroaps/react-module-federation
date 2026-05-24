# React + TypeScript + Vite with Module Federation

A minimal example demonstrating Module Federation with Vite, React and TypeScript using
`@originjs/vite-plugin-federation`. This repository contains two apps:

- `host-app` — consumes remote components exposed by the remote app.
- `remote-app` — exposes a small UI component (example: `Button`).

## Features

- Module Federation with Vite
- React + TypeScript
- Simple example to experiment with micro-frontends

## Prerequisites

- Node.js 18+ (or compatible LTS)
- npm (or yarn/pnpm)

## Install

Install dependencies for each app (run these from the repository root):

```bash
cd host-app
npm install

cd ../remote-app
npm install
```

## Development

Start both apps in development mode (separate terminals):

```bash
# Terminal 1 — host
cd host-app
npm run dev

# Terminal 2 — remote
cd remote-app
npm run dev
```

Open the URL printed by Vite for the host app (usually `http://localhost:5173`) — it will dynamically load the remote module from the running remote app.

## Production preview (build + serve)

To build and preview the production bundles (this repository uses `vite preview` with fixed ports):

```bash
# Terminal 1 — host (preview on port 5000)
cd host-app
npm run serve

# Terminal 2 — remote (preview on port 5001)
cd remote-app
npm run serve
```

Then open:

- Host preview: <http://localhost:5000>
- Remote preview: <http://localhost:5001>

## Project structure (key files)

- `host-app/vite.config.ts` — Vite config and Module Federation consumer
- `host-app/src/components/RemoteComponentWrapper.tsx` — wrapper that loads the remote component
- `remote-app/vite.config.ts` — Vite config and Module Federation provider
- `remote-app/src/components/Button.tsx` — example exposed component

## How it works (tl;dr)

`@originjs/vite-plugin-federation` lets the host load JS modules exposed by the remote at runtime.
In development Vite serves the apps separately; in production the host fetches the remote build from the remote preview server.

## Next steps / Ideas

- Add automated tests and CI for both apps
- Expand exposed API surface for the remote (more components)
- Add documentation about Versioning / Shared dependencies

## License

No license specified. Add a `LICENSE` file if you want to open-source this project.
