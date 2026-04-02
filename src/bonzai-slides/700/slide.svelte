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
			<span style="font-size: 0.75rem; color: #f97316; font-weight: 700; background: rgba(249,115,22,0.15); padding: 0.2rem 0.6rem; border-radius: 6px;">STEP 2</span>
			<p style="font-size: 1.8rem; font-weight: 700; color: var(--text);">
				Login as Admin
			</p>
		</div>
	</Transition>

	<div style="display: flex; gap: 1.5rem;">
		<Transition>
			<div style="flex: 1; background: #1a1a2e; padding: 1rem 1.2rem; border-radius: 10px; border-top: 3px solid #34d399;">
				<p style="font-family: var(--r-code-font); font-size: 0.7rem; color: var(--text-muted); margin-bottom: 0.5rem;">Expected (correct)</p>
				<p style="font-family: var(--r-code-font); font-size: 0.75rem; color: #d4d4d4;">
					stored = <span style="color: #34d399;">hash</span>(password)<br /><br />
					login_check:<br />
					&nbsp;&nbsp;<span style="color: #34d399;">hash</span>(input) == stored
				</p>
				<p style="font-size: 0.7rem; color: #34d399; margin-top: 0.5rem; font-weight: 600;">Hash then compare</p>
			</div>
		</Transition>
		<Transition>
			<div style="flex: 1; background: #1a1a2e; padding: 1rem 1.2rem; border-radius: 10px; border-top: 3px solid #ef4444;">
				<p style="font-family: var(--r-code-font); font-size: 0.7rem; color: var(--text-muted); margin-bottom: 0.5rem;">Actual (broken)</p>
				<p style="font-family: var(--r-code-font); font-size: 0.75rem; color: #d4d4d4;">
					stored = hash(password)<br /><br />
					login_check:<br />
					&nbsp;&nbsp;<span style="color: #ef4444;">input == stored</span>
				</p>
				<p style="font-size: 0.7rem; color: #ef4444; margin-top: 0.5rem; font-weight: 600;">Direct comparison!</p>
			</div>
		</Transition>
	</div>

	<Transition>
		<div style="background: #1a1a2e; padding: 1rem 1.2rem; border-radius: 10px; border-left: 3px solid #f97316;">
			<p style="font-family: var(--r-code-font); font-size: 0.8rem; color: #d4d4d4;">
				curl -X POST ".../v2/login" \<br />
				&nbsp;&nbsp;-d '&#123;"username":"<span style="color: #60a5fa;">admin@iodigital.com</span>",<br />
				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"password":"<span style="color: #ef4444;">HASH_FROM_STEP_1</span>"&#125;'
			</p>
			<p style="font-family: var(--r-code-font); font-size: 0.75rem; color: #34d399; margin-top: 0.5rem;">
				Response: HTTP 200 OK + Set-Cookie: JWT
			</p>
		</div>
	</Transition>
</div>
