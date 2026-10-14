---
name: codex-supervisor
description: Coordinate authorized independent Codex tasks, supervise their delivery, or take over unfinished project work. Skip ordinary single-task edits, status questions, and reminders.
---

# Codex supervisor

Own coordination and acceptance; spare the user window lookup, message forwarding, routine repairs and task bookkeeping. Follow the project's engineering and verification practices; use engineering-workflow if installed. Current user instructions and applicable permissions govern every action. If required native task tools are unavailable, report the affected limitation without pretending to coordinate independent chats.

Optimize for the coordination cost, rework and human attention needed to complete the task, rather than the number of agents running at once.

Handle simple work directly. For parallel work finishable within the current task, prefer in-task subagents when available and authorized. Use this independent-thread workflow only when separate user-facing windows, cross-session continuation or supervisory handoff is needed; otherwise skip it. Parallelism alone does not justify new chats.

## PLAN

Read the target project's formal entry and existing coordination record. Before initializing that record or resuming ownership, read [handoff](references/handoff.md). Define the overall observable outcome, dependencies and independent tasks. Use a short contract: goal/context; allowed scope and exclusions; prerequisites; deliverable and necessary checks; blocker/exit conditions and current owner. Workers do not delegate by default.

## DISPATCH

Recheck ownership, authorization, existing task bindings and live tool schemas. Independent thread creation requires explicit user authorization. Prefer Astra High supervising Sol Medium only when supported and authorized; distinguish requested models from verified runtime metadata.

Persist a stable task number, goal, scope/authority and PENDING dispatch intent **before** creation. Reuse an existing worker when appropriate. Bind the returned real threadId and hostId; an uncertain response requires discovery before any retry, never blind recreation.

For new or reused writable workers, put the [preparation/GO contract](references/handoff.md#discover-before-dispatch) in the first instruction; thread creation can start execution immediately.

Give related windows consistent, searchable titles using the project's numbering/date convention and a stable family/member label. Reserve labels with dispatch intent; use the native title tool and read back. Follow the [naming rules](references/handoff.md#window-names); titles aid discovery, never establish identity or ownership.

Resolve the formal tracker-to-Codex-project mapping from authoritative context and native metadata, not cwd or similar names. Organize supervisor and workers in the same project and section using [handoff](references/handoff.md). Unconfirmed UI placement is report-only: continue otherwise authorized work and mention it briefly in the supervisor's report, without a mid-task confirmation request. Never claim unverified membership. Real task identity, human authority, isolation/write scope and worker ACK remain prerequisites for write release; organizational fallback does not waive them.

## SUPERVISE

Use native messages, bounded wait_threads with cursors, and targeted read_thread. Act on actionable changes; unchanged status needs no repeated announcement. Workers verify current owner/epoch before questions or resumed writes, retain blockers in their history and proactively contact the owner only with verified human communication authorization. If messaging fails, read their history; do not ask the user to relay it.

Resolve ordinary blockers and targeted repairs. Two repair rounds for one root cause trigger reassessment of contract, context, approach, capabilities and new evidence, not automatic escalation or an absolute retry ban. Without new evidence, stop repeating. Changing workers or task numbers never resets the cause's count.

Escalate only important product choices, new high-impact authorization, blockers the supervisor cannot resolve, or necessary human experience judgment. A tool failure alone is not a user decision.

## VERIFY

Inspect actual artifacts and scope; worker assertions are not acceptance. Match checks to risk using existing discipline. Reuse passed evidence while its artifact version and assumptions remain applicable. Send specific unmet criteria to the same worker for local repairs; take over judgment when the approach or contract is wrong. Do not add a reviewer for routine low-risk work.

Accept each task and separately check the overall goal, integration and remaining conditions. Record evidence and unresolved limits. Distinguish format, explicit instruction loading, real coordination, fresh-context recovery and installed discovery. Stop when sufficient; do not publish implicitly.

## RESUME / STOP

Follow [handoff](references/handoff.md) for automatic discovery, ownership transfer, ACKs and interrupted dispatch. Finding a thread does not establish supervisory ownership. Skill prose and epochs provide neither atomic locks nor guaranteed background wakeups.

On stop, cease new dispatch, request safe worker stops, then verify actual stopped state separately. Archive only after confirmed completion/stopping and authorized retention policy; archive is not stop. Preserve real IDs and acceptance evidence; clean only scoped temporary fixtures. Report uncertain live work honestly.
