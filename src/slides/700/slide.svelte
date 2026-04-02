<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const refs = [
		{ ref: '@src/components/Button.tsx', desc: 'Point to a file', color: 'var(--purple)' },
		{ ref: '@src/services/', desc: 'Point to a folder', color: 'var(--blue)' },
		{ ref: '@codebase', desc: 'Search everything', color: 'var(--emerald)' },
		{ ref: '@docs React', desc: 'Read documentation', color: 'var(--cyan)' },
		{ ref: '@git diff', desc: 'Look at changes', color: 'var(--pink)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.5rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			The <span style="color: var(--purple); font-family: var(--r-code-font);">@</span> trick
		</p>
	</Transition>

	<Transition>
		<p style="font-size: 1.15rem; color: var(--text-muted); max-width: 650px; text-align: center;">
			Don't make the AI guess — point it to exactly what matters.
		</p>
	</Transition>

	<Transition>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.8rem;">
			{#each refs as item}
				<div style="display: flex; align-items: center; gap: 1.5rem; padding: 0.5rem 0;">
					<code style="
						font-family: var(--r-code-font); font-size: 1rem;
						color: {item.color}; background: var(--surface);
						padding: 6px 14px; border-radius: 8px;
						border: 1px solid var(--border);
						min-width: 320px;
					">{item.ref}</code>
					<span style="font-size: 1.05rem; color: var(--text-muted);">{item.desc}</span>
				</div>
			{/each}
		</div>
	</Transition>
</div>
