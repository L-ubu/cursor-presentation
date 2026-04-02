<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Don't know how to write rules?
		</p>
	</Transition>

	<Transition>
		<div style="
			max-width: 660px; width: 100%;
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 12px; padding: 1.3rem 1.6rem;
			font-family: var(--r-code-font); font-size: 1rem;
			line-height: 1.7; color: var(--text);
		">
			<span style="color: var(--emerald);">plan</span>{' '}<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Create a Cursor rule that enforces</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">our React component conventions.</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">Read{' '}</span><span style="color: var(--purple);">@src/components/</span>{' '}<span style="color: #e4e4e7;">for</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">examples of our style."</span><span class="cursor-blink"></span>
		</div>
	</Transition>

	<Transition>
		<div style="display: flex; flex-direction: column; gap: 0.6rem; max-width: 580px;">
			<div style="display: flex; align-items: center; gap: 0.8rem;">
				<span style="color: var(--emerald); font-size: 1.2rem;">✓</span>
				<span style="color: var(--text); font-size: 1rem;">It reads your code to understand your patterns</span>
			</div>
			<div style="display: flex; align-items: center; gap: 0.8rem;">
				<span style="color: var(--emerald); font-size: 1.2rem;">✓</span>
				<span style="color: var(--text); font-size: 1rem;">Generates the rule file with proper frontmatter</span>
			</div>
			<div style="display: flex; align-items: center; gap: 0.8rem;">
				<span style="color: var(--emerald); font-size: 1.2rem;">✓</span>
				<span style="color: var(--text); font-size: 1rem;">Places it in the right folder with correct globs</span>
			</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.2rem; color: var(--purple); font-weight: 600;">
			The AI is amazing at setting itself up.
		</p>
	</Transition>
</div>
