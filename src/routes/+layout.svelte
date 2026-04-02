<script lang="ts">
	import '../styles/app.css'
	import type { Snippet } from 'svelte'

	let { children }: { children: Snippet } = $props()
</script>

<svelte:head>
	<title>Cursor AI — Efficient Cursor: The Art of Talking to Your IDE</title>
</svelte:head>

{@render children()}
