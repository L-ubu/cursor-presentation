<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let acceptance = tween(30)
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.25rem;">
	<Transition visible>
		<p style="font-size: 2.5rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em; text-align: center; max-width: 760px;">
			Without rules, you correct the AI
			<span style="color: var(--pink);">every. single. time.</span>
		</p>
	</Transition>

	<Transition
		do={async () => {
			await acceptance.to(82, { duration: 1500 })
		}}
		undo={() => acceptance.reset()}
	>
		<div style="display: flex; align-items: center; gap: 2.25rem;">
			<div style="text-align: center;">
				<p style="font-size: 4.5rem; font-weight: 800; color: var(--emerald);">
					{acceptance.current.toFixed(0)}%
				</p>
				<p style="font-size: 1.05rem; color: var(--text-muted); margin-top: 0.4rem;">acceptance rate with rules</p>
			</div>
			<div style="font-size: 1.75rem; color: var(--text-muted);">vs</div>
			<div style="text-align: center;">
				<p style="font-size: 4.5rem; font-weight: 800; color: var(--text-muted);">~30%</p>
				<p style="font-size: 1.05rem; color: var(--text-muted); margin-top: 0.4rem;">without rules</p>
			</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.2rem; color: var(--purple); font-weight: 600;">
			This is the #1 productivity lever for any team.
		</p>
	</Transition>
</div>
