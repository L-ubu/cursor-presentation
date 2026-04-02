<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let stage = $state(0)
	let advancedOpacity = tween(0, { duration: 400 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.8rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Where do rules live?
		</p>
	</Transition>

	<div style="display: flex; gap: 2.5rem; align-items: flex-start;">
		<!-- Option 1: Simple -->
		<Transition>
			<div style="
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 14px; padding: 1.2rem 1.5rem; min-width: 300px;
			">
				<div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.7rem;">
					<span style="font-size: 1.1rem; color: var(--emerald); font-weight: 700;">Simple</span>
					<span style="font-size: 0.85rem; color: var(--text-muted); background: var(--bg); padding: 2px 8px; border-radius: 4px;">one file</span>
				</div>
				<div style="font-family: var(--r-code-font); font-size: 0.9rem; line-height: 1.6;">
					<p style="color: var(--text-muted);">project/</p>
					<p style="color: var(--emerald); padding-left: 1rem;">└── .cursorrules</p>
				</div>
				<p style="font-size: 0.9rem; color: var(--text-muted); margin-top: 0.7rem; line-height: 1.4;">
					One markdown file in your root.<br/>
					All rules in one place.<br/>
					Great for getting started.
				</p>
			</div>
		</Transition>

		<!-- Option 2: Advanced -->
		<div style="opacity: {advancedOpacity.current}; transform: translateY({(1 - advancedOpacity.current) * 12}px);">
			<div style="
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 14px; padding: 1.2rem 1.5rem; min-width: 300px;
			">
				<div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.7rem;">
					<span style="font-size: 1.1rem; color: var(--purple); font-weight: 700;">Advanced</span>
					<span style="font-size: 0.85rem; color: var(--text-muted); background: var(--bg); padding: 2px 8px; border-radius: 4px;">folder structure</span>
				</div>
				<div style="font-family: var(--r-code-font); font-size: 0.95rem; line-height: 1.6;">
					<p style="color: var(--text-muted);">project/</p>
					<p style="color: var(--purple); padding-left: 1rem;">└── .cursor/</p>
					<p style="color: var(--purple); padding-left: 2rem;">└── rules/</p>
					<p style="color: var(--text); padding-left: 3rem;">├── react-components.mdc</p>
					<p style="color: var(--text); padding-left: 3rem;">├── api-patterns.mdc</p>
					<p style="color: var(--text); padding-left: 3rem;">├── testing.mdc</p>
					<p style="color: var(--text); padding-left: 3rem;">└── code-style.mdc</p>
				</div>
				<p style="font-size: 0.9rem; color: var(--text-muted); margin-top: 0.7rem; line-height: 1.4;">
					Per-topic rules with glob patterns.<br/>
					Each rule targets specific files.<br/>
					Scales with your team.
				</p>
			</div>
		</div>
	</div>

	<Action
		actions={[
			async () => { await advancedOpacity.to(1) },
		]}
	/>

	<Transition>
		<p style="font-size: 1.05rem; color: var(--text-muted);">
			Start with <code style="color: var(--emerald); background: var(--surface); padding: 3px 8px; border-radius: 5px;">.cursorrules</code> — upgrade to the folder when you need per-file control.
		</p>
	</Transition>
</div>
