<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let trunk = tween(0, { duration: 500 })
	let branch1 = tween(0, { duration: 400 })
	let branch2 = tween(0, { duration: 400 })
	let branch3 = tween(0, { duration: 400 })
	let nodes = tween(0, { duration: 300 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		trunk.reset(); branch1.reset(); branch2.reset(); branch3.reset(); nodes.reset(); textOpacity.reset()
		await trunk.to(1); await branch1.to(1); await branch2.to(1); await branch3.to(1); await nodes.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="180" height="120" viewBox="0 0 180 120" style="overflow: visible;">
		<line x1="90" y1="110" x2="90" y2="55" stroke="var(--purple)" stroke-width="2.5" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - trunk.current};" />
		<circle cx="90" cy="55" r="8" fill="var(--purple)" style="opacity: {trunk.current};" />

		<line x1="90" y1="55" x2="40" y2="25" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - branch1.current};" />
		<circle cx="40" cy="25" r="6" fill="var(--blue)" style="opacity: {nodes.current};" />
		<line x1="40" y1="25" x2="15" y2="8" stroke="var(--blue)" stroke-width="1" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - nodes.current};" />
		<circle cx="15" cy="8" r="4" fill="var(--cyan)" style="opacity: {nodes.current};" />

		<line x1="90" y1="55" x2="90" y2="10" stroke="var(--emerald)" stroke-width="1.5" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - branch2.current};" />
		<circle cx="90" cy="10" r="6" fill="var(--emerald)" style="opacity: {nodes.current};" />

		<line x1="90" y1="55" x2="145" y2="20" stroke="var(--pink)" stroke-width="1.5" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - branch3.current};" />
		<circle cx="145" cy="20" r="6" fill="var(--pink)" style="opacity: {nodes.current};" />
		<line x1="145" y1="20" x2="170" y2="5" stroke="var(--pink)" stroke-width="1" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - nodes.current};" />
		<circle cx="170" cy="5" r="4" fill="var(--cyan)" style="opacity: {nodes.current};" />
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 6
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Skills & Automation
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Active workflows that do the work
	</p>
</div>
