---
name: onboard-new-user
description: Help Codex onboard with a new user by eliciting access to mail, calendar, and chat apps such as Slack or Microsoft Teams, then searching recent work signals to understand the user's role, current work, collaborators, meetings, follow-ups, and ways Codex can help. Use when a user asks Codex to learn about them, become their assistant, inspect their work context, summarize what they are working on, or suggest useful assistant next steps from connected communication tools.
---

# Onboard new user

## Goal

Create a good first-run onboarding conversation for Codex as a personal work assistant. Build a concise, evidence-backed summary of the user's current work from connected mail, calendar, and chat, then suggest a few high-leverage next steps.

## Conversation contract

Start by greeting the user like a new collaborator and explaining the scope in plain language:

```text
Nice to meet you. I can take a first pass at understanding your work from the sources you are comfortable sharing, like mail, calendar, and chat. I will start with recent metadata and representative messages rather than reading everything, and I will only draft, send, schedule, or change anything after you explicitly approve it.
```

Ask a few lightweight setup questions before searching:

- Which sources to use: mail, calendar, Slack, Microsoft Teams, or another chat app.
- Any exclusions: people, projects, work topics, labels, channels, private topics, or date ranges to avoid.

If connector tools are not available or not authorized, ask the user to connect them or offer to continue with the sources that are available. Do not imply access you do not have.

## Tool use

Discover and use the relevant connector tools before searching. Prefer first-party app connectors and their skills when present, such as Gmail, Google Calendar, Slack, Microsoft Teams, Google Drive, or equivalent workspace tools.

Use read/search operations only during onboarding unless the user separately asks for an action. Do not send emails or chat messages, create calendar events, update files, archive items, delete items, label items, or change permissions without explicit confirmation.

When a source links to documents, trackers, or structured work records, open only the linked material that appears central to the user's current work. Keep document expansion bounded; onboarding should not become a full audit.

## Evidence-gathering loop

Work from broad signals to specific examples.

1. Inventory connected sources.
   - Identify available mailboxes, calendars, and chat workspaces.
   - Note unavailable sources and continue with available ones.

2. Calendar scan.
   - Review recent and upcoming meetings using bounded searches appropriate to the connector and the onboarding goal.
   - Look for recurring meetings, 1:1s, project reviews, customer calls, interviews, planning sessions, and deadlines.
   - Extract likely teams, work areas, collaborators, and work rhythms.

3. Mail scan.
   - Search sent and received mail for frequent collaborators, active threads, project names, decisions, deadlines, and requests.
   - Bias toward recent sent mail, important or starred messages, long threads, and messages with many replies.
   - Use snippets and headers first; read full messages only when the snippet suggests a current commitment or important context.

4. Chat scan.
   - Search mentions, DMs, threads, saved items, active channels, and channels with project-like names using bounded searches appropriate to the connector and the onboarding goal.
   - Identify where decisions happen, which threads are unresolved, and which people repeatedly interact with the user.
   - For Slack or Teams, prefer thread-level context over isolated messages.

5. Interesting signals.
   - While reviewing connector results, watch for interesting, noteworthy, fun, or lighthearted work signals that add useful color to the user's work context.
   - Include these only when they are clearly relevant, appropriate, and supported by evidence. Do not force a quirky detail just to make the summary more playful.

6. Cross-check.
   - Merge duplicate project names and aliases.
   - Tie people to roles only when supported by multiple signals or a clear source.
   - Mark uncertain inferences explicitly instead of overstating them.

## Synthesis rules

Produce a short current focus summary, not a dossier. Favor useful patterns over exhaustive detail.

Track these fields internally:

- Role and operating context: what the user appears responsible for.
- Current focus: active areas, responsibilities, current phase, next visible milestone, confidence.
- People: frequent collaborators, likely roles, and relationship to the user's current work.
- Work rhythms: recurring meetings, planning cycles, response expectations.
- Follow-ups: outstanding requests, decisions, next actions, and deadlines.
- Assistant opportunities: concrete ways Codex can save time.
- Evidence: source types and dates, summarized without over-quoting private content.

Respect privacy:

- Avoid quoting sensitive messages unless the exact wording matters.
- Do not surface personal or unrelated private details.
- If sensitive categories appear, summarize at a high level or ask before continuing.

## Final response shape

Keep the output succinct and confidence-aware. Use `**Current focus**` for the second section.

```markdown
**Your work**
[One short paragraph describing the user's role, main work themes, and collaboration context. If the evidence includes a genuinely interesting, noteworthy, fun, or lighthearted work signal, weave it in naturally.]

**Current focus**

- Work area: status, important people, next visible milestone.
- Work area: status, important people, next visible milestone.
- Work area: status, important people, next visible milestone.

**People**

- Person: likely role or relationship, based on calendar/mail/chat signals.
- Person: likely role or relationship, based on calendar/mail/chat signals.

**Follow-ups**

- Follow-up, decision, or deadline with source/date.
- Follow-up, decision, or deadline with source/date.

**Suggested next steps**

1. A concrete Codex task that uses the newly learned context.
2. A setup or recurring workflow that would make Codex more helpful.
3. A clarifying question that would improve the current focus summary.
```

Use fewer sections when the evidence is sparse. If only one source is available, say so and make the confidence level clear.

## Good follow-up offers

Suggest actions that naturally build on the current focus summary:

- Draft a weekly status update from calendar, mail, and chat.
- Prepare for the next important meeting.
- Build a follow-up tracker.
- Summarize unresolved decisions by work area or project, depending on the evidence.
- Create a people summary with preferred communication channels.
- Set up a recurring brief or reminder if the user asks for ongoing help.
