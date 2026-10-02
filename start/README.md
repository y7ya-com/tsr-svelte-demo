# TanStack Start · Svelte · basic

Server-rendered routes, server functions in loaders, per-route `head`, a
thrown `notFound()`, and an error boundary — the Svelte port of
`examples/react/start-basic`.

```bash
npm run dev   # http://localhost:3000
npm run build # dist/client + dist/server
npm start     # serve the build
```

Route files are `.svelte` SFCs. Route options live in a `<script module>`
block as `export const Route = createFileRoute(...)`; the component is the
file itself.
