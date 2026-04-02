<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2rem; font-weight: 700; color: var(--text);">
			20 Vulnerabilities Found
		</p>
	</Transition>

	<div style="display: flex; gap: 1.5rem;">
		<Transition>
			<div style="padding: 1.2rem 2rem; background: rgba(239, 68, 68, 0.1); border: 2px solid #ef4444; border-radius: 12px; text-align: center; min-width: 140px;">
				<p style="font-size: 2.5rem; font-weight: 800; color: #ef4444;">3</p>
				<p style="font-size: 0.85rem; font-weight: 600; color: #ef4444;">CRITICAL</p>
			</div>
		</Transition>
		<Transition>
			<div style="padding: 1.2rem 2rem; background: rgba(249, 115, 22, 0.1); border: 2px solid #f97316; border-radius: 12px; text-align: center; min-width: 140px;">
				<p style="font-size: 2.5rem; font-weight: 800; color: #f97316;">8</p>
				<p style="font-size: 0.85rem; font-weight: 600; color: #f97316;">HIGH</p>
			</div>
		</Transition>
		<Transition>
			<div style="padding: 1.2rem 2rem; background: rgba(234, 179, 8, 0.1); border: 2px solid #eab308; border-radius: 12px; text-align: center; min-width: 140px;">
				<p style="font-size: 2.5rem; font-weight: 800; color: #eab308;">7</p>
				<p style="font-size: 0.85rem; font-weight: 600; color: #eab308;">MEDIUM</p>
			</div>
		</Transition>
		<Transition>
			<div style="padding: 1.2rem 2rem; background: rgba(96, 165, 250, 0.1); border: 2px solid #60a5fa; border-radius: 12px; text-align: center; min-width: 140px;">
				<p style="font-size: 2.5rem; font-weight: 800; color: #60a5fa;">2</p>
				<p style="font-size: 0.85rem; font-weight: 600; color: #60a5fa;">LOW</p>
			</div>
		</Transition>
	</div>

	<Transition>
		<p style="font-size: 1.2rem; color: #ef4444; font-weight: 600; margin-top: 0.5rem;">
			Let's focus on the critical chain.
		</p>
	</Transition>
</div>
