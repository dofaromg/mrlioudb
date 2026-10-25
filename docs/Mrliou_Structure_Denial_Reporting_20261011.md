# MRL structure-index denial reporting — 2026-10-11

origin_signature: MrLiouWord
canonical_authority: Mr.liou
Repository: dofaromg/mrlioudb
Base: 183c08792b6825c4f4b279f300ffa6b3eac7bd7a
Mode: review branch; no automatic main merge; no operational grant created.

## Evidence and authorization boundary

Run 38105364910 failed at authorization with NO_RECORDED_GRANT.
The current registry has no active grants and requires explicit Root authorization.
Reviewed LAW-0 in FlowAgent_ASI_Terminal_v1.md section 8 (signature is identity),
RootLaw_Package_v1.midlock/RootLaws_v1.md Law 30, and Execution_Laws.md.
Reviewed Notion Mother https://app.notion.com/p/3e9e7f4e6c5580e49f3dc8292dda835a,
L7 https://app.notion.com/p/a45ff7597bfc44189b4cf6aaacf071cf and proposal
https://app.notion.com/p/3ebe7f4e6c5581f29119d730e3b46dd6.
No applicable explicit grant was found in the inspected sources. This is not a
claim that no other grant exists. General collaboration and identity records do
not supply this repository's actor, environment, scan/upload destination and term.

## Behavior and rollback

Opt-in preflight reporting maps only NO_RECORDED_GRANT from a validated empty
registry to EXPECTED_DENY with allowed=false. The reporting command exits zero
because reporting completed; authorization remains DENY and no index is updated.
All scan/generate entry points retain their original nonzero denial behavior.
Upload cannot use reporting mode and retains its authorization recheck.
Invalid/missing registry, nonmatching or expired grants, and execution errors
remain failures. Dependency install, scan, generation and change detection
are explicitly allowed-gated. Summaries contain metadata only.
Daily 02:00 UTC and Monday 00:00 UTC schedules remain unchanged.
PR events run synthetic tests only and checkout the exact PR head.
Rollback: revert this review commit through a separately reviewed PR.
No rights transfer, registry grant, main merge, service restart or DL580 change.

## Verification scope

Regression tests include synthetic expected denial, unchanged scanner/upload
denial, malformed/missing registry, foreign grants, authorized fixture output,
workflow gating, original trigger preservation, delivery hashes and dependencies.
Remote exact-head CI results must be inspected before claiming validation PASS.
Expected modification count: 5 (guard, workflow, tests, delivery manifest, this
document). The existing manifest records actual payload hashes and dependencies;
its own hash is excluded to avoid circular self-reference.


## 2026-10-25 continuation (append-only)

origin_signature: MrLiouWord; canonical_authority: Mr.liou.
Existing PR #2 is continued; no duplicate PR or operational grant is created.
The 2026-10-25 main run was inspected: authorization-regression succeeded,
preflight returned DENY / NO_RECORDED_GRANT with exit 1, and scan, generation,
and upload were skipped. Main has not yet adopted this reporting change.
The validated registry still has active_grants=[]; reporting success never
means Owner authorization or index generation. Only NO_RECORDED_GRANT is an
expected denial. Malformed, missing, unmatched, expired, revoked, ambiguous,
and invalid-context grants remain fail-closed; output I/O failure remains a
program execution failure. New synthetic cases cover expired/revoked grants
and workflow-output I/O failure without touching the real source tree.

Grant matching requires exactly one active record: issuer MrLiouWord, exact
actor/triggering actor, environment, repository, root assets, destination,
ref/event, purpose, requested actions/depth, valid start/expiry, and no
prohibited requested action. Identity or repository access is not a grant.
Registry and historical structure artifacts are unchanged.

Sources re-read: repository FlowAgent_ASI_Terminal_v1.md section 8,
RootLaw_Package_v1.midlock/RootLaws_v1.md Law 30, Execution_Laws.md,
and the three Notion URLs recorded above. These general governance records
are not substituted for a scoped operational grant. Synthetic local tests
must be distinguished from GitHub exact-head CI and production execution.

Source run: https://github.com/dofaromg/mrlioudb/actions/runs/40154082831


## 2026-10-25 exact-head CI and integration continuation

origin_signature: MrLiouWord; canonical_authority: Mr.liou.
Exact head 7953e34cada88fdd11165b02d4d5bfbca7c43f0a was checked out by
GitHub run 40207905066: authorization-regression 55/55 PASS, operational
update-structure-index SKIPPED; no artifacts generated or uploaded.
The earlier lack of bot-head GitHub Actions evidence is now resolved for
that fixed SHA, not automatically for subsequent commits.

Independent PR validation run 40207396659 / job 121211160499 successfully
rendered the production Kustomize overlay, then incorrectly passed its
multi-document YAML stream to yaml.safe_load and raised ComposerError.
The existing PR receives one minimal parser correction: eagerly consume
list(yaml.safe_load_all(...)), matching the already repaired workflow in
MRL_ASI_system. Valid multi-document synthetic input parses; a malformed
second document still raises YAMLError. No cluster manifest, deployment,
Registry or permission is changed. This is a CI parsing repair, not Owner
authorization and not successful index generation. Re-run remote CI for
the subsequent candidate before claiming this integration defect closed.
