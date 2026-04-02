<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition, Action } from '$lib/index.js'
	import { tween } from '@animotion/motion'

	let stepsOpacity = tween(0, { duration: 400 })
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.8rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Setting up <span style="color: var(--purple);">plugins</span> / <span style="color: var(--pink);">MCP</span>
		</p>
	</Transition>

	<Transition>
		<div style="display: flex; gap: 1.5rem; max-width: 820px;">
			<!-- Step 1: Marketplace -->
			<div style="
				flex: 1; background: var(--surface); border: 1px solid var(--border);
				border-radius: 12px; padding: 1.1rem 1.3rem;
			">
				<div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.6rem;">
					<span style="font-size: 1.3rem;">🛒</span>
					<span style="font-size: 1rem; font-weight: 700; color: var(--purple);">Marketplace</span>
				</div>
				<p style="font-size: 0.95rem; color: var(--text); line-height: 1.7;">
					Browse & install from the <span style="color: var(--purple); font-weight: 600;">web marketplace</span> or via <span style="color: var(--purple); font-weight: 600;">Cursor Settings</span>.
				</p>
			</div>

			<!-- Step 2: MCP Config -->
			<div style="
				flex: 1; background: var(--surface); border: 1px solid var(--border);
				border-radius: 12px; padding: 1.1rem 1.3rem;
			">
				<div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.6rem;">
					<span style="font-size: 1.3rem;">⚙️</span>
					<span style="font-size: 1rem; font-weight: 700; color: var(--blue);">MCP Config</span>
				</div>
				<pre style="
					font-family: var(--r-code-font); font-size: 0.75rem;
					background: var(--bg); border-radius: 8px; padding: 0.6rem 0.8rem;
					line-height: 1.5; color: var(--text); text-align: left;
					white-space: pre; margin: 0;
				"><span style="color: var(--text-muted);">// .cursor/mcp.json</span>
&#123;
  "mcpServers": &#123;
    "<span style="color: var(--blue);">jira</span>": &#123;
      "command": "npx",
      "args": ["mcp-jira"]
    &#125;
  &#125;
&#125;</pre>
			</div>

			<!-- Step 3: Let Cursor help -->
			<div style="
				flex: 1; background: var(--surface); border: 1px solid var(--border);
				border-radius: 12px; padding: 1.1rem 1.3rem;
			">
				<div style="display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.6rem;">
					<span style="font-size: 1.3rem;">🤖</span>
					<span style="font-size: 1rem; font-weight: 700; color: var(--emerald);">Ask Cursor</span>
				</div>
				<div style="font-size: 0.95rem; color: var(--text); line-height: 1.7;">
					<p>Cursor can help you <span style="color: var(--emerald); font-weight: 600;">set up</span> and configure any plugin.</p>
					<p style="font-size: 0.9rem; color: var(--text-muted); margin-top: 0.4rem;">
						Always review the <span style="color: var(--emerald); font-weight: 600;">settings</span> to limit what tools can do.
					</p>
				</div>
			</div>
		</div>
	</Transition>

	<Action
		actions={[
			async () => { await stepsOpacity.to(1) },
		]}
	/>

	<div style="opacity: {stepsOpacity.current}; transform: translateY({(1 - stepsOpacity.current) * 10}px);">
		<p style="font-size: 1.05rem; color: var(--text-muted);">
			Tip: <code style="color: var(--purple); background: var(--surface); padding: 3px 8px; border-radius: 5px;">Cmd + Shift + J</code> opens Cursor Settings directly.
		</p>
	</div>
</div>
