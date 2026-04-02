<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const shortcuts = [
		{ keys: ['⌘/Ctrl', 'L'], label: 'Agent Panel', desc: 'Talk to the AI', color: 'var(--purple)' },
		{ keys: ['⌘/Ctrl', 'K'], label: 'Inline Edit', desc: 'Quick edits on selected code', color: 'var(--blue)' },
		{ keys: ['⇧', 'Tab'], label: 'Switch Mode', desc: 'Agent / Ask / Plan', color: 'var(--emerald)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.5rem;">
	<Transition visible>
		<p style="font-size: 2.5rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			The only <span style="color: var(--purple);">3</span> shortcuts you need
		</p>
	</Transition>

	<Transition>
		<div style="display: flex; flex-direction: column; gap: 1.2rem;" class="stagger-children">
			{#each shortcuts as shortcut}
				<div style="
					display: flex; align-items: center;
					padding: 1.2rem 2rem;
					background: var(--surface);
					border: 1px solid var(--border);
					border-radius: 14px;
					width: 550px;
				">
					<div style="display: flex; gap: 0.5rem; width: 130px; flex-shrink: 0; justify-content: center;">
						{#each shortcut.keys as key}
							<span class="kbd" style="font-size: 1.1rem; padding: 8px 18px;">{key}</span>
						{/each}
					</div>
					<div style="flex: 1; text-align: center;">
						<p style="font-size: 1.3rem; font-weight: 600; color: {shortcut.color};">{shortcut.label}</p>
						<p style="font-size: 0.95rem; color: var(--text-muted);">{shortcut.desc}</p>
					</div>
				</div>
			{/each}
		</div>
	</Transition>

	<Transition>
		<div style="display: flex; align-items: center; gap: 0.6rem; font-size: 0.9rem; color: var(--text-muted);">
			<span style="color: var(--text-muted);">*</span>
			<span class="kbd" style="font-size: 0.85rem; padding: 4px 12px;">Tab</span>
			<span>to accept AI autocomplete suggestions as you type</span>
		</div>
	</Transition>
</div>
