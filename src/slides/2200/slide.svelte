<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2.25rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Real prompts with MCP
		</p>
	</Transition>

	<div style="display: flex; flex-direction: column; gap: 1.15rem; max-width: 760px;">
		<Transition>
			<div style="
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 10px; padding: 1.05rem 1.35rem;
				font-family: var(--r-code-font); font-size: 0.95rem;
			">
				<span style="color: var(--purple);">❯</span>
				<span style="color: var(--text); margin-left: 0.45rem;">"Read <span style="color: var(--blue); font-weight: 700; background: rgba(96, 165, 250, 0.12); padding: 2px 6px; border-radius: 4px;">Jira ticket JLROV-123</span> and implement the acceptance criteria."</span>
			</div>
		</Transition>

		<Transition>
			<div style="
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 10px; padding: 1.05rem 1.35rem;
				font-family: var(--r-code-font); font-size: 0.95rem;
			">
				<span style="color: var(--blue);">❯</span>
				<span style="color: var(--text); margin-left: 0.45rem;">"Search <span style="color: var(--purple); font-weight: 700; background: rgba(167, 139, 250, 0.12); padding: 2px 6px; border-radius: 4px;">Confluence</span> for the reservation API docs and update our client."</span>
			</div>
		</Transition>

		<Transition>
			<div style="
				background: var(--surface); border: 1px solid var(--border);
				border-radius: 10px; padding: 1.05rem 1.35rem;
				font-family: var(--r-code-font); font-size: 0.95rem;
			">
				<span style="color: var(--emerald);">❯</span>
				<span style="color: var(--text); margin-left: 0.45rem;">"Look at the <span style="color: var(--pink); font-weight: 700; background: rgba(249, 168, 212, 0.12); padding: 2px 6px; border-radius: 4px;">Figma design</span> and build the component with responsive breakpoints."</span>
			</div>
		</Transition>
	</div>
</div>
