<script lang="ts">
	import { enhance } from '$app/forms';
	import type { ActionData } from './$types';

	let { form }: { form: ActionData } = $props();
</script>

<h1>Sign Up</h1>
<form method="post" action="?/signup" use:enhance>
	<label>
		Username
		<input name="username" />
	</label>
	<label>
		Password
		<input type="password" name="password" />
	</label>
  <label>
    Confirm Password
    <input type="password" name="confirmPassword" />
  </label>
	<button>Sign Up</button>
</form>
<p style="color: red">{form?.message ?? ''}</p>

<p>Already have an account?</p>
<a href="/login">Login</a>