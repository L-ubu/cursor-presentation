<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const steps = ['Finds the right file', 'Reads existing code', 'Writes the changes', 'Shows you a diff to review']
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.5rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Your first prompt
		</p>
	</Transition>

	<Transition>
		<div style="
			background: var(--surface);
			border: 1px solid var(--border);
			border-radius: 14px;
			padding: 1.4rem 1.8rem;
			font-family: var(--r-code-font);
			font-size: 1rem;
			max-width: 750px;
		">
			<span style="color: var(--purple);">❯</span>
			<span class="cursor-blink" style="color: var(--text); margin-left: 0.5rem;">"Add a loading spinner to the submit button while the API call is in progress."</span>
		</div>
	</Transition>

	<Transition>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.8rem;">
			{#each steps as step}
				<div style="display: flex; align-items: center; gap: 1rem;">
					<span style="color: var(--emerald); font-size: 1.3rem;">✓</span>
					<span style="font-size: 1.1rem; color: var(--text);">{step}</span>
				</div>
			{/each}
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.2rem; color: var(--pink); font-weight: 500;">
			No config. No plugins. No setup.
		</p>
	</Transition>
</div>
