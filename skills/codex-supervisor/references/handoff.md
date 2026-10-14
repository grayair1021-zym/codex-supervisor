# Discovery, ownership and recovery

Read when initializing coordination, taking over, recovering an interrupted dispatch or resolving ownership ambiguity. This cooperative protocol is not a system lock, authorization grant, process supervisor or reliable background service.

## One discoverable record

Start with the named project's formal entry, then its `Codex Supervisor` section or one direct link. Resolve its Codex project and section against native metadata. A project tracker, Codex project, sidebar section and working directory are different objects. Obtain your real thread identity from trusted runtime context, not the latest active item. Match actual IDs, not titles. A new supervisor joins the recorded project/section; do not move every worker into its accidental default section.

Keep the sole coordination record in the existing target-project tracker. Store only:

- Overall goal and completion conditions; authorized scope/limits and references to actual human messages (thread/turn), including relevant withdrawals. A prior agent saying “authorized” is insufficient.
- Intended projectId/sectionId and separately observed API membership or UI/user-confirmed fallback; owner threadId/hostId; ownership_epoch; handoff state, from/to and pending ACKs when transferring. Never label intended IDs as confirmed when API readback is missing.
- Stable task numbers, goals/dependencies, original worker threadId/hostId or unresolved creation intent, contracts/artifact locations, acceptance evidence, blockers and next actions. Associate repair counts with root causes.

Use PENDING, RUNNING, BLOCKED, REVIEW, ACCEPTED, PAUSED as coordination judgments, never substitutes for live runtime state. PENDING includes workers awaiting execution prerequisites; unconfirmed sidebar placement alone does not block execution. REVIEW requires delivery; ACCEPTED requires supervisor evidence; PAUSED requires confirmed safe stopping. Keep separate release/deploy/merge facts if relevant to the goal.

Update at dispatch, real blockers, authorization changes, acceptance, ownership changes and stopping. The current owner writes the record; workers report through their threads. Re-read before a narrow change and after writing. Do not overwrite concurrent changes or duplicate the ledger. Native history owns messages; runtime caches and full logs stay outside formal records.

## Discover before dispatch

Use recorded real IDs to read native history and actual artifacts. Native recent-thread lists are bounded, not exhaustive. An absent item, idle state or archived window does not mean nonexistent, stopped or ownerless. Resolve archived IDs with native history/archive discovery; unarchive only as needed within authority. Do not ask the user to supply IDs that these sources can recover.

Before creating, persist a stable task number, precise goal, scope, authorization and PENDING intent. Include the task number in the new thread's initial contract. After success bind the real ID. For uncertain creation or interrupted binding, inspect matching native history, project and creation outcome; do not create again unless absence is actually established. A clientThreadId is not a real threadId. Ambiguous outcomes remain blocked for reconciliation, without blind retry.

For writable work, the initial creation prompt or first instruction to a reused worker must require read-only preparation: read the contract and human authority, ACK the owner/epoch, exact allowed write scope and relevant isolation, then stop without modifying files. An ACK is not permission to proceed. After independently checking identity, authority, scope and the ACK, the supervisor records and sends a separate, uniquely identified GO. The worker rechecks current owner/epoch and prior handling before writing within that scope. Do not send an immediate implementation prompt and rely on later placement or messages to prevent early writes.

Placement uses automatic move, readback and at most one justified retry. A retry needs evidence such as a transient error or corrected target, not merely another null response. Carry the attempt count across contexts; do not reset it by changing task numbers. Never repeat creation to repair organization.

If native readback remains null/inconsistent, record intended membership, attempted moves and "native API unconfirmed". Continue work whose execution prerequisites are verified; do not raise placement alone as a blocker or ask for mid-task confirmation. Mention the unresolved placement briefly in the supervisor's report so the user can adjust it manually if needed. A later explicit UI confirmation is separate evidence, not native ID equality. Report any actual manual coordination honestly; do not invent either successful placement or a human action.

Creation and placement are separate operations. Real thread identity, human authorization, isolation/write scope and worker scope ACK must be checked before GO. UI organization is not a security boundary or a substitute for those checks; uncertainty about execution authority or scope still holds the affected writes.

## Window names

The convention below is the author's personal naming habit, not a Codex requirement. Use it as a default only when the user or project has no different convention; preserve explicit user choices. The leading star marks the current supervisor under this convention.

Use `N.M.D [A0] Shared theme` for the originating supervisor and `N.M.D [A1] Shared theme·Specific task` for its children. N is the project's window sequence; M.D is the actual creation month/day in the user's timezone, not the rename date. The family letter is shared; member 0 denotes the originating window, and children receive 1, 2, 3 in creation order. Member labels identify lineage, not model, current owner or task state. A successor keeps its label and existing family; its new children take the next family member number. After Z, continue AA, AB. Separate windows each retain their own project sequence and creation date.

Preserve existing sequence/date prefixes. Reserve unnumbered windows from the project's established numbering in the existing coordination record, using native titles and known bindings to check collisions; do not count a bounded recent list as all historical windows. Record the numbering baseline and uncertainty when historical coverage is incomplete. Prefer a stable user-approved project/topic phrase over changing system-generated titles. Keep specific task wording short. Record family, next reserved sequence/member and title-to-real-ID bindings in the existing record, not another database. An authorized historical retrofit need not rename unrelated windows.

Before authorized creation, reserve the intended title alongside task intent and pass it using the current schema. If creation normalizes or omits the title, use set_thread_title after binding the real ID, then read back. For existing windows, rename by verified ID without waking them. Reuse bindings on retries or recovery; do not renumber on archive, handoff or completion, recycle numbers, or rename an entire family merely because the owner changed. User changes take precedence. If a collision is discovered, reconcile only conflicting reservations; never silently renumber unrelated history.

Shared theme and labels help find unplaced windows, but title matches are only candidates: confirm real ID, history and authority before acting. A successful rename neither verifies project/section placement nor authorizes work. Store an unconfirmed rename honestly; do not create a replacement window to fix a name. These instructions apply when this Skill is used; no global naming enforcement or background renamer is implied.

Use one leading `⭐️ ` before the title's number to mark the current supervisor in this project's coordination record. At an authorized handoff, after ownership commits and before new dispatch, update the successor's title using these naming rules, remove the marker from the recorded former supervisor if present, and add it to the successor; read back both real IDs. Preserve existing names apart from required naming and marker changes. Keep the marker on the final supervisor when the project completes so the user can find its last point of contact. Do not move it merely because another window is active; the marker neither grants ownership nor proves completion.

## Transfer with acknowledgments

ownership_epoch is a revision counter, **not an atomic lock or lease**. Idle, timeout, archive, a larger epoch or last writer wins cannot establish ownership. Only one supervisor issues new instructions.

1. Discover the unique record, read the actual old owner's history, verify current human authorization and all relevant worker states and evidence. Recover authority from actual human messages; receiving an agent message alone does not authorize replying. Missing authority affects only dependent work, never grants broader permissions.
2. Establish the old owner's explicit release or actual human replacement instruction. If reachable, request release before transfer. If neither exists, freeze conflicting dispatch and reconcile facts; escalate only a genuine unresolved ownership choice. A vanished window is not a release.
3. Prepare transfer with from/to, proposed epoch and pending workers. Both supervisors refrain from new conflicting dispatch. Ask unfinished workers to reach a safe boundary and ACK the intended owner, epoch and completed/remaining work. Do not wake completed inactive workers just for ACKs. A running command may not be interruptible.
4. After establishing either old-owner release or the explicit human replacement instruction from step 2, and obtaining required boundary ACKs, re-read unchanged state, commit owner/new epoch, and read back. Human replacement does not prove conflicting execution has stopped; resolve that before committing. Apply the [window-name and supervisor-marker rules](#window-names). Notify relevant workers of effective ownership; collect their ACKs after they verify the record and authority. Only then release remaining work. Keep original task IDs, artifacts and scope.
5. Before each dispatch/change instruction, acceptance write or resumed execution, verify ownership. Messages carry task number, epoch and a distinct instruction/question ID. Workers check prior handling before executing duplicates, reject stale-owner instructions and route questions to the verified current owner. Record delayed or rejected instructions when they affect decisions.

A previously authorized successor can finish a prepared transfer using either authority from step 2; it must still verify workers and current authority. Do not infer human consent from elapsed time. Two successors may race on Markdown/iCloud; re-reading reduces risk but cannot make updates atomic. Conflicting owners, equal epochs with different owners or evidence of simultaneous commands require a safe freeze of affected dispatch/writes. Independent read-only inspection may continue. Never claim universal mutual exclusion.

## Interrupted recovery and completion

Prepared but uncommitted: retain original owner, intended successor and pending ACKs; resolve history before committing or rolling back. Committed but ACKs missing: resend only necessary effective notices and verify them, without recreating workers. Changed artifacts invalidate only relevant acceptance evidence. Corrupt or conflicting records require reconciliation, not optimistic overwrites.

A worker reports a genuine blocker with task/epoch/question ID, facts, attempts and a recommendation. Sending successfully is not proof of processing. If the owner is inactive, retain the report in native history for later readback; do not promise autonomous resurrection or continuous unattended supervision. Authorized native wakeups may be evaluated separately, never silently installed.

Before closure verify every released worker's actual completion or safe stop, inspect the full project's outcome and preserve evidence/real IDs. Distinguish no new dispatch, stop requested and stop confirmed. Uncertain active work remains explicitly unresolved. Retain completed threads according to the existing policy; no automatic deletion or archive-as-stop.
