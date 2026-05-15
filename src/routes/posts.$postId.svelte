<script lang="ts">
  import { Link, Outlet, useParams } from '@tanstack/svelte-router'

  const params = useParams({ strict: false })
</script>

<article>
  <header>
    <h1>Post #{params.current?.postId}</h1>
    <nav class="tabs">
      <Link
        to="/posts/$postId"
        params={{ postId: params.current?.postId }}
        activeProps={{ class: 'active' }}
        activeOptions={{ exact: true }}
      >
        Body
      </Link>
      <Link
        to="/posts/$postId/comments"
        params={{ postId: params.current?.postId }}
        activeProps={{ class: 'active' }}
      >
        Comments
      </Link>
    </nav>
  </header>

  <Outlet />
</article>

<style>
  article {
    max-width: 640px;
  }
  header h1 {
    margin: 0 0 0.5rem;
  }
  .tabs {
    display: flex;
    gap: 1rem;
    border-bottom: 1px solid #e5e7eb;
    padding-bottom: 0.5rem;
    margin-bottom: 1rem;
    font-size: 0.95rem;
  }
  :global(.tabs a.active) {
    color: #111827;
    font-weight: 700;
  }
</style>
