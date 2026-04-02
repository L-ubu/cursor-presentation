<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween, all } from '@animotion/motion'

	let agentPulse = tween(0, { duration: 500 })
	let beam1 = tween(0, { duration: 600 })
	let beam2 = tween(0, { duration: 600 })
	let beam3 = tween(0, { duration: 600 })
	let card1 = tween(0, { duration: 350 })
	let card2 = tween(0, { duration: 350 })
	let card3 = tween(0, { duration: 350 })
	let mergeBeams = tween(0, { duration: 500 })
	let mergeGlow = tween(0, { duration: 600 })

	const tasks = [
		{ label: 'Types', detail: 'check interfaces', color: 'var(--purple)' },
		{ label: 'Hooks', detail: 'review patterns', color: 'var(--blue)' },
		{ label: 'Tests', detail: 'check coverage', color: 'var(--emerald)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Subagents — parallel delegation
		</p>
	</Transition>

	<svg width="800" height="260" viewBox="0 0 800 260" style="overflow: visible;">
		<!-- Main Agent icon -->
		<g style="opacity: {agentPulse.current}; transform: scale({0.8 + agentPulse.current * 0.2}); transform-origin: 80px 130px;">
			<rect x="53" y="103" width="54" height="54" rx="14" fill="url(#agent-grad)" />
			<path d="M80 116 L70 121 l10 5 10-5-10-5z" fill="rgba(255,255,255,0.9)"/>
			<path d="M70 131 l10 5 10-5" stroke="rgba(255,255,255,0.6)" stroke-width="1.5" fill="none"/>
			<path d="M70 126 l10 5 10-5" stroke="rgba(255,255,255,0.4)" stroke-width="1.5" fill="none"/>
			<text x="80" y="180" text-anchor="middle" fill="var(--text)" font-size="14" font-weight="600">Main Agent</text>
		</g>

		<defs>
			<linearGradient id="agent-grad" x1="0" y1="0" x2="1" y2="1">
				<stop offset="0%" stop-color="var(--purple)" />
				<stop offset="100%" stop-color="var(--blue)" />
			</linearGradient>
			<linearGradient id="merge-grad" x1="0" y1="0" x2="1" y2="1">
				<stop offset="0%" stop-color="var(--purple)" />
				<stop offset="100%" stop-color="var(--emerald)" />
			</linearGradient>
		</defs>

		<!-- Fan-out lines: agent center (107,130) → card left edges -->
		<path d="M107 130 C180 130 220 55 280 55" fill="none" stroke="var(--purple)" stroke-width="1.5"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - beam1.current}; opacity: {beam1.current};" />
		<path d="M107 130 L280 130" fill="none" stroke="var(--blue)" stroke-width="1.5"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - beam2.current}; opacity: {beam2.current};" />
		<path d="M107 130 C180 130 220 205 280 205" fill="none" stroke="var(--emerald)" stroke-width="1.5"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - beam3.current}; opacity: {beam3.current};" />

		<!-- Task cards -->
		{#each tasks as task, i}
			{@const cardTween = [card1, card2, card3][i]}
			{@const cy = 55 + i * 75}
			<g style="opacity: {cardTween.current}; transform: translateX({(1 - cardTween.current) * 20}px);">
				<rect x="280" y={cy - 26} width="200" height="52" rx="10" fill="rgba(30, 30, 46, 0.6)" stroke={task.color} stroke-width="0" />
				<rect x="280" y={cy - 26} width="3" height="52" rx="1" fill={task.color} />
				<circle cx="298" cy={cy} r="4" fill={task.color} />
				<text x="315" y={cy - 4} fill={task.color} font-size="15" font-weight="600">{task.label}</text>
				<text x="315" y={cy + 14} fill="var(--text-muted)" font-size="13">{task.detail}</text>
			</g>
		{/each}

		<!-- Merge lines: card right edges (480) → merged result center -->
		<path d="M480 55 C540 55 560 130 620 130" fill="none" stroke="var(--purple)" stroke-width="1"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - mergeBeams.current}; opacity: {mergeBeams.current * 0.6};" />
		<path d="M480 130 L620 130" fill="none" stroke="var(--blue)" stroke-width="1"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - mergeBeams.current}; opacity: {mergeBeams.current * 0.6};" />
		<path d="M480 205 C540 205 560 130 620 130" fill="none" stroke="var(--emerald)" stroke-width="1"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - mergeBeams.current}; opacity: {mergeBeams.current * 0.6};" />

		<!-- Merged result icon -->
		<g style="opacity: {mergeGlow.current}; transform: scale({0.8 + mergeGlow.current * 0.2}); transform-origin: 647px 130px;">
			<rect x="620" y="103" width="54" height="54" rx="14" fill="url(#merge-grad)"
				style="filter: drop-shadow(0 0 {mergeGlow.current * 12}px rgba(167,139,250,0.3));" />
			<path d="M641 130 l6 6 12-12" stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
			<circle cx="647" cy="130" r="16" stroke="rgba(255,255,255,0.4)" stroke-width="1.5" fill="none"/>
			<text x="647" y="180" text-anchor="middle" fill="var(--text)" font-size="14" font-weight="600">Merged result</text>
		</g>
	</svg>

	<Action
		actions={[
			async () => { await agentPulse.to(1) },
			async () => {
				await all(beam1.to(1), beam2.to(1), beam3.to(1))
				await all(card1.to(1), card2.to(1), card3.to(1))
			},
			async () => { await mergeBeams.to(1); await mergeGlow.to(1) },
		]}
	/>

	<Transition>
		<p style="font-size: 1.05rem; color: var(--text-muted);">
			Faster + deeper analysis than a single pass.
		</p>
	</Transition>
</div>
