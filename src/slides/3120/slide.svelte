<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween, all } from '@animotion/motion'

	const roles = [
		{
			title: 'Developers',
			color: '#a78bfa',
			items: ['Scaffold features from tickets', 'Auto-generate tests & docs', 'Review PRs with context'],
		},
		{
			title: 'Marketing',
			color: '#f472b6',
			items: ['Generate campaign copy', 'Analyze competitor content', 'Create A/B test variants'],
		},
		{
			title: 'Sales',
			color: '#34d399',
			items: ['Draft personalized outreach', 'Summarize client history', 'Build proposal decks'],
		},
		{
			title: 'Project Managers',
			color: '#60a5fa',
			items: ['Break down epics into tasks', 'Write sprint retrospectives', 'Generate status reports'],
		},
	]

	let roleOpacities = roles.map(() => tween(0, { duration: 400 }))
	let demoOpacity = tween(0, { duration: 500 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.6rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Possibilities for <span style="color: var(--purple);">every role</span>
		</p>
	</Transition>

	<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; max-width: 820px; width: 100%;">
		{#each roles as role, i}
			<div style="
				opacity: {roleOpacities[i].current};
				transform: translateY({(1 - roleOpacities[i].current) * 16}px);
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 12px; padding: 1.1rem 1.3rem;
			">
				<p style="font-size: 1.1rem; font-weight: 700; color: {role.color}; margin-bottom: 0.5rem;">{role.title}</p>
				{#each role.items as item}
					<p style="font-size: 0.95rem; color: var(--text-muted); line-height: 1.55; padding-left: 0.6rem; border-left: 2px solid {role.color}33; margin-bottom: 0.3rem;">{item}</p>
				{/each}
			</div>
		{/each}
	</div>

	<Action
		actions={[
			async () => { await all(roleOpacities[0].to(1), roleOpacities[1].to(1)) },
			async () => { await all(roleOpacities[2].to(1), roleOpacities[3].to(1)) },
			async () => { await demoOpacity.to(1) },
		]}
	/>

	<p style="
		font-size: 1.15rem; color: var(--emerald); font-weight: 600;
		opacity: {demoOpacity.current};
	">
		Let me show you what this looks like in action...
	</p>
</div>
