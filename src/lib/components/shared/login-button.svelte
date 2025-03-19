<script lang="ts">
  import { goto } from '$app/navigation';
  import type { User } from '$lib/server/db/schema';
  import { Button } from 'bits-ui';

  type LoginButtonProps = {
    user?: User;
  };

  let { user }: LoginButtonProps = $props();

  function handleGoToLogin() {
    goto('/login');
  }

  function handleGoToProfile() {
    goto(`/profile/`);
  }
</script>

{#if user}
  <Button.Root class="px-4 py-2 rounded-lg" onclick={handleGoToProfile}>
    {user.username}
  </Button.Root>
{:else}
  <Button.Root class="px-4 py-2 rounded-lg" onclick={handleGoToLogin}>
    Login
  </Button.Root>
{/if}
