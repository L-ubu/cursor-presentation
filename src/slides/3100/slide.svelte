<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let stage = $state(0)
	let badge1 = tween(0, { duration: 350 })
	let badge2 = tween(0, { duration: 350 })
	let badge3 = tween(0, { duration: 350 })
	let badge4 = tween(0, { duration: 350 })
	let finalOpacity = tween(0, { duration: 500 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Remember your <span style="color: var(--purple);">first prompt</span>?
		</p>
	</Transition>

	<Transition>
		<div style="
			width: 100%; max-width: 740px;
			background: #1b1b2f; border: 1px solid var(--border);
			border-radius: 10px; padding: 1.3rem 1.6rem;
			font-family: var(--r-code-font); font-size: 1rem;
			line-height: 1.7; color: var(--text);
		">
		{#if stage === 0}
			<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Add a loading spinner to the submit button</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">while the API call is in progress."</span><span class="cursor-blink"></span>
		{:else if stage === 1}
			<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Add a loading spinner in{' '}</span><span style="color: var(--purple); font-weight: 600;">@ReservationForm.tsx</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">while the API from{' '}</span><span style="color: var(--purple); font-weight: 600;">@services/reservations</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">is loading."</span><span class="cursor-blink"></span>
		{:else if stage === 2}
			<span style="color: var(--emerald); font-weight: 700;">plan</span>{' '}<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Add a loading spinner in{' '}</span><span style="color: var(--purple);">@ReservationForm.tsx</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">while the API from{' '}</span><span style="color: var(--purple);">@services/reservations</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">is loading."</span><span class="cursor-blink"></span>
		{:else if stage === 3}
			<span style="color: var(--emerald);">plan</span>{' '}<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Add a loading spinner in{' '}</span><span style="color: var(--purple);">@ReservationForm.tsx</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">while the API from{' '}</span><span style="color: var(--purple);">@services/reservations</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">is loading. Follow the{' '}</span><span style="color: var(--blue); font-weight: 600;">Confluence component</span><br/>
			<span style="padding-left: 1.2rem;"><span style="color: var(--blue); font-weight: 600;">guidelines via MCP</span><span style="color: #e4e4e7;">."</span></span><span class="cursor-blink"></span>
		{:else}
			<span style="color: var(--emerald);">plan</span>{' '}<span style="color: var(--text-muted);">❯</span>{' '}<span style="color: #e4e4e7;">"Add a loading spinner in{' '}</span><span style="color: var(--purple);">@ReservationForm.tsx</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">while the API from{' '}</span><span style="color: var(--purple);">@services/reservations</span><br/>
			<span style="padding-left: 1.2rem; color: #e4e4e7;">is loading. Follow the{' '}</span><span style="color: var(--blue);">Confluence component</span><br/>
			<span style="padding-left: 1.2rem;"><span style="color: var(--blue);">guidelines via MCP</span><span style="color: #e4e4e7;">.</span></span><br/>
			<span style="padding-left: 1.2rem;"><span style="color: var(--pink); font-weight: 600;">Run pre-mr-checklist when done.</span><span style="color: #e4e4e7;">"</span></span><span class="cursor-blink"></span>
		{/if}
		</div>
	</Transition>

	<!-- Badges row — each appears with its corresponding step -->
	<div style="display: flex; gap: 0.8rem; flex-wrap: wrap; justify-content: center; font-size: 0.85rem; min-height: 32px;">
		<span style="
			color: var(--purple); background: rgba(167, 139, 250, 0.15);
			padding: 4px 12px; border-radius: 6px; font-weight: 600;
			opacity: {badge1.current}; transform: translateY({(1 - badge1.current) * 8}px);
		">@ references</span>
		<span style="
			color: var(--emerald); background: rgba(52, 211, 153, 0.15);
			padding: 4px 12px; border-radius: 6px; font-weight: 600;
			opacity: {badge2.current}; transform: translateY({(1 - badge2.current) * 8}px);
		">plan mode</span>
		<span style="
			color: var(--blue); background: rgba(96, 165, 250, 0.15);
			padding: 4px 12px; border-radius: 6px; font-weight: 600;
			opacity: {badge3.current}; transform: translateY({(1 - badge3.current) * 8}px);
		">MCP</span>
		<span style="
			color: var(--pink); background: rgba(244, 114, 182, 0.15);
			padding: 4px 12px; border-radius: 6px; font-weight: 600;
			opacity: {badge4.current}; transform: translateY({(1 - badge4.current) * 8}px);
		">rules & skills</span>
	</div>

	<Action
		actions={[
			async () => { stage = 1; await badge1.to(1) },
			async () => { stage = 2; await badge2.to(1) },
			async () => { stage = 3; await badge3.to(1) },
			async () => { stage = 4; await badge4.to(1) },
			async () => { await finalOpacity.to(1) },
		]}
	/>

	<p style="
		font-size: 1.15rem; color: var(--emerald); font-weight: 600;
		opacity: {finalOpacity.current};
	">
		Same task. Massively better result.
	</p>
</div>
