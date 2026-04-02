<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const topics = [
		{ num: '01', label: 'The Basics', desc: 'Productive in 5 minutes', color: 'var(--purple)' },
		{ num: '02', label: 'Indexing', desc: 'How it reads your code', color: 'var(--blue)' },
		{ num: '03', label: 'Agent Modes', desc: 'Pick your gear', color: 'var(--emerald)' },
		{ num: '04', label: 'Rules', desc: 'Teach it YOUR style', color: 'var(--cyan)' },
		{ num: '05', label: 'Skills & Automation', desc: 'Active workflows that do the work', color: 'var(--pink)' },
		{ num: '06', label: 'MCP & Plugins', desc: 'Connect all the things', color: 'var(--purple)' },
		{ num: '07', label: 'Cloud & CLI', desc: 'Beyond the editor', color: 'var(--blue)' },
		{ num: '08', label: 'How I Use It', desc: 'Daily workflow & subagents', color: 'var(--emerald)' },
		{ num: '09', label: 'Tips & Wrap-up', desc: "Don'ts, possibilities & toolkit", color: 'var(--pink)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.5rem;">
	<Transition visible>
		<p style="font-size: 2.8rem; font-weight: 700; color: var(--text); letter-spacing: -0.03em;">
			What we'll cover
		</p>
	</Transition>

	<div style="display: flex; flex-direction: column; gap: 0.45rem; width: 560px;">
		{#each topics as topic, i}
			<Transition>
				<div style="
					display: grid; grid-template-columns: 32px 180px 1fr; align-items: baseline; gap: 0.8rem;
					padding: 0.65rem 1.3rem;
					border-left: 3px solid {topic.color};
					background: var(--surface);
					border-radius: 0 10px 10px 0;
				">
					<span style="
						font-family: var(--r-code-font); font-size: 0.95rem;
						color: {topic.color}; font-weight: 700;
					">{topic.num}</span>
					<p style="font-size: 1.1rem; font-weight: 600; color: var(--text);">{topic.label}</p>
					<p style="font-size: 0.95rem; color: var(--text-muted);">{topic.desc}</p>
				</div>
			</Transition>
		{/each}
	</div>
</div>
