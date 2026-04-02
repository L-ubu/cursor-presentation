<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let key1 = tween(0, { duration: 300 })
	let key2 = tween(0, { duration: 300 })
	let cursorBlink = tween(0, { duration: 400 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		key1.reset(); key2.reset(); cursorBlink.reset(); textOpacity.reset()
		await key1.to(1); await key2.to(1); await cursorBlink.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="200" height="70" viewBox="0 0 200 70" style="overflow: visible;">
		<g style="opacity: {key1.current}; transform: translateY({(1 - key1.current) * 10}px);">
			<rect x="5" y="10" width="50" height="50" rx="10" fill="var(--surface)" stroke="var(--purple)" stroke-width="1.5" />
			<text x="30" y="43" text-anchor="middle" fill="var(--purple)" font-size="20" font-weight="700" font-family="Inter Variable, sans-serif">⌘</text>
		</g>
		<g style="opacity: {key2.current}; transform: translateY({(1 - key2.current) * 10}px);">
			<rect x="70" y="10" width="50" height="50" rx="10" fill="var(--surface)" stroke="var(--blue)" stroke-width="1.5" />
			<text x="95" y="43" text-anchor="middle" fill="var(--blue)" font-size="18" font-weight="700" font-family="var(--r-code-font)">L</text>
		</g>
		<g style="opacity: {cursorBlink.current};">
			<rect x="140" y="15" width="3" height="40" rx="1" fill="var(--emerald)">
				<animate attributeName="opacity" values="1;0;1" dur="1s" repeatCount="indefinite" />
			</rect>
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 2
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		The Basics
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Be productive in 5 minutes
	</p>
</div>
