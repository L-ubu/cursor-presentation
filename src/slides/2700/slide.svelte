<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const timeline = [
		{ time: '08:45', label: '"standup"', desc: 'AI gathers git, Jira, calendar', color: 'var(--purple)' },
		{ time: '09:15', label: '"break down JLROV-456"', desc: 'Ticket → TODO list with estimates', color: 'var(--blue)' },
		{ time: '09:30', label: 'Agent Mode', desc: 'AI handles boilerplate, I decide', color: 'var(--emerald)' },
		{ time: '14:00', label: '"check my code"', desc: 'Pre-MR catches 3 issues', color: 'var(--cyan)' },
		{ time: '17:15', label: '"eod"', desc: 'Summarizes day, commits WIP', color: 'var(--pink)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			My daily workflow
		</p>
	</Transition>

	<Transition>
		<div style="display: flex; flex-direction: column; gap: 0; position: relative; padding-left: 2.5rem;">
			<div style="position: absolute; left: 0.6rem; top: 0.5rem; bottom: 0.5rem; width: 2px; background: var(--border);"></div>

			<div class="stagger-children" style="display: flex; flex-direction: column;">
				{#each timeline as item}
					<div style="display: flex; align-items: flex-start; gap: 1.2rem; padding: 0.7rem 0; position: relative;">
						<div style="
							position: absolute; left: -2.05rem; top: 0.95rem;
							width: 12px; height: 12px;
							background: {item.color}; border-radius: 50%;
							box-shadow: 0 0 10px {item.color};
						"></div>
						<span style="
							font-family: var(--r-code-font); font-size: 0.9rem;
							color: {item.color}; font-weight: 700;
							min-width: 60px;
						">{item.time}</span>
						<div>
							<p style="font-size: 1.1rem; font-weight: 600; color: var(--text);">{item.label}</p>
							<p style="font-size: 0.9rem; color: var(--text-muted);">{item.desc}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</Transition>
</div>
