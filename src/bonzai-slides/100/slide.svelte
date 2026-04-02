<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { onMount } from 'svelte'
	import { tween } from '@animotion/motion'

	let lockScale = tween(0, { duration: 500 })
	let crackOpacity = tween(0, { duration: 300 })
	let titleOpacity = tween(0, { duration: 600 })
	let subtitleOpacity = tween(0, { duration: 500 })
	let slideEl

	async function playAnimation() {
		lockScale.reset(); crackOpacity.reset(); titleOpacity.reset(); subtitleOpacity.reset()
		await lockScale.to(1)
		await crackOpacity.to(1)
		await titleOpacity.to(1)
		await subtitleOpacity.to(1)
	}

	onMount(() => {
		const section = slideEl.closest('section')
		section.addEventListener('in', playAnimation)
		playAnimation()
		return () => section.removeEventListener('in', playAnimation)
	})
</script>

<div class="divider-slide" style="justify-content: center; gap: 0;" bind:this={slideEl}>
	<svg width="120" height="140" viewBox="0 0 120 140" style="overflow: visible; transform: scale({lockScale.current});">
		<!-- lock body -->
		<rect x="15" y="60" width="90" height="70" rx="12" fill="#1e1e2e" stroke="#ef4444" stroke-width="2.5" />
		<!-- lock shackle -->
		<path d="M35 60 V35 C35 15, 85 15, 85 35 V60" fill="none" stroke="#ef4444" stroke-width="4" stroke-linecap="round" />
		<!-- keyhole -->
		<circle cx="60" cy="90" r="8" fill="#ef4444" />
		<rect x="57" y="90" width="6" height="18" rx="2" fill="#ef4444" />
		<!-- crack lines -->
		<g style="opacity: {crackOpacity.current};">
			<line x1="105" y1="60" x2="120" y2="45" stroke="#f97316" stroke-width="2" stroke-linecap="round" />
			<line x1="105" y1="75" x2="125" y2="75" stroke="#f97316" stroke-width="2" stroke-linecap="round" />
			<line x1="105" y1="90" x2="120" y2="105" stroke="#f97316" stroke-width="2" stroke-linecap="round" />
			<line x1="15" y1="65" x2="0" y2="50" stroke="#f97316" stroke-width="2" stroke-linecap="round" />
			<line x1="15" y1="80" x2="-5" y2="80" stroke="#f97316" stroke-width="2" stroke-linecap="round" />
		</g>
	</svg>

	<div style="display: flex; flex-direction: column; align-items: center; margin-top: 1.5rem;">
		<p style="font-size: 0.85rem; color: #ef4444; letter-spacing: 0.25em; text-transform: uppercase; font-weight: 700; opacity: {titleOpacity.current};">
			Security Incident Report
		</p>
		<p style="font-size: 4.5rem; font-weight: 800; letter-spacing: -0.04em; line-height: 1.1; margin-top: 0.8rem; opacity: {titleOpacity.current};
			background: linear-gradient(135deg, #ef4444, #f97316);
			-webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">
			Bonzai v2 API
		</p>
		<p style="font-size: 1.5rem; color: var(--text-muted); margin-top: 0.8rem; font-weight: 300; opacity: {subtitleOpacity.current};">
			Full Admin Takeover in 3 Requests
		</p>
		<div style="margin-top: 2rem; display: flex; gap: 2rem; align-items: center; opacity: {subtitleOpacity.current};">
			<p style="font-size: 0.85rem; color: var(--text-muted);">
				Luca Vandenweghe &middot; Maarten De Rammelaere
			</p>
			<p style="font-size: 0.85rem; color: var(--text-muted);">
				March 2026
			</p>
		</div>
	</div>
</div>
