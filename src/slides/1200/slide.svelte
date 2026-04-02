<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let check1 = tween(0, { duration: 300 })
	let check2 = tween(0, { duration: 300 })
	let check3 = tween(0, { duration: 300 })
	let listOpacity = tween(0, { duration: 400 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		check1.reset(); check2.reset(); check3.reset(); listOpacity.reset(); textOpacity.reset()
		await listOpacity.to(1); await check1.to(1); await check2.to(1); await check3.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="160" height="110" viewBox="0 0 160 110" style="overflow: visible;">
		<g style="opacity: {listOpacity.current};">
			<rect x="20" y="5" width="120" height="100" rx="10" fill="none" stroke="var(--border)" stroke-width="1.5" />
			<rect x="50" y="0" width="60" height="14" rx="4" fill="var(--surface)" stroke="var(--border)" stroke-width="1" />

			<rect x="38" y="28" width="14" height="14" rx="3" fill="none" stroke="var(--purple)" stroke-width="1.5" />
			<path d="M41 35 L44 38 L50 30" stroke="var(--purple)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" fill="none"
				pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - check1.current};" />
			<rect x="62" y="32" width="65" height="5" rx="2.5" fill="var(--surface)" />

			<rect x="38" y="52" width="14" height="14" rx="3" fill="none" stroke="var(--blue)" stroke-width="1.5" />
			<path d="M41 59 L44 62 L50 54" stroke="var(--blue)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" fill="none"
				pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - check2.current};" />
			<rect x="62" y="56" width="50" height="5" rx="2.5" fill="var(--surface)" />

			<rect x="38" y="76" width="14" height="14" rx="3" fill="none" stroke="var(--emerald)" stroke-width="1.5" />
			<path d="M41 83 L44 86 L50 78" stroke="var(--emerald)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" fill="none"
				pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - check3.current};" />
			<rect x="62" y="80" width="58" height="5" rx="2.5" fill="var(--surface)" />
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 5
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Rules
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Teach it YOUR style
	</p>
</div>
