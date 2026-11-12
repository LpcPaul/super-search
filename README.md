# Super Search

[简体中文](README.zh-CN.md)

A browser-based agent skill whose core value is **expanding search coverage and improving retrieval for free, without requiring paid accounts on other AI platforms**. It uses available free web-search modes across multiple services to find sources a single service may miss, then checks the originals.

Find useful papers, articles, courses, projects and original posts, with direct links and independent source checks. No paid search API or Deep Research subscription is required.

## What it does

1. Give the selected AI services the same research question and constraints.
2. Use the user's signed-in Chrome sessions, rather than model API keys.
3. Collect source links and each service's unique discoveries.
4. Deduplicate sources, open the important originals, and report what is actually supported.
5. Close every tab opened for the run's searches and source checks after completion, preserving pre-existing tabs and any pages the user asks to keep. Keep necessary login or unfinished-task tabs until the run resumes and finishes.

AI-written explanations and agreement between models are not substitutes for source evidence.

## Platforms and caller routing

The default pool contains **ChatGPT, Claude, Grok, Gemini, Doubao, DeepSeek, Perplexity and Kimi**.

| Calling agent | Default external targets |
| --- | --- |
| Codex / ChatGPT | All except ChatGPT |
| Claude / Claude Code / Claude Desktop / Cowork | All except Claude |
| Gemini, Grok, Doubao, DeepSeek, Perplexity or Kimi | All except the caller's corresponding service |
| Another agent or unknown identity | All eight, with the uncertainty disclosed |

An explicit user platform list overrides automatic exclusion. Grouping Codex with ChatGPT is a routing convention, not a claim that they have identical search capabilities. Grok additionally searches public X/Twitter posts while retaining ordinary web search.

## Requirements

- An agent that can load `SKILL.md` and operate browser pages.
- A connected browser-control tool that can access the user's Chrome session.
- Accounts or guest access for the selected services, subject to their current availability and limits.

This repository contains **workflow instructions**, not a browser driver, extension or executable search engine. Reading the skill in a plain chat does not grant browser control. The host supplies that capability: for example, Codex Chrome browser tools or Claude in Chrome. Other hosts need an equivalent supported connection.

The default workflow uses available **free search modes**. Free accounts or guest access are enough where a provider offers them; a paid account on any target platform is not a prerequisite. Free does not mean login-free or unlimited: if a free mode is unavailable or its quota is exhausted, report the gap and continue with other channels instead of requiring an upgrade.

No model API key is required by this skill. Deep Research is optional and used only when explicitly requested and already available. The skill does not purchase subscriptions or silently switch to paid APIs. Your chosen host agent and browser tools may have their own costs; the free-search claim concerns the external search channels.

## Install

Copy this repository's skill folder into your agent's supported skill location, keeping `SKILL.md` at the folder root. Typical personal locations:

| Host | Skill folder |
| --- | --- |
| Codex | `~/.codex/skills/super-search/` |
| Claude Code | `~/.claude/skills/super-search/` |
| Other agents | Their documented Agent Skills directory |

`agents/openai.yaml` provides optional Codex display metadata. The operational instructions are in `SKILL.md`; they do not rely on a private local skill or an absolute machine path.

## Use

```text
Use $super-search to find practical methods for explaining principles visually.
Return original resources and direct links; do not replace them with your own essay.
```

Natural-language requests work when the host supports implicit skill selection:

```text
The search results missed the point. Run Super Search and look for original sources.
```

You may restrict platforms, request a language or exclude already-known resources. The skill reports unavailable platforms, login requirements and unconfirmed search activity rather than counting them as successful searches.

## Output

Expect a short source shortlist with relevance, unique discoveries, verification limits and actual platform coverage. The default output stays in chat. Files and reports are created only when requested or required by an existing project agreement.

## Privacy and limitations

- Prompts are sent to selected third-party services and may remain in their account histories. Temporary tabs are not a no-retention guarantee.
- Only the minimum necessary task context is sent. Credentials, cookies, unrelated private history and whole private knowledge bases are excluded.
- Login, MFA and verification challenges are handed to the user.
- Browser UI changes, region restrictions and account limits can interrupt a run. This repository does not guarantee live compatibility with every service or agent.
- A visible citation is still a candidate source, not proof. Core findings need checks against the original material.

## Contributing

For a platform change, describe the observed UI, host/browser, failure and recovery steps. Remove account identifiers, private prompts, chat history and credentials from issues and screenshots. Keep provider additions separate from claims about search quality.

## License

[MIT](LICENSE). Provider names are used for identification; this project is not affiliated with the listed services.
