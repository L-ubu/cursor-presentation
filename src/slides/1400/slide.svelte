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
			A rule is just a <span style="color: var(--purple);">markdown</span> file
		</p>
	</Transition>

	<div style="width: 100%; max-width: 750px;">
		<Transition>
			<Code
				bind:this={code}
				lang="markdown"
				theme="poimandres"
				code={`---
description: "React component rules"
globs: ["src/components/**/*.tsx"]
---`}
				options={{ duration: 800, stagger: 0.3, containerStyle: false }}
			/>
		</Transition>
	</div>

	<Action
		actions={[
			async () => {
				await code.update`---
description: "React component rules"
globs: ["src/components/**/*.tsx"]
alwaysApply: false
---

# Component Rules

- Use functional components with hooks
- Props interface: \{ComponentName\}Props
- Always memoize callbacks with useCallback
- Export named, never default`
			},
			async () => {
				await code.selectLines`3`
			},
			async () => {
				await code.selectLines`4`
			},
			async () => {
				await code.selectLines`*`
			},
		]}
	/>

	<Transition>
		<div style="display: flex; gap: 2rem; font-size: 0.95rem; color: var(--text-muted); text-align: center;">
			<div style="display: flex; flex-direction: column; gap: 0.25rem; align-items: center;">
				<code style="color: var(--purple); background: var(--surface); padding: 4px 10px; border-radius: 6px;">alwaysApply: true</code>
				<span>every chat, always active</span>
			</div>
			<div style="display: flex; flex-direction: column; gap: 0.25rem; align-items: center;">
				<code style="color: var(--blue); background: var(--surface); padding: 4px 10px; border-radius: 6px;">globs: ["**/*.tsx"]</code>
				<span>only when matching files open</span>
			</div>
			<div style="display: flex; flex-direction: column; gap: 0.25rem; align-items: center;">
				<code style="color: var(--emerald); background: var(--surface); padding: 4px 10px; border-radius: 6px;">neither</code>
				<span>agent decides when to use it</span>
			</div>
		</div>
	</Transition>
</div>
