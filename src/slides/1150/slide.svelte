<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const steps = [
		{ num: '1', title: 'Understand scope', detail: 'Read existing auth flow, identify touchpoints', color: 'var(--purple)' },
		{ num: '2', title: 'Database changes', detail: 'Add password_reset_tokens table with expiry column', color: 'var(--blue)' },
		{ num: '3', title: 'API endpoint', detail: 'POST /auth/forgot-password — validate email, generate token, send mail', color: 'var(--emerald)' },
		{ num: '4', title: 'Reset page', detail: 'New route /reset-password?token=... with form + validation', color: 'var(--cyan)' },
		{ num: '5', title: 'Tests', detail: 'Token expiry, invalid token, password mismatch, happy path', color: 'var(--pink)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.6rem;">
	<Transition visible>
		<div style="display: flex; align-items: center; gap: 0.6rem;">
			<span style="
				font-size: 0.85rem; font-weight: 700; color: var(--emerald);
				background: rgba(52, 211, 153, 0.15); padding: 3px 10px;
				border-radius: 6px; text-transform: uppercase; letter-spacing: 0.1em;
			">Plan mode</span>
			<p style="font-size: 1.8rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
				Think first, build second
			</p>
		</div>
	</Transition>

	<Transition>
		<div style="
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 10px; padding: 0.85rem 1.3rem;
			font-family: var(--r-code-font); font-size: 1rem;
			max-width: 650px; width: 100%;
		">
			<span style="color: var(--emerald);">plan ❯</span>
			<span style="color: var(--text); margin-left: 0.4rem;">"Add password reset flow to our auth system"</span>
		</div>
	</Transition>

	<Transition>
		<div style="
			background: var(--surface); border: 1px solid var(--border);
			border-radius: 14px; padding: 1.2rem 1.5rem;
			max-width: 650px; width: 100%;
			display: flex; flex-direction: column; gap: 0.1rem;
		">
			<p style="font-size: 0.9rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.1em; font-weight: 600; margin-bottom: 0.5rem;">
				Agent plan
			</p>
		<div class="stagger-children" style="display: flex; flex-direction: column; gap: 0.45rem;">
			{#each steps as step}
				<div style="display: flex; align-items: flex-start; gap: 0.8rem; padding: 0.4rem 0;">
					<span style="
						font-family: var(--r-code-font); font-size: 0.9rem;
						color: {step.color}; font-weight: 700;
						width: 22px; flex-shrink: 0; text-align: right;
					">{step.num}</span>
					<div style="flex: 1;">
						<p style="font-size: 1rem; font-weight: 600; color: var(--text);">{step.title}</p>
						<p style="font-size: 0.9rem; color: var(--text-muted);">{step.detail}</p>
					</div>
				</div>
			{/each}
		</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1rem; color: var(--emerald); font-weight: 500;">
			Review the plan → approve → it builds exactly this.
		</p>
	</Transition>
</div>
