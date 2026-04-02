<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({ transition: 'slide' })
</script>

<script>
	import { Transition } from '$lib/index.js'

	const actions = [
		{ priority: 'NOW', label: 'Disable /v2/login or restrict to internal', color: '#ef4444' },
		{ priority: 'NOW', label: 'Strip password field from /spend/users', color: '#ef4444' },
		{ priority: 'NOW', label: 'Rotate all admin passwords + API keys', color: '#ef4444' },
		{ priority: '24h', label: 'Restrict /ui/ to admin IPs only', color: '#f97316' },
		{ priority: '48h', label: 'Remove API keys from JWT payload', color: '#f97316' },
		{ priority: '1w', label: 'Add rate limiting on login endpoints', color: '#eab308' },
		{ priority: '1w', label: 'Report to LiteLLM upstream (CVE candidates)', color: '#eab308' },
		{ priority: '1m', label: 'Implement proper hashing (bcrypt/argon2)', color: '#60a5fa' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text);">
			Recommendations
		</p>
	</Transition>

	<div style="display: flex; flex-direction: column; gap: 0.4rem; width: 650px;">
		{#each actions as action, i}
			<Transition>
				<div style="
					display: flex; align-items: center; gap: 1rem;
					padding: 0.5rem 1rem;
					border-left: 3px solid {action.color};
					background: var(--surface);
					border-radius: 0 8px 8px 0;
				">
					<span style="
						font-family: var(--r-code-font); font-size: 0.7rem;
						color: {action.color}; font-weight: 700;
						min-width: 35px; text-align: center;
						background: rgba(0,0,0,0.3); padding: 0.15rem 0.3rem; border-radius: 4px;
					">{action.priority}</span>
					<p style="font-size: 0.85rem; color: var(--text);">{action.label}</p>
				</div>
			</Transition>
		{/each}
	</div>

	<Transition>
		<p style="font-size: 0.9rem; color: #ef4444; font-weight: 600; margin-top: 0.5rem;">
			Reports submitted to CERT + Bridge
		</p>
	</Transition>
</div>
