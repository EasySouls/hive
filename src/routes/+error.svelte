<script lang="ts">
    import { page } from "$app/state";
</script>

<h1>Ooops!</h1>
<p>{page.status}: {page.error?.message}</p>