<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween, all } from '@animotion/motion'

	let sourcesOpacity = tween(0, { duration: 400 })
	let flowProgress = tween(0, { duration: 800 })
	let termOpacity = tween(0, { duration: 400 })
	let line1 = tween(0, { duration: 300 })
	let line2 = tween(0, { duration: 300 })
	let line3 = tween(0, { duration: 300 })
	let line4 = tween(0, { duration: 300 })
	let line5 = tween(0, { duration: 300 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Example: <span style="color: var(--purple);">standup-prep</span> skill
		</p>
	</Transition>

	<Transition>
		<p style="font-size: 1.1rem; color: var(--text-muted);">
			I say <code style="color: var(--emerald); background: var(--surface); padding: 4px 10px; border-radius: 6px;">"standup"</code> at 08:45. Cursor does the rest:
		</p>
	</Transition>

	<div style="display: flex; align-items: center; gap: 2.5rem;">
		<!-- Source pills -->
		<div style="display: flex; flex-direction: column; gap: 0.8rem; opacity: {sourcesOpacity.current};">
			<div style="display: flex; align-items: center; gap: 0.6rem; padding: 0.5rem 1rem; border-left: 3px solid var(--purple); background: rgba(167, 139, 250, 0.06); border-radius: 0 8px 8px 0;">
				<svg width="18" height="18" viewBox="0 0 18 18"><path d="M3 3 L3 15 L10 15 L10 6 L7 3 Z M7 3 L7 6 L10 6" fill="none" stroke="var(--purple)" stroke-width="1.2" stroke-linejoin="round"/></svg>
				<span style="font-size: 0.95rem; color: var(--purple); font-weight: 600;">git log</span>
			</div>
			<div style="display: flex; align-items: center; gap: 0.6rem; padding: 0.5rem 1rem; border-left: 3px solid var(--blue); background: rgba(96, 165, 250, 0.06); border-radius: 0 8px 8px 0;">
				<svg width="18" height="18" viewBox="0 0 18 18"><rect x="2" y="2" width="14" height="14" rx="2" fill="none" stroke="var(--blue)" stroke-width="1.2"/><line x1="2" y1="6" x2="16" y2="6" stroke="var(--blue)" stroke-width="1"/><line x1="6" y1="6" x2="6" y2="16" stroke="var(--blue)" stroke-width="1"/></svg>
				<span style="font-size: 0.95rem; color: var(--blue); font-weight: 600;">calendar</span>
			</div>
			<div style="display: flex; align-items: center; gap: 0.6rem; padding: 0.5rem 1rem; border-left: 3px solid var(--emerald); background: rgba(52, 211, 153, 0.06); border-radius: 0 8px 8px 0;">
				<svg width="18" height="18" viewBox="0 0 18 18"><rect x="2" y="4" width="14" height="10" rx="2" fill="none" stroke="var(--emerald)" stroke-width="1.2"/><circle cx="6" cy="9" r="1.5" fill="var(--emerald)"/><line x1="10" y1="8" x2="14" y2="8" stroke="var(--emerald)" stroke-width="1"/><line x1="10" y1="11" x2="13" y2="11" stroke="var(--emerald)" stroke-width="1"/></svg>
				<span style="font-size: 0.95rem; color: var(--emerald); font-weight: 600;">Jira tickets</span>
			</div>
		</div>

		<!-- Arrow -->
		<svg width="60" height="20" viewBox="0 0 60 20" style="opacity: {flowProgress.current}; overflow: visible;">
			<line x1="0" y1="10" x2="48" y2="10" stroke="var(--text-muted)" stroke-width="1.5"
				pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - flowProgress.current};" />
			<path d="M42 5 L52 10 L42 15" fill="none" stroke="var(--text-muted)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"
				style="opacity: {flowProgress.current};" />
		</svg>

		<!-- Terminal output -->
		<div style="
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 10px; padding: 0; min-width: 380px;
			font-family: var(--r-code-font); font-size: 0.95rem;
			opacity: {termOpacity.current};
			overflow: hidden;
		">
			<div style="display: flex; align-items: center; gap: 6px; padding: 8px 12px; border-bottom: 1px solid var(--border);">
				<span style="width: 8px; height: 8px; border-radius: 50%; background: #ef4444; opacity: 0.7;"></span>
				<span style="width: 8px; height: 8px; border-radius: 50%; background: #fbbf24; opacity: 0.7;"></span>
				<span style="width: 8px; height: 8px; border-radius: 50%; background: #34d399; opacity: 0.7;"></span>
				<span style="font-size: 0.8rem; color: var(--text-muted); margin-left: 6px;">standup output</span>
			</div>
			<div style="padding: 0.8rem 1rem; display: flex; flex-direction: column; gap: 0.35rem;">
				<p style="color: var(--text-muted); opacity: {line1.current};">Yesterday:</p>
				<p style="color: var(--text); padding-left: 0.8rem; opacity: {line2.current};">- Fixed date formatting bug</p>
				<p style="color: var(--text); padding-left: 0.8rem; opacity: {line2.current};">- Started vehicle filter component</p>
				<p style="color: var(--text-muted); margin-top: 0.3rem; opacity: {line3.current};">Today:</p>
				<p style="color: var(--text); padding-left: 0.8rem; opacity: {line4.current};">- Continue JLROV-456</p>
				<p style="color: var(--text); padding-left: 0.8rem; opacity: {line4.current};">- PR review for Thomas</p>
				<p style="color: var(--text-muted); margin-top: 0.3rem; opacity: {line5.current};">Blockers: <span style="color: var(--emerald);">None</span></p>
			</div>
		</div>
	</div>

	<Action
		actions={[
			async () => { await sourcesOpacity.to(1) },
			async () => { await flowProgress.to(1); await termOpacity.to(1); await line1.to(1); await line2.to(1); await line3.to(1); await line4.to(1); await line5.to(1) },
		]}
	/>

	<Transition>
		<p style="font-size: 1.1rem; color: var(--emerald); font-weight: 500;">
			Zero prep time. I just read it out loud.
		</p>
	</Transition>
</div>
