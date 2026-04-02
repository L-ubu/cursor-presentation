<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let hubOpacity = tween(0, { duration: 400 })
	let cableProgress = tween(0, { duration: 600 })
	let nodeOpacity = tween(0, { duration: 400 })
	let pulseOpacity = tween(0, { duration: 300 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		hubOpacity.reset(); cableProgress.reset(); nodeOpacity.reset(); pulseOpacity.reset(); textOpacity.reset()
		await hubOpacity.to(1); await cableProgress.to(1); await nodeOpacity.to(1); await pulseOpacity.to(0.8); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})

	const nodes = [
		{ label: 'Jira', x: 40, y: 20, color: 'var(--blue)' },
		{ label: 'Git', x: 160, y: 20, color: 'var(--emerald)' },
		{ label: 'DB', x: 20, y: 90, color: 'var(--pink)' },
		{ label: 'Docs', x: 180, y: 90, color: 'var(--cyan)' },
	]
	const cx = 100
	const cy = 60

</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="200" height="120" viewBox="0 0 200 120" style="overflow: visible;">
		<!-- center hub -->
		<g style="opacity: {hubOpacity.current};">
			<circle cx={cx} cy={cy} r="22" fill="var(--surface)" stroke="var(--purple)" stroke-width="2" />
			<text x={cx} y={cy + 4} text-anchor="middle" fill="var(--purple)" font-size="10" font-weight="700" font-family="Inter Variable, sans-serif">MCP</text>
		</g>

		<!-- cables from hub to each node -->
		{#each nodes as node}
			{@const dx = node.x - cx}
			{@const dy = node.y - cy}
			{@const dist = Math.sqrt(dx * dx + dy * dy)}
			{@const nx = dx / dist}
			{@const ny = dy / dist}
			{@const startX = cx + nx * 24}
			{@const startY = cy + ny * 24}
			{@const endX = node.x - nx * 16}
			{@const endY = node.y - ny * 16}
			<line
				x1={startX} y1={startY} x2={endX} y2={endY}
				stroke={node.color} stroke-width="1.5" stroke-linecap="round"
				pathLength="1" stroke-dasharray="1"
				style="stroke-dashoffset: {1 - cableProgress.current}; opacity: {hubOpacity.current};"
			/>
		{/each}

		<!-- outer nodes -->
		{#each nodes as node}
			<g style="opacity: {nodeOpacity.current};">
				<circle cx={node.x} cy={node.y} r="14" fill="var(--surface)" stroke={node.color} stroke-width="1.5" />
				<text x={node.x} y={node.y + 3.5} text-anchor="middle" fill={node.color} font-size="8" font-weight="600" font-family="Inter Variable, sans-serif">{node.label}</text>
			</g>
		{/each}

		<!-- data pulses along cables -->
		{#each nodes as node}
			{@const dx = node.x - cx}
			{@const dy = node.y - cy}
			{@const dist = Math.sqrt(dx * dx + dy * dy)}
			{@const nx = dx / dist}
			{@const ny = dy / dist}
			{@const startX = cx + nx * 24}
			{@const startY = cy + ny * 24}
			{@const endX = node.x - nx * 16}
			{@const endY = node.y - ny * 16}
			<circle r="3" fill={node.color} style="opacity: {pulseOpacity.current};">
				<animateMotion dur="1.5s" repeatCount="indefinite"
					path="M{startX},{startY} L{endX},{endY}" />
			</circle>
		{/each}
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 7 + 8
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Plugins & MCP
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Connect all the things
	</p>
</div>
