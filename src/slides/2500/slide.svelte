<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween, all } from '@animotion/motion'

	let pushOpacity = tween(0, { duration: 400 })
	let handoffLine = tween(0, { duration: 600 })
	let cloudScale = tween(0, { duration: 500 })
	let step1 = tween(0, { duration: 300 })
	let step2 = tween(0, { duration: 300 })
	let step3 = tween(0, { duration: 300 })
	let step4 = tween(0, { duration: 300 })
	let doneGlow = tween(0, { duration: 600 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Cloud Agents — set it and forget it
		</p>
	</Transition>

	<div style="display: flex; align-items: flex-start; gap: 0;">
		<!-- Step 1: Push from IDE -->
		<div style="
			display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
			opacity: {pushOpacity.current};
			transform: translateY({(1 - pushOpacity.current) * 15}px);
		">
			<div style="
				width: 56px; height: 56px; border-radius: 12px;
				background: var(--surface); border: 2px solid var(--purple);
				display: flex; align-items: center; justify-content: center;
			">
				<svg width="26" height="26" viewBox="0 0 24 24" fill="none">
					<rect x="3" y="3" width="18" height="18" rx="3" stroke="var(--purple)" stroke-width="1.5"/>
					<path d="M8 12h4m0 0V8m0 4l4 4" stroke="var(--purple)" stroke-width="1.5" stroke-linecap="round"/>
				</svg>
			</div>
			<span style="font-size: 0.9rem; font-weight: 600; color: var(--purple);">Push task</span>
			<span style="font-size: 0.75rem; color: var(--text-muted);">from your IDE</span>
		</div>

		<!-- Handoff line — aligned to icon center (28px from top) -->
		{#if handoffLine.current > 0.01}
			<svg width="60" height="56" viewBox="0 0 60 56" style="overflow: visible; flex-shrink: 0;">
				<line x1="0" y1="28" x2={52 * handoffLine.current} y2="28"
					stroke="var(--text-muted)" stroke-width="1.5" stroke-dasharray="4 3"
					style="opacity: {Math.min(handoffLine.current * 2, 1)};" />
				<path d="M46 22 L56 28 L46 34" fill="none" stroke="var(--text-muted)" stroke-width="1.5"
					stroke-linecap="round" stroke-linejoin="round" style="opacity: {handoffLine.current > 0.9 ? 1 : 0};" />
			</svg>
		{:else}
			<div style="width: 60px; height: 56px; flex-shrink: 0;"></div>
		{/if}

		<!-- Cloud VM block -->
		<div style="
			display: flex; flex-direction: column; align-items: center; gap: 0.7rem;
			padding: 1.2rem 2rem;
			background: rgba(96, 165, 250, 0.04);
			border: 1px solid rgba(96, 165, 250, 0.15);
			border-radius: 14px;
			opacity: {cloudScale.current};
			transform: scale({0.9 + cloudScale.current * 0.1});
		">
			<div style="display: flex; align-items: center; gap: 0.5rem;">
				<svg width="20" height="20" viewBox="0 0 24 24" fill="none">
					<path d="M6 19a4 4 0 01-.88-7.9A6 6 0 0117.65 8.1 4 4 0 0118 16H6z" stroke="var(--blue)" stroke-width="1.5" fill="none"/>
				</svg>
				<span style="font-size: 1rem; font-weight: 700; color: var(--blue);">Cloud Agent VM</span>
			</div>

			<div style="display: flex; flex-direction: column; gap: 0.35rem; width: 100%;">
				{#each [
					{ label: 'Writes code', t: step1 },
					{ label: 'Runs tests', t: step2 },
					{ label: 'Creates PR', t: step3 },
					{ label: 'Fixes CI', t: step4 }
				] as step}
					<div style="
						display: flex; align-items: center; gap: 0.5rem;
						opacity: {step.t.current};
						transform: translateX({(1 - step.t.current) * 10}px);
					">
						<svg width="14" height="14" viewBox="0 0 14 14">
							<path d="M3 7l3 3 5-5" fill="none" stroke="var(--emerald)" stroke-width="1.8"
								stroke-linecap="round" stroke-linejoin="round"
								pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - step.t.current};" />
						</svg>
						<span style="font-size: 0.9rem; color: var(--text);">{step.label}</span>
					</div>
				{/each}
			</div>
		</div>

		<!-- Done line — aligned to icon center (28px from top) -->
		{#if doneGlow.current > 0.01}
			<svg width="60" height="56" viewBox="0 0 60 56" style="overflow: visible; flex-shrink: 0;">
				<line x1="0" y1="28" x2={52 * doneGlow.current} y2="28"
					stroke="var(--text-muted)" stroke-width="1.5" stroke-dasharray="4 3"
					style="opacity: {Math.min(doneGlow.current * 2, 1)};" />
				<path d="M46 22 L56 28 L46 34" fill="none" stroke="var(--text-muted)" stroke-width="1.5"
					stroke-linecap="round" stroke-linejoin="round" style="opacity: {doneGlow.current > 0.9 ? 1 : 0};" />
			</svg>
		{:else}
			<div style="width: 60px; height: 56px; flex-shrink: 0;"></div>
		{/if}

		<!-- Notification -->
		<div style="
			display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
			opacity: {doneGlow.current};
			transform: translateY({(1 - doneGlow.current) * 15}px);
		">
			<div style="
				width: 56px; height: 56px; border-radius: 12px;
				background: var(--surface); border: 2px solid var(--emerald);
				display: flex; align-items: center; justify-content: center;
				box-shadow: 0 0 {doneGlow.current * 16}px rgba(52, 211, 153, 0.25);
			">
				<svg width="26" height="26" viewBox="0 0 24 24" fill="none">
					<path d="M13.73 21a2 2 0 01-3.46 0M18 8A6 6 0 006 8c0 7-3 9-3 9h18s-3-2-3-9" stroke="var(--emerald)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
				</svg>
			</div>
			<span style="font-size: 0.9rem; font-weight: 600; color: var(--emerald);">Done!</span>
			<span style="font-size: 0.75rem; color: var(--text-muted);">notification</span>
		</div>
	</div>

	<Action
		actions={[
			async () => { await pushOpacity.to(1) },
			async () => {
				await handoffLine.to(1)
				await cloudScale.to(1)
				await step1.to(1)
				await step2.to(1)
				await step3.to(1)
				await step4.to(1)
			},
			async () => { await doneGlow.to(1) },
		]}
	/>

	<Transition>
		<p style="font-size: 1.15rem; color: var(--emerald); font-weight: 500;">
			Go get coffee. Come back to a finished PR.
		</p>
	</Transition>
</div>
