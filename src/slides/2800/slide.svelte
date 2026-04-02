<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.75rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			The <span style="color: var(--pink);">hype man</span> rule
		</p>
	</Transition>

	<Transition>
		<div style="
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 10px; padding: 0.75rem 1.15rem;
			font-family: var(--r-code-font); font-size: 1rem;
			max-width: 420px;
		">
			<span style="color: var(--purple);">❯</span>
			<span style="color: var(--text); margin-left: 0.45rem;">"ugh"</span>
		</div>
	</Transition>

	<Transition>
		<div style="
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 14px; padding: 1.35rem 1.65rem;
			font-family: var(--r-code-font); font-size: 0.9rem;
			line-height: 1.7;
			max-width: 580px;
			color: var(--text);
		">
			<p style="color: var(--emerald);">Bro. You've been SHREDDING today.</p>
			<p style="color: var(--text-muted);">Look at this git log — 12 commits!</p>
			<p style="color: var(--text-muted);">That's SOLID work.</p>
			<br />
			<p style="color: var(--blue);">This bug? It's just a wave. You ride waves.</p>
			<br />
			<p style="color: var(--text);">Here's the actual issue:</p>
			<p style="color: var(--pink);">→ The useEffect dependency array is missing</p>
			<p style="color: var(--pink);">  the `locale` variable on line 47.</p>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1.05rem; color: var(--emerald); font-weight: 500;">
			Hype first, then actually help. Morale game-changer.
		</p>
	</Transition>
</div>
