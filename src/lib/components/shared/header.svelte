<script lang="ts">
  import { Button } from 'bits-ui';
  import LoginButton from './login-button.svelte';
  import type { User } from '$lib/server/db/schema';

  type HeaderProps = {
    user?: User;
  };

  let { user }: HeaderProps = $props();

  const links = [
    { name: 'Trending', href: '/trending' },
    { name: 'New', href: '/new' },
    { name: 'Top', href: '/top' },
  ];

  let isOpen = $state(false);
</script>

<header class="bg-amber-200 overflow-hidden">
  <div class="flex flex-row container mx-auto items-center justify-between">
    <h1>
      <Button.Root href="/" class="text-2xl font-bold">Hive</Button.Root>
    </h1>

    <!-- <div class='flex items-center gap-2 h-full lg:hidden'>
      <LoginButton version={0} />
      <Hamburger toggled={isOpen} toggle={setIsOpen} />
    </div> -->

    <!--Mobile View -->
    {#if isOpen}
      <div
        class="absolute top-14 left-0 right-0 bg-amber-200 flex flex-col items-start lg:hidden z-50 pl-8 pb-4"
      >
        {#each links as link}
          <Button.Root href={link.href} class="text-lg font-bold">
            {link.name}
          </Button.Root>
        {/each}
      </div>
    {/if}

    <!--Desktop View -->
    <div class="hidden lg:flex items-center gap-2 h-full">
      <LoginButton {user} />
    </div>
  </div>
</header>
