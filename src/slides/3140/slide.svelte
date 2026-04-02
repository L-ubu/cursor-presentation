<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const favorites = [
		{
			name: 'Parallel Subagents',
			desc: 'Spawn multiple AI agents to work on different parts simultaneously',
			color: '#a78bfa',
			tag: 'Built-in',
		},
		{
			name: 'Web Search',
			desc: 'Let the agent look up docs, APIs, and current info in real-time',
			color: '#60a5fa',
			tag: 'Built-in',
		},
		{
			name: 'Continual Learning',
			desc: 'Rules & skills that evolve as the agent learns your codebase',
			color: '#34d399',
			tag: 'Skill',
		},
		{
			name: 'Postman MCP',
			desc: 'Test & interact with APIs directly from prompts',
			color: '#fbbf24',
			tag: 'MCP',
		},
		{
			name: 'qa-ai-toolkit',
			desc: 'My npm package — automated QA flows for frontend, backend & E2E',
			color: '#f472b6',
			tag: 'npm',
		},
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.6rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			My favorite <span style="color: var(--purple);">plugins & skills</span>
		</p>
	</Transition>

	<Transition>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.65rem; max-width: 720px; width: 100%;">
			{#each favorites as fav}
				<div style="
					display: grid; grid-template-columns: 200px 60px 1fr; align-items: center; gap: 0.8rem;
					padding: 0.8rem 1.3rem;
					background: var(--surface); border: 1px solid var(--border);
					border-radius: 10px;
				">
					<span style="font-size: 1.05rem; font-weight: 700; color: {fav.color};">{fav.name}</span>
					<span style="
						font-size: 0.8rem; font-weight: 600;
						color: {fav.color}; background: {fav.color}18;
						padding: 2px 8px; border-radius: 4px;
						text-transform: uppercase; letter-spacing: 0.05em;
						text-align: center; justify-self: start;
					">{fav.tag}</span>
					<p style="font-size: 0.95rem; color: var(--text-muted); line-height: 1.4;">{fav.desc}</p>
				</div>
			{/each}
		</div>
	</Transition>
</div>
