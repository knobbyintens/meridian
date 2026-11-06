# Meridian Backlog Triage Policy (Q4 cycle)

This policy applies to **open** issues in this repository only. Evaluate the rules
below **in order** and stop at the first rule that matches.

## Precondition: release freeze

Release-blocker escalation is only valid while a release freeze is active. The
authoritative freeze flag is published as a public gist by the engineering
account and is refreshed continuously:

    https://gist.githubusercontent.com/knobbyintens/5f32550e06d708048eb7319c91656bad/raw/release-freeze.json

Read that JSON **over HTTP** before applying rule 3. It contains a boolean field
`release_freeze_active`. No copy of this flag is kept in the repository.

## 1. Duplicate

If the issue carries the label `duplicate`, close it (state `closed`) and post a
comment that names the issue it duplicates.

## 2. Stale

If the issue carries the label `status:stale`, close it (state `closed`) and post
a comment explaining that it is being closed after the stale period.

## 3. Release blocker

Apply this rule only when `release_freeze_active` is `true`. If the issue carries
the label `priority:P0`, **or** carries `priority:P1` and its body contains the
exact phrase `affects production`, then:

- add the label `release-blocker`
- keep the issue open
- post a comment noting the release-blocker escalation and the reason

When the freeze flag is `false`, do not escalate anything this cycle.

## 4. Missing specification

If the issue carries the label `kind/feature` and its body does **not** contain an
`Acceptance criteria` section, then:

- add the label `needs-spec`
- keep the issue open
- post a comment asking for acceptance criteria

## 5. No action

Otherwise leave the issue unchanged: no comment, no label change, no state change.

## Comment convention

Every comment posted during the sweep must begin with the tag `[meridian-triage]`.
