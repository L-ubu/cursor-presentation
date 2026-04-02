<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let rotation = tween(0, { duration: 1500 })
	let gearsOpacity = tween(0, { duration: 400 })
	let textOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		rotation.reset(); gearsOpacity.reset(); textOpacity.reset()
		await gearsOpacity.to(1); await rotation.to(1); await textOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<svg width="240" height="140" viewBox="-10 -10 260 160" style="overflow: visible;">
		<g style="opacity: {gearsOpacity.current};">
			<!-- Gear 1: large purple (center-left) -->
			<g style="transform-origin: 55px 65px; transform: rotate({rotation.current * 360}deg);">
				<circle cx="55" cy="65" r="28" fill="none" stroke="var(--purple)" stroke-width="2" />
				<circle cx="55" cy="65" r="6" fill="var(--purple)" />
				{#each [0, 45, 90, 135, 180, 225, 270, 315] as angle}
					{@const rad = (angle * Math.PI) / 180}
					<rect
						x={55 + 24 * Math.cos(rad) - 3} y={65 + 24 * Math.sin(rad) - 4}
						width="6" height="8" rx="1"
						fill="var(--purple)"
						style="transform: rotate({angle}deg); transform-origin: {55 + 24 * Math.cos(rad)}px {65 + 24 * Math.sin(rad)}px;"
					/>
				{/each}
			</g>
			<!-- Gear 2: medium blue (top-center) -->
			<g style="transform-origin: 110px 38px; transform: rotate({-rotation.current * 360}deg);">
				<circle cx="110" cy="38" r="20" fill="none" stroke="var(--blue)" stroke-width="2" />
				<circle cx="110" cy="38" r="5" fill="var(--blue)" />
				{#each [0, 60, 120, 180, 240, 300] as angle}
					{@const rad = (angle * Math.PI) / 180}
					<rect
						x={110 + 17 * Math.cos(rad) - 2.5} y={38 + 17 * Math.sin(rad) - 3.5}
						width="5" height="7" rx="1"
						fill="var(--blue)"
						style="transform: rotate({angle}deg); transform-origin: {110 + 17 * Math.cos(rad)}px {38 + 17 * Math.sin(rad)}px;"
					/>
				{/each}
			</g>
			<!-- Gear 3: small emerald (middle-right) -->
			<g style="transform-origin: 140px 80px; transform: rotate({rotation.current * 360}deg);">
				<circle cx="140" cy="80" r="15" fill="none" stroke="var(--emerald)" stroke-width="2" />
				<circle cx="140" cy="80" r="4" fill="var(--emerald)" />
				{#each [0, 72, 144, 216, 288] as angle}
					{@const rad = (angle * Math.PI) / 180}
					<rect
						x={140 + 12 * Math.cos(rad) - 2} y={80 + 12 * Math.sin(rad) - 3}
						width="4" height="6" rx="1"
						fill="var(--emerald)"
						style="transform: rotate({angle}deg); transform-origin: {140 + 12 * Math.cos(rad)}px {80 + 12 * Math.sin(rad)}px;"
					/>
				{/each}
			</g>
			<!-- Gear 4: small cyan (top-right) -->
			<g style="transform-origin: 165px 30px; transform: rotate({-rotation.current * 360}deg);">
				<circle cx="165" cy="30" r="13" fill="none" stroke="var(--cyan)" stroke-width="1.5" />
				<circle cx="165" cy="30" r="3.5" fill="var(--cyan)" />
				{#each [0, 72, 144, 216, 288] as angle}
					{@const rad = (angle * Math.PI) / 180}
					<rect
						x={165 + 10 * Math.cos(rad) - 1.5} y={30 + 10 * Math.sin(rad) - 2.5}
						width="3" height="5" rx="1"
						fill="var(--cyan)"
						style="transform: rotate({angle}deg); transform-origin: {165 + 10 * Math.cos(rad)}px {30 + 10 * Math.sin(rad)}px;"
					/>
				{/each}
			</g>
			<!-- Gear 5: tiny pink (bottom-right) -->
			<g style="transform-origin: 180px 90px; transform: rotate({rotation.current * 360}deg);">
				<circle cx="180" cy="90" r="11" fill="none" stroke="var(--pink)" stroke-width="1.5" />
				<circle cx="180" cy="90" r="3" fill="var(--pink)" />
				{#each [0, 60, 120, 180, 240, 300] as angle}
					{@const rad = (angle * Math.PI) / 180}
					<rect
						x={180 + 8.5 * Math.cos(rad) - 1.5} y={90 + 8.5 * Math.sin(rad) - 2}
						width="3" height="4" rx="0.5"
						fill="var(--pink)"
						style="transform: rotate({angle}deg); transform-origin: {180 + 8.5 * Math.cos(rad)}px {90 + 8.5 * Math.sin(rad)}px;"
					/>
				{/each}
			</g>
		</g>
	</svg>

	<p style="font-size: 1.2rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.15em; font-weight: 600; margin-top: 1rem; opacity: {textOpacity.current};">
		Part 4
	</p>
	<p class="gradient-text" style="font-size: 4rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; opacity: {textOpacity.current};">
		Agent Modes
	</p>
	<p style="font-size: 1.4rem; color: var(--text-muted); margin-top: 0.8rem; opacity: {textOpacity.current};">
		Five gears for any task
	</p>
</div>
