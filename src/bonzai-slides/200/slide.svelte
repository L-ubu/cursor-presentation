<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.5rem; font-weight: 700; color: var(--text); letter-spacing: -0.03em;">
			What is <span style="color: #ef4444;">Bonzai</span>?
		</p>
	</Transition>

	<Transition>
		<div style="display: flex; gap: 1.5rem; flex-wrap: wrap; justify-content: center; max-width: 800px;">
			<div style="padding: 1rem 1.5rem; background: var(--surface); border: 1px solid var(--border); border-radius: 12px; text-align: center; min-width: 200px;">
				<p style="font-size: 1.3rem; font-weight: 600; color: var(--purple);">iO's Internal AI</p>
				<p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 0.3rem;">LLM Gateway for all employees</p>
			</div>
			<div style="padding: 1rem 1.5rem; background: var(--surface); border: 1px solid var(--border); border-radius: 12px; text-align: center; min-width: 200px;">
				<p style="font-size: 1.3rem; font-weight: 600; color: var(--blue);">Built on LiteLLM</p>
				<p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 0.3rem;">Open-source proxy framework</p>
			</div>
			<div style="padding: 1rem 1.5rem; background: var(--surface); border: 1px solid var(--border); border-radius: 12px; text-align: center; min-width: 200px;">
				<p style="font-size: 1.3rem; font-weight: 600; color: var(--emerald);">1,874 Users</p>
				<p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 0.3rem;">Every iO employee has access</p>
			</div>
		</div>
	</Transition>

	<Transition>
		<div style="margin-top: 1rem;">
			<p style="font-size: 1.1rem; font-weight: 600; color: var(--text); margin-bottom: 0.8rem; text-align: center;">Tools We Used</p>
			<div style="display: flex; gap: 1rem;">
				{#each [
					{ name: 'curl', desc: 'HTTP requests' },
					{ name: 'python3', desc: 'JSON parsing' },
					{ name: 'base64', desc: 'JWT decoding' },
					{ name: 'Cursor AI', desc: 'Analysis & automation' }
				] as tool}
					<div style="padding: 0.6rem 1.2rem; background: var(--surface); border-radius: 8px; border-left: 3px solid var(--pink); text-align: center;">
						<p style="font-size: 0.95rem; font-weight: 600; color: var(--pink); font-family: var(--r-code-font);">{tool.name}</p>
						<p style="font-size: 0.7rem; color: var(--text-muted);">{tool.desc}</p>
					</div>
				{/each}
			</div>
		</div>
	</Transition>
</div>
