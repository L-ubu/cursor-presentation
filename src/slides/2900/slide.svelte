<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let bulbDraw = tween(0, { duration: 400 })
	let filamentDraw = tween(0, { duration: 300 })
	let baseDraw = tween(0, { duration: 250 })
	let fillGlow = tween(0, { duration: 350 })
	let sparkAngle = tween(0, { duration: 700 })
	let sparkOpacity = tween(0, { duration: 200 })
	let raysScale = tween(0, { duration: 300 })
	let textOpacity = tween(0, { duration: 300 })
	let slideEl

	const rays = [135, 165, 195, 225, 255, 285, 315, 345, 15, 45]

	async function playAnimation() {
		bulbDraw.reset(); filamentDraw.reset(); baseDraw.reset()
		fillGlow.reset(); sparkAngle.reset(); sparkOpacity.reset()
		raysScale.reset(); textOpacity.reset()

		await bulbDraw.to(1)
		await filamentDraw.to(1)
		await baseDraw.to(1)
		await fillGlow.to(1)
		sparkOpacity.to(1)
		await sparkAngle.to(1)
		await raysScale.to(1)
		await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="140" height="160" viewBox="0 0 140 160" style="overflow: visible;">
		<defs>
			<filter id="tip-glow" x="-100%" y="-100%" width="300%" height="300%">
				<feGaussianBlur stdDeviation={fillGlow.current * 10} result="blur" />
				<feMerge>
					<feMergeNode in="blur" />
					<feMergeNode in="SourceGraphic" />
				</feMerge>
			</filter>
			<linearGradient id="bulb-fill" x1="0" y1="0" x2="0" y2="1">
				<stop offset="0%" stop-color="rgba(52, 211, 153, 0.25)" />
				<stop offset="100%" stop-color="rgba(167, 139, 250, 0.15)" />
			</linearGradient>
		</defs>

		<!-- Bulb glass, drawn in -->
		<path
			d="M70 12 C42 12, 28 36, 28 55 C28 72, 42 86, 52 93 L88 93 C98 86, 112 72, 112 55 C112 36, 98 12, 70 12 Z"
			fill="none" stroke="var(--emerald)" stroke-width="2.5"
			pathLength="1" stroke-dasharray="1"
			style="stroke-dashoffset: {1 - bulbDraw.current};"
		/>

		<!-- Bulb fill, fades in -->
		<path
			d="M70 12 C42 12, 28 36, 28 55 C28 72, 42 86, 52 93 L88 93 C98 86, 112 72, 112 55 C112 36, 98 12, 70 12 Z"
			fill="url(#bulb-fill)"
			style="opacity: {fillGlow.current};"
		/>

		<!-- Filament, drawn in -->
		<g filter="url(#tip-glow)">
			<path
				d="M55 72 L60 48 L66 65 L70 42 L74 65 L80 48 L85 72"
				fill="none" stroke="var(--emerald)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
				pathLength="1" stroke-dasharray="1"
				style="stroke-dashoffset: {1 - filamentDraw.current};"
			/>
		</g>

		<!-- Spark particle orbiting the bulb -->
		<circle
			cx={70 + 48 * Math.cos((sparkAngle.current * 360 - 90) * Math.PI / 180)}
			cy={52 + 42 * Math.sin((sparkAngle.current * 360 - 90) * Math.PI / 180)}
			r="2.5"
			fill="var(--emerald)"
			style="opacity: {sparkOpacity.current * (0.5 + 0.5 * Math.sin(sparkAngle.current * Math.PI * 6))}; filter: url(#tip-glow);"
		/>

		<!-- Screw base bands, drawn in -->
		<g style="opacity: {baseDraw.current};">
			<rect x="52" y="93" width="36" height="7" rx="2" fill="none" stroke="var(--text-muted)" stroke-width="1.5" />
			<rect x="55" y="100" width="30" height="5" rx="2" fill="none" stroke="var(--text-muted)" stroke-width="1.5" />
			<rect x="58" y="105" width="24" height="5" rx="2" fill="none" stroke="var(--text-muted)" stroke-width="1.5" />
			<path d="M65 110 Q70 116 75 110" fill="none" stroke="var(--text-muted)" stroke-width="1.5" stroke-linecap="round" />
		</g>

		<!-- Radiating rays, scale out from center -->
		{#each rays as angle}
			{@const rad = (angle * Math.PI) / 180}
			{@const inner = 52 + raysScale.current * 8}
			{@const outer = 52 + raysScale.current * 22}
			<line
				x1={70 + inner * Math.cos(rad)} y1={52 + inner * Math.sin(rad)}
				x2={70 + outer * Math.cos(rad)} y2={52 + outer * Math.sin(rad)}
				stroke="var(--emerald)" stroke-width="1.5" stroke-linecap="round"
				style="opacity: {raysScale.current * 0.7};"
			/>
		{/each}
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Final
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Tips & Wrap-up
	</p>
</div>
