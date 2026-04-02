<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const modes = [
		{
			name: 'Agent',
			tagline: 'The doer',
			desc: 'Writes code, runs commands',
			color: 'var(--purple)',
			bg: 'rgba(167, 139, 250, 0.08)',
		},
		{
			name: 'Ask',
			tagline: 'The explainer',
			desc: 'Reads only — touches nothing',
			color: 'var(--blue)',
			bg: 'rgba(96, 165, 250, 0.08)',
		},
		{
			name: 'Plan',
			tagline: 'The architect',
			desc: 'Thinks first, builds second',
			color: 'var(--emerald)',
			bg: 'rgba(52, 211, 153, 0.08)',
		},
		{
			name: 'Debug',
			tagline: 'The detective',
			desc: 'Traces bugs step-by-step',
			color: 'var(--cyan)',
			bg: 'rgba(34, 211, 238, 0.08)',
		},
		{
			name: 'YOLO',
			tagline: 'The madlad',
			desc: 'Auto-approves everything',
			color: 'var(--pink)',
			bg: 'rgba(249, 168, 212, 0.08)',
		},
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Pick your gear
		</p>
	</Transition>

	<div style="display: flex; gap: 1rem;">
		{#each modes as mode, i (mode.name)}
			<Transition delay={i * 0.15}>
				<div style="
					display: flex; flex-direction: column; gap: 0.7rem;
					padding: 1.4rem 1.1rem;
					background: {mode.bg};
					border: 1px solid var(--border);
					border-radius: 14px;
					width: 170px;
					text-align: center;
				">
					<p style="font-size: 1.35rem; font-weight: 800; color: {mode.color}; letter-spacing: -0.02em;">
						{mode.name}
					</p>
					<p style="font-size: 0.95rem; color: var(--text); font-weight: 600;">
						{mode.tagline}
					</p>
					<p style="font-size: 0.9rem; color: var(--text-muted); line-height: 1.4;">
						{mode.desc}
					</p>
				</div>
			</Transition>
		{/each}
	</div>

	<Transition>
		<p style="font-size: 1.05rem; color: var(--text-muted);">
			Switch anytime with <span class="kbd" style="font-size: 0.95rem;">Shift</span> <span class="kbd" style="font-size: 0.95rem;">Tab</span>
		</p>
	</Transition>
</div>
