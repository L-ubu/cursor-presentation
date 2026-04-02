<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const skills = [
		{ name: 'standup-prep', desc: 'auto-generates my standup', color: 'var(--purple)' },
		{ name: 'end-of-day', desc: 'wraps up my day cleanly', color: 'var(--blue)' },
		{ name: 'pre-mr-checklist', desc: 'catches mistakes before MR', color: 'var(--emerald)' },
		{ name: 'jira-ticket-breakdown', desc: 'breaks tickets into chunks', color: 'var(--cyan)' },
		{ name: 'pr-summary', desc: 'writes PR descriptions', color: 'var(--purple)' },
		{ name: 'qa-run', desc: 'runs full QA across frontend + backend', color: 'var(--pink)' },
		{ name: 'code-review-agent', desc: 'reviews PRs against project rules', color: 'var(--blue)' },
		{ name: 'self-improving-agent', desc: 'learns and evolves from every task', color: 'var(--emerald)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Skills I actually use
		</p>
	</Transition>

	<Transition>
		<div style="
			display: flex; flex-direction: column; gap: 0.5rem;
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 14px; padding: 1.2rem 1.5rem;
			font-family: var(--r-code-font); font-size: 0.95rem;
			min-width: 620px;
		">
			<div style="color: var(--text-muted); margin-bottom: 0.4rem; font-size: 1rem;">.cursor/skills/</div>
			<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.5rem;">
				{#each skills as skill}
					<div style="display: flex; gap: 1.2rem; padding-left: 1.4rem;">
						<span style="color: {skill.color};">{skill.name}/SKILL.md</span>
						<span style="color: var(--text-muted);">→ {skill.desc}</span>
					</div>
				{/each}
			</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.1rem; color: var(--pink); font-weight: 500;">
			Each skill is a multi-step workflow the agent executes autonomously.
		</p>
	</Transition>
</div>
