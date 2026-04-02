<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script>
	import { Transition } from '$lib/index.js'
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 2rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			What is a <span style="color: var(--purple);">plugin</span>?
		</p>
	</Transition>

	<Transition>
		<p style="font-size: 1.15rem; color: var(--text-muted); max-width: 650px; text-align: center; line-height: 1.6;">
			A plugin bundles <span style="color: var(--blue); font-weight: 600;">rules</span>,
			<span style="color: var(--emerald); font-weight: 600;">skills</span>, and
			<span style="color: var(--pink); font-weight: 600;">MCP servers</span>
			into a single installable package.
		</p>
	</Transition>

	<Transition>
		<div style="display: flex; gap: 0; align-items: center; margin-top: 0.5rem;">
			<!-- Bundle wrapper -->
			<div style="
				position: relative;
				display: flex; gap: 0.8rem; align-items: center;
				background: linear-gradient(135deg, rgba(167, 139, 250, 0.08), rgba(167, 139, 250, 0.03));
				border: 2px dashed rgba(167, 139, 250, 0.35);
				border-radius: 16px; padding: 1.2rem 1.6rem;
			">
				<!-- Label -->
				<div style="
					position: absolute; top: -0.7rem; left: 50%; transform: translateX(-50%);
					background: var(--bg); padding: 0 0.6rem;
					font-size: 0.75rem; font-weight: 600; color: var(--purple);
					letter-spacing: 0.08em; text-transform: uppercase;
				">Plugin</div>

				<div style="
					background: var(--surface); border: 1px solid var(--border);
					border-radius: 10px; padding: 1rem 1.4rem; text-align: center; min-width: 90px;
				">
					<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--blue)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="margin: 0 auto 0.4rem;">
						<path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
						<polyline points="14 2 14 8 20 8"/>
						<line x1="16" y1="13" x2="8" y2="13"/>
						<line x1="16" y1="17" x2="8" y2="17"/>
					</svg>
					<p style="font-size: 0.9rem; color: var(--blue); font-weight: 600;">Rules</p>
				</div>

				<div style="
					background: var(--surface); border: 1px solid var(--border);
					border-radius: 10px; padding: 1rem 1.4rem; text-align: center; min-width: 90px;
				">
					<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--emerald)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="margin: 0 auto 0.4rem;">
						<polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
					</svg>
					<p style="font-size: 0.9rem; color: var(--emerald); font-weight: 600;">Skills</p>
				</div>

				<div style="
					background: var(--surface); border: 1px solid var(--border);
					border-radius: 10px; padding: 1rem 1.4rem; text-align: center; min-width: 90px;
				">
					<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--pink)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" style="margin: 0 auto 0.4rem;">
						<path d="M12 2v6m0 8v6"/>
						<path d="M6 12H2"/>
						<path d="M22 12h-4"/>
						<circle cx="12" cy="12" r="4"/>
					</svg>
					<p style="font-size: 0.9rem; color: var(--pink); font-weight: 600;">MCP</p>
				</div>
			</div>
		</div>
	</Transition>

	<Transition>
		<p style="font-size: 0.95rem; color: var(--text-muted); font-style: italic;">
			Think of it as an extension — but for your AI, not your editor.
		</p>
	</Transition>
</div>
