<script lang="ts">
	import { enhance } from '$app/forms';
  import { page } from '$app/state';
	import type { PageProps } from './$types';

	let { data } : PageProps = $props();
</script>

{#if data.user}
<h1>Hi, {data.user.username}!</h1>
<p>Your user ID is {data.user.id}.</p>
<form method="post" action="?/logout" use:enhance>
	<button>Sign out</button>
</form>
{:else}
<h1>Login/Register</h1>
<a href="?/login">Login</a>
{/if}