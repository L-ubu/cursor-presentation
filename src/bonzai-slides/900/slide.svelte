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
			<span style="font-size: 0.75rem; color: #eab308; font-weight: 700; background: rgba(234,179,8,0.15); padding: 0.2rem 0.6rem; border-radius: 6px;">STEP 3</span>
			<p style="font-size: 1.8rem; font-weight: 700; color: var(--text);">
				Decode JWT, Get Admin Key
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="background: #1a1a2e; padding: 1rem 1.2rem; border-radius: 10px; border-left: 3px solid #eab308;">
			<p style="font-family: var(--r-code-font); font-size: 0.7rem; color: var(--text-muted); margin-bottom: 0.4rem;">JWT from Set-Cookie header (base64 decode middle segment)</p>
			<p style="font-family: var(--r-code-font); font-size: 0.8rem; color: #d4d4d4;">
				echo "MIDDLE_PART" | base64 -d
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="background: #1a1a2e; padding: 1.2rem 1.5rem; border-radius: 10px; border-left: 3px solid #ef4444;">
			<p style="font-family: var(--r-code-font); font-size: 0.7rem; color: var(--text-muted); margin-bottom: 0.4rem;">Decoded payload</p>
			<p style="font-family: var(--r-code-font); font-size: 0.8rem; color: #d4d4d4;">
				{'{'}<br />
				&nbsp;&nbsp;"user_id": "<span style="color: #60a5fa;">admin@iodigital.com</span>",<br />
				&nbsp;&nbsp;"user_role": "<span style="color: #ef4444;">proxy_admin</span>",<br />
				&nbsp;&nbsp;"key": "<span style="color: #ef4444; font-weight: 700;">sk-xRUet_7BaMxXndF4vkMLWw</span>",<br />
				&nbsp;&nbsp;"exp": 1743350000<br />
				{'}'}
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="display: flex; gap: 1rem; margin-top: 0.3rem;">
			<div style="padding: 0.6rem 1rem; background: rgba(239,68,68,0.1); border-radius: 8px; border: 1px solid #ef4444;">
				<p style="font-size: 0.85rem; color: #ef4444; font-weight: 600;">Full admin API key in plaintext</p>
			</div>
			<div style="padding: 0.6rem 1rem; background: rgba(239,68,68,0.1); border-radius: 8px; border: 1px solid #ef4444;">
				<p style="font-size: 0.85rem; color: #ef4444; font-weight: 600;">Works as Bearer token on all endpoints</p>
			</div>
		</div>
	</Transition>
</div>
