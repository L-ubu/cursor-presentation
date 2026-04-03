<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'

	const steps = [
		{ num: '1', title: 'Understand scope', detail: 'Read existing auth flow, identify touchpoints', color: 'var(--purple)' },
		{ num: '2', title: 'Database changes', detail: 'Add password_reset_tokens table with expiry column', color: 'var(--blue)' },
		{ num: '3', title: 'API endpoint', detail: 'POST /auth/forgot-password — validate, generate token, send mail', color: 'var(--emerald)' },
		{ num: '4', title: 'Reset page', detail: 'New route /reset-password?token=... with form + validation', color: 'var(--cyan)' },
		{ num: '5', title: 'Tests', detail: 'Token expiry, invalid token, password mismatch, happy path', color: 'var(--pink)' },
	]
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<div style="display: flex; align-items: center; gap: 0.8rem;">
			<span style="
				font-size: 0.8rem; font-weight: 700; color: var(--emerald);
				background: rgba(52, 211, 153, 0.15); padding: 4px 12px;
				border-radius: 6px; text-transform: uppercase; letter-spacing: 0.1em;
			">Plan mode</span>
			<p style="font-size: 2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
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
			<span style="color: var(--emerald);">plan ></span>
			<span style="color: var(--text); margin-left: 0.4rem;">"Add password reset flow to our auth system"</span>
		</div>
	</Transition>

	<Transition>
		<div style="
			max-width: 650px; width: 100%;
			display: flex; flex-direction: column; gap: 0;
		">
			<div style="
				display: flex; align-items: center; gap: 0.5rem;
				padding: 0.6rem 1rem;
				background: rgba(52, 211, 153, 0.08);
				border: 1px solid rgba(52, 211, 153, 0.2);
				border-radius: 10px 10px 0 0;
			">
				<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--emerald)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
					<path d="M9 5H7a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V7a2 2 0 0 0-2-2h-2"/>
					<rect x="9" y="3" width="6" height="4" rx="1"/>
				</svg>
				<span style="font-size: 0.8rem; font-weight: 700; color: var(--emerald); text-transform: uppercase; letter-spacing: 0.08em;">
					Agent Plan
				</span>
			</div>

			<div style="
				background: var(--surface);
				border: 1px solid var(--border);
				border-top: none;
				border-radius: 0 0 10px 10px;
				padding: 0.8rem 0;
			">
				{#each steps as step, i}
					<div style="
						display: flex; align-items: flex-start; gap: 0.7rem;
						padding: 0.5rem 1.2rem;
						{i < steps.length - 1 ? 'border-bottom: 1px solid rgba(255,255,255,0.04);' : ''}
					">
						<span style="
							font-family: var(--r-code-font); font-size: 0.8rem;
							color: {step.color}; font-weight: 700;
							background: {step.color}15;
							width: 24px; height: 24px;
							display: flex; align-items: center; justify-content: center;
							border-radius: 6px; flex-shrink: 0;
						">{step.num}</span>
						<div style="flex: 1; padding-top: 1px;">
							<p style="font-size: 0.95rem; font-weight: 600; color: var(--text);">{step.title}</p>
							<p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 0.1rem;">{step.detail}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 1rem; color: var(--emerald); font-weight: 500;">
			Review the plan  ->  approve  ->  it builds exactly this.
		</p>
	</Transition>
</div>
