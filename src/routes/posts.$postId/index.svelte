<script lang="ts">
  import { Link, useParams } from '@tanstack/svelte-router'

  const params = useParams({ strict: false })

  const allPosts: Record<string, { title: string; body: string }> = {
    '1': {
      title: 'Routing without a build step',
      body: 'TanStack Router runs entirely at runtime. The file-based plugin is an optional convenience.',
    },
    '2': {
      title: 'Loaders, beforeLoad, and route context',
      body: 'Routes can declare loaders and beforeLoad hooks. They run before the component renders.',
    },
    '3': {
      title: 'Search-param validation',
      body: 'Wire a Zod / Valibot / Arktype schema to a route\'s search params for validation and typing.',
    },
    '4': {
      title: 'Nested layouts with <Outlet />',
      body: 'Drop an <Outlet /> in a parent route and matching children render into it.',
    },
    '5': {
      title: 'Type-safe Link components',
      body: 'The <Link> component knows every route in your tree. Typos and missing params are compile errors.',
    },
    '6': {
      title: 'Lazy-loaded routes via file-based code-splitting',
      body: 'Every route file is imported lazily via lazyRouteComponent.',
    },
  }

  const post = $derived(allPosts[params.current?.postId as string])
</script>

{#if post}
  <h2>{post.title}</h2>
  <p>{post.body}</p>
  <p class="meta"><Link to="/posts">back to list</Link></p>
{:else}
  <h2>Not found</h2>
  <p>No post with id <code>{params.current?.postId}</code>.</p>
  <p><Link to="/posts">back to list</Link></p>
{/if}

<style>
  h2 {
    margin: 0 0 0.5rem;
  }
  .meta {
    margin-top: 1.5rem;
    color: #6b7280;
    font-size: 0.9rem;
  }
  code {
    background: #f3f4f6;
    padding: 0.1rem 0.35rem;
    border-radius: 4px;
    font-size: 0.9em;
  }
</style>
