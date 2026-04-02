<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween, all } from '@animotion/motion'

	const cx = 350, cy = 160, r = 120
	const hw = 40, hh = 26

	function rectEdgeDist(angleDeg) {
		const rad = (angleDeg * Math.PI) / 180
		const dx = Math.cos(rad)
		const dy = Math.sin(rad)
		const sx = dx !== 0 ? hw / Math.abs(dx) : Infinity
		const sy = dy !== 0 ? hh / Math.abs(dy) : Infinity
		return Math.min(sx, sy)
	}

	const tools = [
		{ label: 'Jira',      color: '#60a5fa', angle: -90 },
		{ label: 'Confluence', color: '#a78bfa', angle: -30 },
		{ label: 'Figma',     color: '#f9a8d4', angle: 30 },
		{ label: 'Slack',     color: '#34d399', angle: 90 },
		{ label: 'Database',  color: '#22d3ee', angle: 150 },
		{ label: 'AWS',       color: '#fbbf24', angle: 210 },
	]

	let hubScale = tween(0, { duration: 500 })
	let toolProgress = tools.map(() => tween(0, { duration: 600 }))
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.6rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			MCP — Model Context Protocol
		</p>
	</Transition>

	<svg width="700" height="320" viewBox="0 0 700 320" style="overflow: visible;">
		<!-- center hub -->
		<g style="opacity: {hubScale.current}; transform: scale({0.5 + hubScale.current * 0.5}); transform-origin: {cx}px {cy}px;">
			<circle cx={cx} cy={cy} r="55" fill="#1e1e2e" stroke="#a78bfa" stroke-width="2.5" />
			<text x={cx} y={cy - 4} text-anchor="middle" fill="#a78bfa" font-size="18" font-weight="700" font-family="Inter Variable, sans-serif">Cursor</text>
			<text x={cx} y={cy + 18} text-anchor="middle" fill="#a1a1aa" font-size="15" font-family="Inter Variable, sans-serif">Agent</text>
		</g>

		<!-- tool nodes + connecting lines -->
		{#each tools as tool, i}
			{@const rad = (tool.angle * Math.PI) / 180}
			{@const tx = cx + r * Math.cos(rad)}
			{@const ty = cy + r * Math.sin(rad)}
			{@const hubEdgeX = cx + 58 * Math.cos(rad)}
			{@const hubEdgeY = cy + 58 * Math.sin(rad)}
			{@const edgeDist = rectEdgeDist(tool.angle)}
			{@const toolEdgeX = tx - edgeDist * Math.cos(rad)}
			{@const toolEdgeY = ty - edgeDist * Math.sin(rad)}
			{@const p = toolProgress[i].current}

			<!-- line from hub edge to tool node edge -->
			{#if p > 0.01}
				<line
					x1={hubEdgeX} y1={hubEdgeY}
					x2={hubEdgeX + (toolEdgeX - hubEdgeX) * p}
					y2={hubEdgeY + (toolEdgeY - hubEdgeY) * p}
					stroke={tool.color} stroke-width="1.5" stroke-dasharray="5 4"
					style="opacity: {Math.min(p * 2, 1)};"
				/>
			{/if}

			<!-- tool node -->
			<g style="opacity: {p}; transform: scale({0.5 + p * 0.5}); transform-origin: {tx}px {ty}px;">
				<rect x={tx - hw} y={ty - hh} width={hw * 2} height={hh * 2} rx="10" fill="#1e1e2e" stroke={tool.color} stroke-width="1.5" />
				<text x={tx} y={ty + 6} text-anchor="middle" fill={tool.color} font-size="15" font-weight="600" font-family="Inter Variable, sans-serif">{tool.label}</text>
			</g>
		{/each}
	</svg>

	<Action
		actions={[
			async () => { await hubScale.to(1) },
			async () => {
				for (const tp of toolProgress) {
					await tp.to(1)
				}
			},
		]}
	/>

	<Transition>
		<p style="font-size: 1.2rem; color: var(--text-muted);">
			One prompt. No tab switching. No copy-pasting.
		</p>
	</Transition>
</div>
