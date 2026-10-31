<!-- second-brain-repository-bootstrap:v1 -->

# Repository agent guide

This repository extends Abraham's canonical agent contract at
`/Users/abraham/src/second-brain/AGENTS.md`. Repository-specific instructions
below add to that contract; they do not replace it.

## Required task-start synchronization

Before substantive work or a substantive response in a new task:

1. Run `.codex/bin/repository-preflight` from anywhere inside this repository.
2. If it reports a dirty, detached, untracked, or diverged checkout, preserve
   the existing work and report the exact synchronization blocker. Never reset,
   clean, force, or overwrite work to make the preflight pass.
3. After a successful pull, read the current Second Brain `AGENTS.md`, then this
   file, before acting. Start a new task if pulled instruction changes must be
   loaded by the runtime immediately.

The preflight verifies the global Second Brain link and performs only
fast-forward pulls for clean checkouts with tracking branches.

## Repository-specific instructions

This is Abraham's development fork of `rfverbruggen/rachiopy`, the Rachio API
client used by Home Assistant. Default branch: `dev`. `origin` is the personal
fork; `upstream` is the official repository. The private household configuration
repository's issue #305 owns live adoption and the capability plan.

Keep credentials, household identifiers, API responses and private deployment
records out of this public fork. Tests use synthetic fixtures and mocked HTTP.
Preserve the client's existing response tuple and timeout behavior when adding
API methods. Do not introduce physical-device calls into tests.

Keep bootstrap guidance on fork `dev`. Future upstream contributions branch
from freshly fetched `upstream/dev` and exclude personal scaffold commits.
Abraham requested local use and verification before PRs; do not submit yet.

For code changes, install the declared requirements in an ignored virtual
environment, run `python3 -m unittest discover -v` and the applicable lint checks
in `tox.ini`. For bootstrap/docs-only changes, use the scaffold check,
`git diff --check` and repository preflight. This scaffold does not install the
full Python test environment.

Household deployment is owned by the private Home Assistant repository and
requires its live-operation queue, pinned versions, verification and rollback.
