<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let stepOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		stepOpacity.reset()
		await stepOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" bind:this={slideEl}>
	<p style="font-size: 0.85rem; color: #f97316; letter-spacing: 0.2em; text-transform: uppercase; font-weight: 700; opacity: {stepOpacity.current};">
		Step 2 of 3
	</p>
	<p style="font-size: 3.5rem; font-weight: 800; letter-spacing: -0.03em; margin-top: 0.5rem; color: var(--text); opacity: {stepOpacity.current};">
		Auth Bypass
	</p>
	<p style="font-size: 1.2rem; color: var(--text-muted); margin-top: 0.5rem; opacity: {stepOpacity.current};">
		The hash IS the password
	</p>
</div>
