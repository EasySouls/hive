<script lang="ts">
  import { afterNavigate, beforeNavigate } from '$app/navigation';
  import { page } from '$app/state';

  import Header from '$lib/components/shared/header.svelte';
  import NavigationLoader from '$lib/components/shared/navigation-loader.svelte';

  import '../app.css';

  let { children } = $props();

  let showNavigationLoader = $state(false);

  beforeNavigate(() => {
    showNavigationLoader = true;
  });

  afterNavigate(() => {
    showNavigationLoader = false;
  });
</script>

<svelte:head>
  {#if page.data.meta?.title}
    <title>{page.data.meta.title} - Hive</title>
  {:else}
    <title>Hive</title>
  {/if}
</svelte:head>

{#if showNavigationLoader}
  <NavigationLoader />
{/if}
<div class="flex-1">
  <Header />
  <main class="space-y-4 p-4 container">
    {@render children()}
  </main>
</div>
