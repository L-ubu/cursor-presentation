<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let step1 = tween(0, { duration: 500 })
	let line1 = tween(0, { duration: 600 })
	let tip1 = tween(0, { duration: 250 })
	let step2 = tween(0, { duration: 500 })
	let line2 = tween(0, { duration: 600 })
	let tip2 = tween(0, { duration: 250 })
	let step3 = tween(0, { duration: 500 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.4rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			How Cursor <span class="gradient-text" style="font-weight: 800;">knows</span> your code
		</p>
	</Transition>

	<svg width="700" height="140" viewBox="0 0 700 140" style="overflow: visible;">
		<!-- Step 1: Your Code -->
		<g style="opacity: {step1.current}; transform: translateY({(1 - step1.current) * 8}px);">
			<circle cx="80" cy="70" r="48" fill="none" stroke="var(--purple)" stroke-width="1.5" />
			<circle cx="80" cy="70" r="48" fill="rgba(167, 139, 250, 0.06)" />
			<path d="M68 50 L68 90 L92 90 L92 58 L84 50 Z" fill="none" stroke="var(--purple)" stroke-width="1.5" stroke-linejoin="round" />
			<path d="M84 50 L84 58 L92 58" fill="none" stroke="var(--purple)" stroke-width="1.5" stroke-linejoin="round" />
			<line x1="74" y1="68" x2="86" y2="68" stroke="var(--purple)" stroke-width="1" opacity="0.5" />
			<line x1="74" y1="74" x2="84" y2="74" stroke="var(--purple)" stroke-width="1" opacity="0.5" />
			<line x1="74" y1="80" x2="88" y2="80" stroke="var(--purple)" stroke-width="1" opacity="0.5" />
			<text x="80" y="132" text-anchor="middle" fill="var(--purple)" font-size="13" font-weight="600" font-family="Inter Variable, sans-serif">Your Code</text>
		</g>

		<!-- Arrow 1: line then tip -->
		<line x1="135" y1="70" x2="260" y2="70" stroke="var(--purple)" stroke-width="1.5"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - line1.current};" />
		<path d="M253 63 L268 70 L253 77" fill="none" stroke="var(--purple)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"
			style="opacity: {tip1.current}; transform: scale({0.6 + tip1.current * 0.4}); transform-origin: 268px 70px;" />

		<!-- Step 2: Chunking -->
		<g style="opacity: {step2.current}; transform: translateY({(1 - step2.current) * 8}px);">
			<circle cx="330" cy="70" r="48" fill="none" stroke="var(--blue)" stroke-width="1.5" />
			<circle cx="330" cy="70" r="48" fill="rgba(96, 165, 250, 0.06)" />
			<line x1="315" y1="55" x2="345" y2="55" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" />
			<line x1="315" y1="65" x2="340" y2="65" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" />
			<line x1="310" y1="75" x2="350" y2="75" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" opacity="0.4" stroke-dasharray="4 3" />
			<line x1="315" y1="85" x2="342" y2="85" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" />
			<text x="330" y="132" text-anchor="middle" fill="var(--blue)" font-size="13" font-weight="600" font-family="Inter Variable, sans-serif">Chunking</text>
		</g>

		<!-- Arrow 2: line then tip -->
		<line x1="385" y1="70" x2="510" y2="70" stroke="var(--blue)" stroke-width="1.5"
			pathLength="1" stroke-dasharray="1" style="stroke-dashoffset: {1 - line2.current};" />
		<path d="M503 63 L518 70 L503 77" fill="none" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"
			style="opacity: {tip2.current}; transform: scale({0.6 + tip2.current * 0.4}); transform-origin: 518px 70px;" />

		<!-- Step 3: Vectors -->
		<g style="opacity: {step3.current}; transform: translateY({(1 - step3.current) * 8}px);">
			<circle cx="580" cy="70" r="48" fill="none" stroke="var(--emerald)" stroke-width="1.5" />
			<circle cx="580" cy="70" r="48" fill="rgba(52, 211, 153, 0.06)" />
			{#each [[565, 55], [580, 55], [595, 55], [570, 68], [585, 68], [600, 68], [565, 81], [580, 81], [595, 81]] as [dx, dy], i}
				<circle cx={dx} cy={dy} r="3" fill="var(--emerald)" opacity={0.3 + (i % 3) * 0.25} />
			{/each}
			<text x="580" y="132" text-anchor="middle" fill="var(--emerald)" font-size="13" font-weight="600" font-family="Inter Variable, sans-serif">Vectors</text>
		</g>

		<!-- Instant search trail -->
		<g style="opacity: {step3.current};">
			<line x1="635" y1="70" x2="690" y2="70" stroke="var(--emerald)" stroke-width="1" stroke-dasharray="6 4" opacity="0.5" />
			<text x="695" y="74" fill="var(--text-muted)" font-size="11" font-family="Inter Variable, sans-serif" opacity="0.7">instant search</text>
		</g>
	</svg>

	<Action
		actions={[
			async () => { await step1.to(1) },
			async () => { await line1.to(1); await tip1.to(1); await step2.to(1) },
			async () => { await line2.to(1); await tip2.to(1); await step3.to(1) },
		]}
	/>

	<Transition>
		<p style="font-size: 1.1rem; color: var(--text-muted); max-width: 700px; text-align: center;">
			100% local. Auto-updates as you edit.
			<code style="color: var(--purple); background: var(--surface); padding: 4px 10px; border-radius: 6px; font-size: 1rem;">@codebase</code>
			gives you millisecond semantic search.
		</p>
	</Transition>
</div>
