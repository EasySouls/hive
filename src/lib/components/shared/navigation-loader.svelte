<script lang='ts'>
  import { onMount } from "svelte";
  import { cubicOut } from "svelte/easing";
  import { Tween } from "svelte/motion";

  let showing = $state(false);

  const delay = 50;

  const tween = new Tween(0, {
    duration: 1000,
    easing: cubicOut,
  });

  function animate() {
    showing = true;
    tween.target = 90;
  }

  onMount(() => {
    const timeout = setTimeout(animate, delay);
    return () => clearTimeout(timeout);
  });
</script>

{#if showing}
<div class="absolute left-0 top-0 z-[999999999] h-[3px] w-screen bg-white">
  <span class="absolute h-[3px] bg-orange-500" style:width={`${tween.current}%`}></span>
</div>
{/if}