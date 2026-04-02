<script module>
	import { defineProps } from '$lib/index.js'
	export const props = defineProps({})
</script>

<script lang="ts">
	import { Transition, Code, Action } from '$lib/index.js'

	let code: ReturnType<typeof Code>
</script>

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; gap: 1.5rem;">
	<Transition visible>
		<p style="font-size: 2.2rem; font-weight: 700; color: var(--text); letter-spacing: -0.02em;">
			Cursor CLI — AI in your terminal
		</p>
	</Transition>

	<div style="width: 100%; max-width: 750px;">
		<Transition>
			<Code
				bind:this={code}
				lang="bash"
				theme="poimandres"
				code={`# Interactive agent session
agent`}
				options={{ duration: 600, stagger: 0.3, containerStyle: false }}
			/>
		</Transition>
	</div>

	<Action
		actions={[
			async () => {
				await code.update`# One-shot prompt
agent chat "find and fix all TODO comments"

# Ask without changing anything
agent --mode=ask "explain the deployment pipeline"

# YOLO mode — auto-approve everything
agent --force "fix all lint errors"`
			},
			async () => {
				await code.selectLines`2`
			},
			async () => {
				await code.selectLines`5`
			},
			async () => {
				await code.selectLines`8`
			},
			async () => {
				await code.selectLines`*`
			},
		]}
	/>

	<Transition>
		<p style="font-size: 1.1rem; color: var(--text-muted);">
			Don't even need to open the IDE. Works in CI/CD too.
		</p>
	</Transition>
</div>
