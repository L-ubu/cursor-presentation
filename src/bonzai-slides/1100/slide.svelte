<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text);">
			Whose Fault Is It?
		</p>
	</Transition>

	<div style="display: flex; gap: 2rem; max-width: 800px;">
		<Transition>
			<div style="flex: 1; padding: 1.2rem; background: var(--surface); border-radius: 12px; border-top: 3px solid #ef4444;">
				<p style="font-size: 1.1rem; font-weight: 700; color: #ef4444; margin-bottom: 0.8rem;">LiteLLM Framework</p>
				<div style="display: flex; flex-direction: column; gap: 0.4rem;">
					{#each [
						'/spend/users leaks passwords',
						'/v2/login no re-hash',
						'JWT contains API keys',
						'Model config exposed',
						'No rate limiting',
						'Stack traces in errors'
					] as item}
						<p style="font-size: 0.75rem; color: var(--text-muted); padding-left: 0.8rem; border-left: 2px solid #ef4444;">
							{item}
						</p>
					{/each}
				</div>
				<p style="font-size: 0.7rem; color: #ef4444; margin-top: 0.8rem; font-weight: 600;">
					Affects ALL LiteLLM deployments worldwide
				</p>
			</div>
		</Transition>

		<Transition>
			<div style="flex: 1; padding: 1.2rem; background: var(--surface); border-radius: 12px; border-top: 3px solid #f97316;">
				<p style="font-size: 1.1rem; font-weight: 700; color: #f97316; margin-bottom: 0.8rem;">Bonzai Config</p>
				<div style="display: flex; flex-direction: column; gap: 0.4rem;">
					{#each [
						'252 external user emails',
						'No budget limits (88%)',
						'No key expiry (88%)',
						'Client names in key aliases',
						'Admin UI publicly accessible',
						'"uncompliant" model for all'
					] as item}
						<p style="font-size: 0.75rem; color: var(--text-muted); padding-left: 0.8rem; border-left: 2px solid #f97316;">
							{item}
						</p>
					{/each}
				</div>
				<p style="font-size: 0.7rem; color: #f97316; margin-top: 0.8rem; font-weight: 600;">
					Specific to iO Digital's deployment
				</p>
			</div>
		</Transition>
	</div>
</div>
