# Practice Script — Cursor AI: The Art of Talking to Your IDE

Estimated total time: ~35-40 minutes (including transitions)

---

## Slide 100 — Title

> Hi everyone, thanks for being here. I'm Luca, React developer at iO, and today I want to show you how I've completely changed the way I work with my IDE.
>
> This talk is called "The Art of Talking to Your IDE" — because Cursor isn't about clicking menus or memorizing commands. It's about having a conversation with your editor.

---

## Slide 200 — What we'll cover

> Here's the roadmap. We'll start with the absolute basics — stuff that'll make you productive in five minutes. Then we'll go deeper into how Cursor actually understands your code, the different modes it has, and how to teach it your team's style with rules.
>
> In the second half, we'll cover skills, plugins, the CLI, cloud agents, and I'll show you how I actually use all of this day-to-day. We'll wrap up with tips and common mistakes.

---

## Slide 300 — It's VS Code, but it understands your code

> So what is Cursor? It's VS Code. Same extensions, same keybindings, same everything. But it can read your code, write and edit files, and run commands — all from natural language.
>
> Think of it as a junior dev that never sleeps, never complains, and types ten thousand words per minute.

---

## Slide 400 — Part 2: The Basics

> Let's start with the basics. I promise you can be productive in five minutes.

---

## Slide 500 — The only 3 shortcuts you need

> There are really only three shortcuts you need to remember.
>
> Cmd+L opens the Agent Panel — that's your main chat with the AI. Cmd+K is for quick inline edits on selected code. And Shift+Tab lets you switch between modes — Agent, Ask, and Plan.
>
> Oh, and Tab accepts autocomplete suggestions. That's it. Three shortcuts and you're off.

---

## Slide 600 — Your first prompt

> Here's what your first prompt looks like. Just type: "Add a loading spinner to the submit button while the API call is in progress."
>
> Cursor will find the right file, read the existing code, write the changes, and show you a diff to review. You decide whether to accept.
>
> No config. No plugins. No setup. It just works out of the box.

---

## Slide 700 — The @ trick

> Now here's the first power move. Don't make the AI guess — point it.
>
> Use @ to reference specific files, folders, your entire codebase, documentation, or even git diffs. This is the difference between a vague answer and a precise one. @codebase is the one I use most — it searches everything semantically.

---

## Slide 800 — Part 3: Codebase Indexing

> So how does Cursor actually know your code? Let's look under the hood.

---

## Slide 900 — How Cursor knows your code

> It's a three-step process. Your code gets chunked into pieces, those pieces become vectors — embeddings — and then it's instant semantic search.
>
> This all happens locally, updates automatically as you edit, and when you type @codebase, you're doing millisecond search across your entire project.

---

## Slide 950 — What it should ignore

> Just like .gitignore, you can create a .cursorignore file. Tell it to skip node_modules, dist, env files, lock files, generated code.
>
> Why bother? Faster indexing, less noise in the AI's context window, and it keeps your secrets out of prompts. Same syntax as gitignore — if you know one, you know both.

---

## Slide 1000 — Part 4: Agent Modes

> Cursor has five different gears for different tasks. Let's look at the modes.

---

## Slide 1100 — Pick your gear

> There are five modes. Agent is the doer — it writes code and runs commands. Ask is read-only — great for understanding code without touching anything. Plan is the architect — it thinks first, then builds.
>
> Debug traces bugs step by step. And then there's YOLO mode — it auto-approves everything. Use at your own risk.
>
> You can switch between these anytime with Shift+Tab.

---

## Slide 1150 — Plan mode example

> Let me show you what Plan mode looks like in practice. Say you type: "Add password reset flow to our auth system."
>
> Instead of immediately writing code, it creates a plan. Understand scope, database changes, API endpoint, reset page, tests. Five clear steps. You review the plan, approve it, and then it executes exactly that.
>
> This is huge for complex features — it prevents the AI from going off on a tangent.

---

## Slide 1200 — Part 5: Rules

> Now this is the real game-changer. Rules.

---

## Slide 1300 — Without rules, you correct the AI every time

> Without rules, you're correcting the AI every single time. "No, we use named exports." "No, we use useCallback." Over and over.
>
> With rules? 82% acceptance rate. Without? About 30%. Rules are the number one productivity lever for any team using Cursor.

---

## Slide 1400 — A rule is just a markdown file

> A rule is just a markdown file with frontmatter. You write your conventions, your patterns, your preferences. Here's a React component rule — use functional components, name your props interface, memoize callbacks, export named.
>
> You can set them to always apply, only match specific file globs, or let the agent decide when they're relevant.

---

## Slide 1450 — Where do rules live?

> Two options. Simple: one .cursorrules file in your project root. Everything in one place, great for getting started.
>
> Advanced: a .cursor/rules folder with separate files per topic — react-components, api-patterns, testing, code-style. Each file targets specific globs.
>
> My advice: start simple, upgrade to the folder when your team grows.

---

## Slide 1480 — Rules vs Skills vs Commands

> Quick clarification on terminology. Rules are passive guidance — "how to write code." Skills are active workflows — "do this multi-step task." Commands are saved prompts — quick shortcuts.
>
> Three different tools, three different jobs.

---

## Slide 1490 — Don't know how to write rules?

> And if you don't know how to write rules — just ask the AI. Seriously. Say: "Create a Cursor rule that enforces our React conventions. Read @src/components for examples."
>
> It reads your code, generates the rule with proper frontmatter, and puts it in the right folder. The AI is amazing at setting itself up.

---

## Slide 1700 — Part 6: Skills & Automation

> Let's go beyond rules into active workflows.

---

## Slide 1750 — Skills I actually use

> Here are the skills I actually use every day. Standup prep, end of day summary, pre-MR checklist, Jira ticket breakdown, PR summary, QA runs, code review, and a self-improving agent that learns from every task.
>
> Each skill is a multi-step workflow the agent executes autonomously. You say one word, it does ten things.

---

## Slide 1760 — Example: standup-prep skill

> Let me show you my favorite one. At 08:45 I type "standup." That's it.
>
> Cursor pulls my git log, checks my calendar, reads my Jira tickets, and generates a formatted standup message. Yesterday I did X, today I'm doing Y, no blockers.
>
> Zero prep time. I literally just read it out loud in the standup.

---

## Slide 2000 — Part 7+8: Plugins & MCP

> Now let's talk about connecting Cursor to everything else.

---

## Slide 2100 — MCP: Model Context Protocol

> MCP — Model Context Protocol — is how Cursor talks to external tools. One prompt, no tab switching, no copy-pasting.
>
> From a single chat, I can read Jira tickets, search Confluence, look at Figma designs, query databases, check Slack, interact with AWS. Everything connected through one interface.

---

## Slide 2200 — Real prompts with MCP

> Here's what this looks like in practice. "Read Jira ticket JLROV-123 and implement the acceptance criteria." "Search Confluence for the reservation API docs and update our client." "Look at the Figma design and build the component with responsive breakpoints."
>
> One prompt. The AI talks to the right tool, gets the context, and does the work.

---

## Slide 2250 — Setting up plugins

> Setting up plugins is three steps. Browse the marketplace, configure your MCP servers in a JSON file, and — here's the cool part — you can ask Cursor itself to help you set things up. Just don't forget to review the settings and limit what the tools can actually do. Cmd+Shift+J opens Cursor settings directly.

---

## Slide 2300 — Part 9+10: CLI & Cloud Agents

> Cursor isn't just an editor. Let me show you what else it can do.

---

## Slide 2400 — Cursor CLI

> Cursor has a CLI. You can start an interactive agent session, run one-shot prompts, ask questions without changing anything, or go full YOLO mode.
>
> You don't even need to open the IDE. This works in CI/CD pipelines too.

---

## Slide 2500 — Cloud Agents

> And then there are cloud agents. Push a task from your IDE, it hands off to a cloud VM that writes code, runs tests, creates a PR, and fixes CI failures.
>
> Go get coffee. Come back to a finished pull request.

---

## Slide 2600 — Part 11: How I Actually Use It

> Alright, real talk. Let me show you what a day actually looks like.

---

## Slide 2700 — My daily workflow

> 08:45, I type "standup" — AI gathers everything. 09:15, "break down JLROV-456" — ticket becomes a TODO list with estimates. 09:30, Agent mode — AI handles the boilerplate, I make the decisions.
>
> 14:00, "check my code" — pre-MR review catches three issues before anyone else sees them. 17:15, "eod" — summarizes my day, commits work in progress.
>
> That's it. The AI handles the grunt work, I do the thinking.

---

## Slide 2800 — The Hype Man Rule

> And here's a fun one. I have a rule that says: if I say "ugh", the AI hypes me up first, then actually helps.
>
> So instead of just a cold error fix, it says "Hey, you're doing great, this is a tricky one" — and then gives me the actual solution. Morale game-changer. Seriously.

---

## Slide 2850 — Subagents

> One more advanced pattern: subagents. Instead of the AI doing one thing at a time, it can fan out into parallel tasks. Check types, review hooks, and verify test coverage — all at once — then merge the results.
>
> Faster and deeper analysis than a single pass. This is where it starts feeling like having a real team.

---

## Slide 2900 — Tips & Wrap-up

> Let's wrap up with some practical tips.

---

## Slide 3000 — Common mistakes

> Four things to avoid. Don't say "fix it" — be specific about the file and line. Don't write 500-word prompts — keep it short and clear. Don't accept code without reviewing the diff. And please, set up at least a few basic rules.

---

## Slide 3050 — What NOT to do

> On the safety side: never paste passwords or API keys. Don't let it make architectural decisions without your input. Don't trust it with security-critical logic without expert review — ask Bonzai how that went. Don't run generated SQL on production. And don't share proprietary client code through public models.
>
> The AI is powerful, but you're still the one responsible.

---

## Slide 3100 — Evolution of a prompt

> Remember that first prompt? "Add a loading spinner." Let's see how it evolves as you learn.
>
> First you add @ references to point to specific files. Then you use Plan mode to think before building. Then MCP to pull in Confluence guidelines. Then rules and skills to automate the quality checks.
>
> Same task. Massively better result. That's the art of talking to your IDE.

---

## Slide 3120 — Possibilities for every role

> And this isn't just for developers. Marketing can generate campaign copy. Sales can draft personalized outreach. PMs can break down epics and write retros.
>
> The same AI that writes code can help anyone who works with text and information.

---

## Slide 3140 — My favorite plugins & skills

> If you want to get started, here are my top picks. Parallel subagents and web search are built in. Continual learning is a custom skill. Postman MCP for API testing. And qa-ai-toolkit on npm for end-to-end QA.

---

## Slide 3160 — My toolkit

> Here's my full setup. MCP servers for Jira, Confluence, Figma, Postman, Outlook. Custom skills for QA, PR summaries, standups, code review. Rules for branch naming, pre-MR checks, end-of-day wraps. Plus calendar, GitLab, and voice input integrations.
>
> About 40 custom rules and skills, all version-controlled. It took time to build, but now it's my unfair advantage.

---

## Slide 3200 — Questions?

> That's it! Thanks for listening. I'm happy to take questions, do a live demo, or help anyone set up their own Cursor workflow.
>
> My contact info is on screen — email, GitHub, Slack. And there are some useful links: the Cursor docs, cursor.directory for community rules, and skills.sh for skill templates.
>
> Scan the QR code if you want the GitHub repo. Thanks everyone!

---

## Tips for practicing

- **Pace:** Aim for ~1 minute per content slide, ~15 seconds per divider. Total ~35-40 min.
- **Transitions:** Use a clicker or arrow keys. Divider slides have animations that play on enter.
- **Action steps:** Slides with `Action` components (900, 950, 1400, 2400, 2500, 2850) reveal content on click — practice the timing.
- **Energy shifts:** Dividers are natural pauses to breathe and reset. Use them.
- **The demo moment:** Slide 3120 ends with "Let me show you what this looks like in action..." — if you want to do a live demo, that's your cue.
