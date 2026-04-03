<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { Action } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let iStroke = tween(0, { duration: 800 })
	let dotScale = tween(0, { duration: 400 })
	let oStroke = tween(0, { duration: 800 })
	let glowRadius = tween(0, { duration: 600 })
	let bulbOpacity = tween(0, { duration: 500 })
	let textOpacity = tween(0, { duration: 600 })

	async function playAnimation() {
		await iStroke.to(1)
		await dotScale.to(1)
		await oStroke.to(1)
		await glowRadius.to(8)
		await bulbOpacity.to(1)
		await textOpacity.to(1)
	}

	async function resetAnimation() {
		iStroke.reset(); dotScale.reset(); oStroke.reset(); glowRadius.reset(); bulbOpacity.reset(); textOpacity.reset()
	}
</script>

<Action
	actions={[
		async () => { await playAnimation() },
	]}
/>

<div class="divider-slide" style="justify-content: center; gap: 0;">
	<!-- iO logo animation -->
	<svg width="220" height="160" viewBox="0 0 220 160" style="overflow: visible;">
		<defs>
			<filter id="bulb-glow" x="-100%" y="-100%" width="300%" height="300%">
				<feGaussianBlur stdDeviation={glowRadius.current} result="blur" />
				<feMerge>
					<feMergeNode in="blur" />
					<feMergeNode in="SourceGraphic" />
				</feMerge>
			</filter>
		</defs>

		<!-- "i" stem -->
		<line
			x1="45" y1="55" x2="45" y2="130"
			stroke="#e4e4e7" stroke-width="18" stroke-linecap="round"
			pathLength="1" stroke-dasharray="1"
			style="stroke-dashoffset: {1 - iStroke.current};"
		/>

		<!-- "i" dot → lightbulb -->
		<g filter="url(#bulb-glow)" style="transform-origin: 45px 20px;">
			<path
				d="M45 8 C35 8, 33 18, 33 22 C33 28, 38 32, 40 33 L50 33 C52 32, 57 28, 57 22 C57 18, 55 8, 45 8 Z"
				fill="#a78bfa"
				style="opacity: {dotScale.current}; transform: scale({0.5 + dotScale.current * 0.5}); transform-origin: 45px 20px;"
			/>
			<rect
				x="40" y="33" width="10" height="4" rx="1"
				fill="#8b7bcc"
				style="opacity: {dotScale.current};"
			/>
			{#each [0, 45, 135, 180, 225, 270, 315] as angle}
				{@const rad = (angle * Math.PI) / 180}
				{@const x1 = 45 + 18 * Math.cos(rad)}
				{@const y1 = 20 + 18 * Math.sin(rad)}
				{@const x2 = 45 + 26 * Math.cos(rad)}
				{@const y2 = 20 + 26 * Math.sin(rad)}
				<line
					{x1} {y1} {x2} {y2}
					stroke="#a78bfa" stroke-width="2" stroke-linecap="round"
					style="opacity: {bulbOpacity.current};"
				/>
			{/each}
		</g>

		<!-- "O" -->
		<circle
			cx="145" cy="92" r="52"
			fill="none" stroke="#e4e4e7" stroke-width="18"
			pathLength="1" stroke-dasharray="1"
			style="stroke-dashoffset: {1 - oStroke.current};"
		/>
	</svg>

	<div style="display: flex; flex-direction: column; align-items: center; min-height: 220px; justify-content: flex-start; margin-top: 1.2rem;">
		<p style="font-size: 0.9rem; color: var(--text-muted); letter-spacing: 0.2em; text-transform: uppercase; opacity: {textOpacity.current};">
			presents
		</p>
		<p
			class="gradient-text"
			style="font-size: 5.5rem; font-weight: 800; letter-spacing: -0.04em; line-height: 1.1; margin-top: 1rem; opacity: {textOpacity.current};"
		>
			Cursor AI
		</p>
		<p style="font-size: 1.6rem; color: var(--text-muted); margin-top: 1rem; font-weight: 300; opacity: {textOpacity.current};">
			The Art of Talking to Your IDE
		</p>
		<div style="margin-top: 2.5rem; display: flex; flex-direction: column; align-items: center; gap: 0.4rem; opacity: {textOpacity.current};">
			<p style="font-size: 1rem; color: var(--purple); font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase;">
				R&D Knowledge Sharing
			</p>
			<p style="font-size: 0.9rem; color: var(--text-muted);">
				April 2026
			</p>
		</div>
	</div>
</div>
