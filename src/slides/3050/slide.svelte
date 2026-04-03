<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const donts = [
		{ icon: '🔑', text: 'Paste passwords, API keys, or secrets', sub: '' },
		{ icon: '🏗️', text: 'Let it make architectural decisions without your input', sub: '' },
		{ icon: '🔓', text: 'Use it for security-critical logic without expert review', sub: '' },
		{ icon: '🗄️', text: 'Run generated SQL on production databases', sub: '' },
		{ icon: '📤', text: 'Share proprietary client code on public models', sub: '' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.8rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			What <span style="color: #ef4444;">NOT</span> to do
		</p>
	</Transition>

	<Transition>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.7rem; max-width: 680px;">
			{#each donts as item}
				<div style="
					display: flex; align-items: center; gap: 1rem;
					padding: 0.75rem 1.3rem;
					background: rgba(239, 68, 68, 0.06);
					border: 1px solid rgba(239, 68, 68, 0.2);
					border-radius: 10px;
				">
					<span style="font-size: 1.3rem;">{item.icon}</span>
					<div style="display: flex; flex-direction: column;">
						<span style="font-size: 1.05rem; color: var(--text);">{item.text}</span>
						{#if item.sub}
							<span style="font-size: 0.85rem; color: var(--text-muted); font-style: italic;">{item.sub}</span>
						{/if}
					</div>
				</div>
			{/each}
		</div>
	</Transition>
</div>
