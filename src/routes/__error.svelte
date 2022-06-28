<script lang="ts">

	// Imports:
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';

	onMount(() => {
		goto('/');
	});
	
</script>