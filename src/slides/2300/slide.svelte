<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let termOpacity = tween(0, { duration: 400 })
	let char1 = tween(0, { duration: 150 })
	let char2 = tween(0, { duration: 150 })
	let char3 = tween(0, { duration: 150 })
	let char4 = tween(0, { duration: 150 })
	let char5 = tween(0, { duration: 150 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		termOpacity.reset(); char1.reset(); char2.reset(); char3.reset(); char4.reset(); char5.reset(); textOpacity.reset()
		await termOpacity.to(1); await char1.to(1); await char2.to(1); await char3.to(1); await char4.to(1); await char5.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="280" height="100" viewBox="0 0 280 100" style="overflow: visible;">
		<g style="opacity: {termOpacity.current};">
			<rect x="10" y="5" width="260" height="90" rx="10" fill="var(--surface)" stroke="var(--border)" stroke-width="1.5" />
			<circle cx="28" cy="20" r="4" fill="#ef4444" opacity="0.7" />
			<circle cx="42" cy="20" r="4" fill="#fbbf24" opacity="0.7" />
			<circle cx="56" cy="20" r="4" fill="#34d399" opacity="0.7" />
			<text x="25" y="52" fill="var(--emerald)" font-size="14" font-weight="700" font-family="Monaspace Neon, monospace">$</text>
			<text x="42" y="52" fill="var(--text)" font-size="14" font-family="Monaspace Neon, monospace" style="opacity: {char1.current};">a</text>
			<text x="52" y="52" fill="var(--text)" font-size="14" font-family="Monaspace Neon, monospace" style="opacity: {char2.current};">g</text>
			<text x="62" y="52" fill="var(--text)" font-size="14" font-family="Monaspace Neon, monospace" style="opacity: {char3.current};">e</text>
			<text x="72" y="52" fill="var(--text)" font-size="14" font-family="Monaspace Neon, monospace" style="opacity: {char4.current};">n</text>
			<text x="82" y="52" fill="var(--text)" font-size="14" font-family="Monaspace Neon, monospace" style="opacity: {char5.current};">t</text>
			<rect x="92" y="40" width="2" height="16" fill="var(--purple)">
				<animate attributeName="opacity" values="1;0;1" dur="1s" repeatCount="indefinite" />
			</rect>
			<text x="25" y="75" fill="var(--purple)" font-size="10" font-family="Monaspace Neon, monospace" style="opacity: {char5.current};">Starting interactive session...</text>
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 9 + 10
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		CLI & Cloud Agents
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Cursor beyond the editor
	</p>
</div>
