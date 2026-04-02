<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script lang="ts">
	import { Transition, Code, Action } from '$lib/index.js'

	let code: ReturnType<typeof Code>
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.8rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			What it should <span style="color: #ef4444;">ignore</span>
		</p>
	</Transition>

	<div style="display: flex; gap: 2.5rem; align-items: flex-start;">
		<div style="display: flex; flex-direction: column; gap: 1rem; width: 420px;">
			<Transition>
				<Code
					bind:this={code}
					lang="bash"
					theme="poimandres"
					code={`# .cursorignore

node_modules/
dist/
.env*`}
					options={{ duration: 600, stagger: 0.3, containerStyle: false }}
				/>
			</Transition>
		</div>

		<div style="display: flex; flex-direction: column; gap: 0.8rem; max-width: 340px;">
			<Transition>
				<div style="display: flex; flex-direction: column; gap: 0.6rem;">
					<p style="font-size: 1.1rem; font-weight: 600; color: var(--text);">Why bother?</p>
					<div style="display: flex; flex-direction: column; gap: 0.5rem; font-size: 0.95rem; color: var(--text-muted);">
						<p>Faster indexing</p>
						<p>Less noise in AI context</p>
						<p>Keeps secrets out of prompts</p>
					</div>
				</div>
			</Transition>
		</div>
	</div>

	<Action
		actions={[
			async () => {
				await code.update`# .cursorignore

node_modules/
dist/
.env*
*.lock
coverage/
**/*.generated.*
vendor/

# works like .gitignore
# drop it in root — done`
			},
		]}
	/>

	<Transition>
		<p style="font-size: 1rem; color: var(--text-muted);">
			Same syntax as <code style="color: var(--emerald); background: var(--surface); padding: 4px 10px; border-radius: 6px;">.gitignore</code> — if you know one, you know both.
		</p>
	</Transition>
</div>
