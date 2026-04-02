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
			The Full Attack Chain
		</p>
	</Transition>

	<div style="display: flex; flex-direction: column; gap: 0.8rem; width: 650px;">
		<Transition>
			<div style="display: flex; align-items: center; gap: 1rem; padding: 0.8rem 1.2rem; background: var(--surface); border-radius: 10px; border-left: 3px solid #ef4444;">
				<span style="font-size: 1.5rem; font-weight: 800; color: #ef4444; min-width: 30px;">1</span>
				<div>
					<p style="font-size: 1rem; font-weight: 600; color: var(--text);">GET /spend/users</p>
					<p style="font-size: 0.75rem; color: var(--text-muted);">Any API key -- returns 1,874 users with password hashes</p>
				</div>
			</div>
		</Transition>

		<Transition>
			<div style="display: flex; justify-content: center;">
				<svg width="20" height="30" viewBox="0 0 20 30"><path d="M10 0 V22 M3 16 L10 25 L17 16" fill="none" stroke="#f97316" stroke-width="2" stroke-linecap="round"/></svg>
			</div>
		</Transition>

		<Transition>
			<div style="display: flex; align-items: center; gap: 1rem; padding: 0.8rem 1.2rem; background: var(--surface); border-radius: 10px; border-left: 3px solid #f97316;">
				<span style="font-size: 1.5rem; font-weight: 800; color: #f97316; min-width: 30px;">2</span>
				<div>
					<p style="font-size: 1rem; font-weight: 600; color: var(--text);">POST /v2/login</p>
					<p style="font-size: 0.75rem; color: var(--text-muted);">Send hash as password -- returns JWT session</p>
				</div>
			</div>
		</Transition>

		<Transition>
			<div style="display: flex; justify-content: center;">
				<svg width="20" height="30" viewBox="0 0 20 30"><path d="M10 0 V22 M3 16 L10 25 L17 16" fill="none" stroke="#eab308" stroke-width="2" stroke-linecap="round"/></svg>
			</div>
		</Transition>

		<Transition>
			<div style="display: flex; align-items: center; gap: 1rem; padding: 0.8rem 1.2rem; background: var(--surface); border-radius: 10px; border-left: 3px solid #eab308;">
				<span style="font-size: 1.5rem; font-weight: 800; color: #eab308; min-width: 30px;">3</span>
				<div>
					<p style="font-size: 1rem; font-weight: 600; color: var(--text);">Decode JWT (base64)</p>
					<p style="font-size: 0.75rem; color: var(--text-muted);">Contains full plaintext admin API key (sk-...)</p>
				</div>
			</div>
		</Transition>

		<Transition>
			<div style="display: flex; justify-content: center;">
				<svg width="20" height="30" viewBox="0 0 20 30"><path d="M10 0 V22 M3 16 L10 25 L17 16" fill="none" stroke="#ef4444" stroke-width="2" stroke-linecap="round"/></svg>
			</div>
		</Transition>

		<Transition>
			<div style="padding: 0.8rem 1.2rem; background: rgba(239,68,68,0.15); border: 2px solid #ef4444; border-radius: 10px; text-align: center;">
				<p style="font-size: 1.1rem; font-weight: 700; color: #ef4444;">FULL ADMIN ACCESS</p>
				<p style="font-size: 0.75rem; color: var(--text-muted); margin-top: 0.3rem;">Users, keys, cloud credentials, model config, admin UI</p>
			</div>
		</Transition>
	</div>

	<Transition>
		<div style="display: flex; gap: 2rem; margin-top: 0.3rem;">
			<p style="font-size: 0.85rem; color: var(--pink); font-weight: 600;">Time: ~10 seconds</p>
			<p style="font-size: 0.85rem; color: var(--pink); font-weight: 600;">Skill: copy-paste curl</p>
			<p style="font-size: 0.85rem; color: var(--pink); font-weight: 600;">Who: any of 1,874 users</p>
		</div>
	</Transition>
</div>
