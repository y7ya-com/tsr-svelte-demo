# tsr-svelte-demo

Live demos of the Svelte 5 adapter for TanStack Router and TanStack Start
(source: [`y7ya-com/router#feat/svelte`](https://github.com/y7ya-com/router/tree/feat/svelte)).

| Demo | Open |
| --- | --- |
| **Router** (this folder): client-side, file-based routing | [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/y7ya-com/tsr-svelte-demo?quickstart=1) |
| **Start** ([`start/`](./start)): SSR, server functions in loaders, `head`, `notFound()`, error boundary | [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/y7ya-com/tsr-svelte-demo?quickstart=1&devcontainer_path=.devcontainer%2Fstart%2Fdevcontainer.json) |

## Router demo: what it shows

- File-based routing with mixed flat + folder conventions
- Nested layouts via `<Outlet />`
- Dynamic path params (`/posts/$postId`)
- Reactive search params (`?filter=…`)
- Active link state via `activeProps`
- Default 404 / error components
- Lazy-loaded routes via the Vite plugin

## Route tree

```
src/routes/
├── __root.svelte             # layout for every page
├── index.svelte              # /
├── about.svelte              # /about
├── posts.svelte              # /posts layout (sidebar)
├── posts.index.svelte        # /posts/
├── posts.$postId.svelte      # /posts/$postId layout (tabs)
└── posts.$postId/
    ├── index.svelte          # /posts/$postId/ (post body)
    └── comments.svelte       # /posts/$postId/comments
```

Top-level routes use the **flat** dot-notation. Children of `$postId` use
the **folder** convention. Both work in the same tree.

## Run locally

```bash
npm install
npm run dev          # router demo, http://localhost:5173

cd start
npm install
npm run dev          # Start demo, http://localhost:3000
```


## Source

The adapter source is on the
[`feat/svelte`](https://github.com/y7ya-com/router/tree/feat/svelte/packages/svelte-router)
branch of the `y7ya-com/router` fork. This demo installs prebuilt copies of the
packages from GitHub until they are published to npm.
