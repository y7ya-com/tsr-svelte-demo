# tsr-svelte-demo

Live demo of [@tanstack/svelte-router](https://github.com/y7ya-com/svelte-router)
— a community port of TanStack Router for Svelte 5.

**Open in StackBlitz:** https://stackblitz.com/github/y7ya-com/tsr-svelte-demo

## What this shows

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
pnpm install
pnpm dev
```

Opens on `http://localhost:5173`.

## Source

The actual adapter source lives in the
[`y7ya-com/router`](https://github.com/y7ya-com/router/tree/feat/svelte-router/packages/svelte-router)
fork. This demo repo just consumes the github-installable distribution.

This is an **experimental community port** — not an official TanStack
release. If/when an official `@tanstack/svelte-router` ships, swap the
`package.json` ref:

```diff
- "@tanstack/svelte-router": "github:y7ya-com/svelte-router#v0.0.0-experimental"
+ "@tanstack/svelte-router": "^1.0.0"
```
