<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const capabilities = [
		{ label: 'Reads your code', color: 'var(--purple)', icon: 'M4 6h16M4 12h16M4 18h10' },
		{ label: 'Writes & edits', color: 'var(--blue)', icon: 'M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z' },
		{ label: 'Runs commands', color: 'var(--emerald)', icon: 'M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.5rem;">
	<Transition visible>
		<p style="font-size: 3rem; font-weight: 700; color: var(--text); letter-spacing: -0.03em; text-align: center; max-width: 850px; line-height: 1.2;">
			It's VS Code, but it actually
			<span class="gradient-text" style="font-weight: 800;">understands</span>
			your code.
		</p>
	</Transition>

	<Transition entry="scale-in" duration={0.6}>
		<div style="display: flex; gap: 2rem;">
			{#each capabilities as cap}
				<div style="
					display: flex; flex-direction: column; align-items: center; gap: 0.8rem;
					padding: 1.5rem 2.5rem;
					background: var(--surface);
					border: 1px solid var(--border);
					border-radius: 14px;
					min-width: 200px;
				">
					<svg width="36" height="36" viewBox="0 0 24 24" fill="none" stroke={cap.color} stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
						<path d={cap.icon} />
					</svg>
					<p style="font-size: 1.2rem; font-weight: 600; color: {cap.color};">{cap.label}</p>
				</div>
			{/each}
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.15rem; color: var(--pink); font-weight: 500;">
			A junior that never sleeps, never complains, and types 10,000 WPM.
		</p>
	</Transition>
</div>
