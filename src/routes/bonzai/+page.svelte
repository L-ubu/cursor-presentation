<script lang="ts">
	import { Presentation } from '$lib/index.js'
	import BonzaiSlides from '$lib/components/bonzai-slides.svelte'
</script>

<svelte:head>
	<title>CRITICAL: Bonzai v2 Security Audit — iO Digital</title>
</svelte:head>

<Presentation
	options={{
		history: true,
		transition: 'slide',
		controls: true,
		progress: true,
		hash: true,
		center: true
	}}
>
	<BonzaiSlides center={true} />
</Presentation>
