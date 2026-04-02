<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let ringDraw = tween(0, { duration: 800 })
	let ticksOpacity = tween(0, { duration: 400 })
	let hourHand = tween(0, { duration: 1000 })
	let minuteHand = tween(0, { duration: 700 })
	let glowPulse = tween(0, { duration: 600 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		ringDraw.reset(); ticksOpacity.reset(); hourHand.reset(); minuteHand.reset(); glowPulse.reset(); textOpacity.reset()
		await ringDraw.to(1)
		await ticksOpacity.to(1)
		await hourHand.to(1)
		await minuteHand.to(1)
		await glowPulse.to(1)
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
	<svg width="140" height="140" viewBox="0 0 140 140" style="overflow: visible;">
		<defs>
			<filter id="clock-glow" x="-50%" y="-50%" width="200%" height="200%">
				<feGaussianBlur stdDeviation={glowPulse.current * 6} result="blur" />
				<feMerge>
					<feMergeNode in="blur" />
					<feMergeNode in="SourceGraphic" />
				</feMerge>
			</filter>
		</defs>

		<!-- Outer ring, drawn in -->
		<circle cx="70" cy="70" r="58" fill="none" stroke="var(--purple)" stroke-width="2"
			pathLength="1" stroke-dasharray="1"
			style="stroke-dashoffset: {1 - ringDraw.current}; opacity: {0.3 + ringDraw.current * 0.7};" />

		<!-- Inner subtle ring -->
		<circle cx="70" cy="70" r="50" fill="none" stroke="var(--border)" stroke-width="1"
			style="opacity: {ticksOpacity.current * 0.4};" />

		<!-- Hour ticks -->
		<g style="opacity: {ticksOpacity.current};">
			{#each [0, 30, 60, 90, 120, 150, 180, 210, 240, 270, 300, 330] as angle}
				{@const rad = (angle * Math.PI) / 180}
				{@const isQuarter = angle % 90 === 0}
				<line
					x1={70 + (isQuarter ? 43 : 47) * Math.cos(rad)}
					y1={70 + (isQuarter ? 43 : 47) * Math.sin(rad)}
					x2={70 + 52 * Math.cos(rad)}
					y2={70 + 52 * Math.sin(rad)}
					stroke={isQuarter ? 'var(--purple)' : 'var(--text-muted)'}
					stroke-width={isQuarter ? 2.5 : 1}
					stroke-linecap="round"
				/>
			{/each}
		</g>

		<!-- Hour hand -->
		<line
			x1="70" y1="70"
			x2={70 + 24 * Math.cos((hourHand.current * 300 - 90) * Math.PI / 180)}
			y2={70 + 24 * Math.sin((hourHand.current * 300 - 90) * Math.PI / 180)}
			stroke="var(--purple)" stroke-width="3.5" stroke-linecap="round"
			style="opacity: {hourHand.current};"
		/>

		<!-- Minute hand -->
		<line
			x1="70" y1="70"
			x2={70 + 36 * Math.cos((minuteHand.current * 1080 - 90) * Math.PI / 180)}
			y2={70 + 36 * Math.sin((minuteHand.current * 1080 - 90) * Math.PI / 180)}
			stroke="var(--blue)" stroke-width="2" stroke-linecap="round"
			style="opacity: {minuteHand.current};"
		/>

		<!-- Center dot with glow -->
		<g filter="url(#clock-glow)">
			<circle cx="70" cy="70" r="4" fill="var(--purple)"
				style="opacity: {ticksOpacity.current};" />
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 11
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		How I Actually Use It
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Real talk
	</p>
</div>
