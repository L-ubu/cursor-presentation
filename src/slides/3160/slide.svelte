<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const sections = [
		{
			title: 'MCP Servers',
			color: '#a78bfa',
			items: ['Jira', 'Confluence', 'Paper Design', 'Postman', 'Outlook'],
		},
		{
			title: 'Custom Skills',
			color: '#34d399',
			items: ['QA Run', 'PR Summary', 'Standup Prep', 'Code Review', 'Self-Improving Agent'],
		},
		{
			title: 'Rules & Context',
			color: '#60a5fa',
			items: ['Personal assistant', 'Branch naming', 'Pre-MR checklist', 'EOD wrap-up'],
		},
		{
			title: 'Integrations',
			color: '#f472b6',
			items: ['Apple Calendar', 'Reminders', 'GitLab CLI', 'Terminup', 'Voice input'],
		},
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.6rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			My <span style="color: var(--purple);">toolkit</span>
		</p>
	</Transition>

	<Transition>
		<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; max-width: 780px; width: 100%;">
			{#each sections as section}
				<div style="
					background: var(--surface); border: 1px solid var(--border);
					border-radius: 12px; padding: 1rem 1.2rem;
				">
					<p style="font-size: 1rem; font-weight: 700; color: {section.color}; margin-bottom: 0.5rem;">{section.title}</p>
					<div style="display: flex; flex-wrap: wrap; gap: 0.35rem;">
						{#each section.items as item}
							<span style="
								font-size: 0.88rem; color: var(--text-muted);
								background: var(--bg); padding: 3px 10px;
								border-radius: 6px; border: 1px solid var(--border);
							">{item}</span>
						{/each}
					</div>
				</div>
			{/each}
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 0.95rem; color: var(--text-muted); font-style: italic;">
			~40 custom rules & skills, all version-controlled
		</p>
	</Transition>
</div>
