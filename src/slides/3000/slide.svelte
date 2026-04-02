<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const donts = [
		{ bad: '"Fix it"', good: '"Fix the null check in @auth.ts line 42"' },
		{ bad: '500-word prompt', good: 'Short, clear instructions' },
		{ bad: 'Accept without reviewing', good: 'Always check the diff' },
		{ bad: 'No rules configured', good: 'Even 3-5 basic rules' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Common mistakes
		</p>
	</Transition>

	<Transition>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.9rem; max-width: 800px;">
			{#each donts as item}
				<div style="
					display: flex; align-items: center; gap: 1.2rem;
					padding: 0.9rem 1.4rem;
					background: var(--surface);
					border: 1px solid var(--border);
					border-radius: 12px;
				">
					<div style="display: flex; align-items: center; gap: 0.6rem; min-width: 280px;">
						<span style="color: #ef4444; font-size: 1.3rem;">✕</span>
						<span style="font-size: 1rem; color: var(--text-muted); font-family: var(--r-code-font);">{item.bad}</span>
					</div>
					<span style="color: var(--text-muted); font-size: 1.1rem;">→</span>
					<div style="display: flex; align-items: center; gap: 0.6rem;">
						<span style="color: var(--emerald); font-size: 1.3rem;">✓</span>
						<span style="font-size: 1rem; color: var(--text); font-family: var(--r-code-font);">{item.good}</span>
					</div>
				</div>
			{/each}
		</div>
	</Transition>
</div>
