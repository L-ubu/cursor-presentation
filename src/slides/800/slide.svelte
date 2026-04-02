<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let scanY = tween(0, { duration: 1200 })
	let linesOpacity = tween(0, { duration: 400 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		scanY.reset(); linesOpacity.reset(); textOpacity.reset()
		await linesOpacity.to(1); await scanY.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="160" height="120" viewBox="0 0 160 120" style="overflow: visible;">
		<g style="opacity: {linesOpacity.current};">
			{#each [15, 35, 55, 75, 95] as y, i}
				<rect x="10" {y} width={80 + (i % 3) * 20} height="6" rx="3" fill="var(--surface)" />
			{/each}
		</g>
		<rect
			x="0" y={scanY.current * 90 + 10} width="140" height="16" rx="2"
			fill="rgba(167, 139, 250, 0.1)" stroke="var(--purple)" stroke-width="0.5"
			style="opacity: {linesOpacity.current};"
		/>
		<g style="transform: translate({100 + scanY.current * 15}px, {scanY.current * 70 + 10}px);">
			<circle cx="0" cy="0" r="18" fill="none" stroke="var(--blue)" stroke-width="2.5" style="opacity: {linesOpacity.current};" />
			<line x1="13" y1="13" x2="26" y2="26" stroke="var(--blue)" stroke-width="3" stroke-linecap="round" style="opacity: {linesOpacity.current};" />
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 3
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Codebase Indexing
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		It reads everything
	</p>
</div>
