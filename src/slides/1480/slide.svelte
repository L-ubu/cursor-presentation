<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const items = [
		{
			name: 'Rules',
			svg: 'M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2',
			tagline: 'Passive guidance',
			detail: '"How to write code"',
			example: '"Use named exports"',
			color: 'var(--purple)',
		},
		{
			name: 'Skills',
			svg: 'M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.066 2.573c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.573 1.066c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.066-2.573c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065zM15 12a3 3 0 11-6 0 3 3 0 016 0z',
			tagline: 'Active workflows',
			detail: '"Do this multi-step task"',
			example: '"Scaffold a service"',
			color: 'var(--blue)',
		},
		{
			name: 'Commands',
			svg: 'M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z',
			tagline: 'Saved prompts',
			detail: 'Quick shortcuts',
			example: '"/commit"',
			color: 'var(--emerald)',
		},
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.25rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Rules vs Skills vs Commands
		</p>
	</Transition>

	<div style="display: flex; gap: 1.35rem;">
		{#each items as item, i (item.name)}
			<Transition delay={i * 0.2}>
				<div style="
					display: flex; flex-direction: column; align-items: center; gap: 0.75rem;
					padding: 1.65rem 1.35rem;
					background: var(--surface);
					border: 1px solid var(--border);
					border-radius: 14px;
					width: 260px;
					text-align: center;
				">
					<svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke={item.color} stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
						<path d={item.svg} />
					</svg>
					<p style="font-size: 1.5rem; font-weight: 700; color: {item.color};">{item.name}</p>
					<p style="font-size: 1rem; font-weight: 600; color: var(--text);">{item.tagline}</p>
					<p style="font-size: 0.9rem; color: var(--text-muted);">{item.detail}</p>
					<div style="margin-top: auto; padding-top: 0.75rem; border-top: 1px solid var(--border); width: 100%;">
						<code style="font-family: var(--r-code-font); font-size: 0.9rem; color: {item.color};">{item.example}</code>
					</div>
				</div>
			</Transition>
		{/each}
	</div>
</div>
