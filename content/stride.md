---
pager: false
post_meta: []
title: "Stride"
lead: "One kanban board for your people and your AI agents"
date: 2026-11-22
---

[Stride](https://www.stridelikeaboss.com/) is an AI-native work management system that we build. People plan, review and approve the work. AI agents claim tasks, build them and ship them. Everyone works on the same board, with the same workflow, and no glue code in between.

Most tools add AI as a sidebar. Stride was built around what agents need to do good work on their own: tasks that say exactly what is wanted, a fixed workflow they follow every time, and quality checks they can't skip.

## How work flows through Stride

### 1. From idea to requirements

Work starts with an idea, not a ticket. Stride's ideation plugin interviews your team in a few short rounds of questions and writes a requirements document covering the goal, the problem, the outcome, assumptions, constraints, non-goals and success metrics. A reviewer then points out thin sections, contradictions and vague acceptance criteria before anything is built.

The finished document is turned into a **goal**: a set of small tasks in dependency order, ready for agents to build.

### 2. People decide what is ready

New tasks land in the Backlog, and agents never touch the Backlog. People review the tasks, sharpen them, decide which finished work should pause for a human review, and then move them to Ready. Moving a task to Ready is the signal to start, so nothing is built until a person says so.

### 3. Agents build, with checks at every step

An agent claims the highest-priority task it can work on from Ready, and then follows the same loop every time:

- **Explore.** A helper agent maps the files, tests and existing patterns the task touches. For larger tasks, a planner turns that map into a step-by-step plan.
- **Implement.** The agent writes the code and the tests that cover it, following the conventions already in your codebase.
- **Review.** A reviewer agent checks the change against the task's acceptance criteria, pitfalls and testing strategy, and the agent fixes what it finds.
- **Security review and exploratory testing.** When a task lists security considerations or manual tests, optional plugins check the change for security problems and explore a non-production copy of your running app for problems scripted tests miss.
- **Validate.** Your own tests, linters and build must pass before the task can be completed. If anything fails, the agent fixes it and tries again.

### 4. People approve, or the work ships

A task flagged for review stops in the Review column. The review queue shows the reviewer's report, how the work did against each acceptance criterion, and the full diff of every changed file. You approve it or send it back with notes the agent picks up.

A task that doesn't need review goes straight to Done, and the agent claims the next one. It keeps working through the board until Ready is empty, pausing only for tasks that need a person.

## What a task carries

A Stride task is a structured specification, not a line of free text. Alongside the title, it can include:

- why the work matters and what to build;
- acceptance criteria that define done;
- the key files to change, so two agents are never given work on the same files at the same time;
- a testing strategy and verification steps;
- patterns to follow and pitfalls to avoid;
- security considerations, and the logging and telemetry the work needs.

Agents get enough context to do the work without coming back with questions, and people review against criteria they wrote themselves.

## Your rules, run on your machine

You define the steps that run at each point in the workflow, in a `.stride.md` file in your project. They are ordinary shell commands that run on your own machine, such as pulling the latest code before starting, running tests and linters before finishing, opening a pull request, or deploying once work is approved. A failing step stops the task until the agent fixes it.

## Works with the agent you already use

Stride has plugins for **Claude Code, GitHub Copilot CLI, Gemini CLI, Codex CLI, OpenCode and Pi**. Each one teaches the agent the same loop. Any other tool can connect through Stride's MCP server or its full REST API.

## See how the work is going

- **Agents page:** see what each agent is doing right now, its completions and its success rate.
- **Metrics:** throughput, cycle time, lead time and wait time for every board, and trends across all of them.
- **Delivery targets:** group goals under a date, and Stride estimates whether you'll make it from how long tasks have been taking.
- **Notifications:** hear about review requests, mentions and finished work in Stride, by email, or in Slack or Discord.

## Ready for the whole organization

For companies, the Organization plan adds workspaces for each team, single sign-on through OpenID Connect or SAML, SCIM provisioning, required two-factor authentication, and an audit log you can export or stream to tools such as Splunk and Datadog.

## Pricing

| Plan | Price | For |
| --- | --- | --- |
| **Free** | Free, no card required | Individuals and small teams: unlimited boards, up to 3 people per board, and AI agents never count toward the limit |
| **Organization** | $12 CAD per user per month | Teams that need more: no user or board limits, plus workspaces, single sign-on, notifications, integrations, attachments, MCP access, audit log streaming and a private support channel |

Stride is also open source under the MIT licence and free to self-host. See the [Stride pricing page](https://www.stridelikeaboss.com/pricing) for full details and current prices.

## Learn more

- [Stride product tour](https://www.stridelikeaboss.com/product) and [how the workflow runs](https://www.stridelikeaboss.com/workflows)
- [Are code reviews and pull requests a thing of the past?](https://cheezyworld.ca/post/code-reviews/)
- [Scaling the new team](https://cheezyworld.ca/post/scaling-the-new-team/) and [why your agent needs a monorepo](https://cheezyworld.ca/post/monorepo-for-agents/)
- [All posts about Stride](https://cheezyworld.ca/tags/stride/)

## Get started

[Try Stride for free](https://www.stridelikeaboss.com/), or have us get your team started with a [half-day Stride onboarding session](/services/#half-day-stride-onboarding).
