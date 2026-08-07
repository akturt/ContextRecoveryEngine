# Contributing to Context Recovery Engine

This file is the **Engineering Playbook** for CRE. It is part of the open-source
project, not part of any Knowledge Governance Runtime. Follow it for every change.

## Rules

1. **Spec first.** Any change starts from `docs/spec.md`. Update the spec before
   the code, not after.
2. **ADR for architecture decisions.** Non-trivial architecture decisions are
   recorded as ADR files under `docs/adr/`.
3. **File gate.** A source file or module is created only if it is invoked by the
   demo `cre recover → publish → DataHub`. Documentation files
   (`README.md`, `docs/spec.md`, `docs/architecture.md`, `NON-GOALS.md`,
   `CONTRIBUTING.md`, `docs/adr/*`) are exempt — they are part of the OSS contract.
4. **Scope audit.** Every change passes an architecture audit for scope expansion.
   If it pulls in Runtime, Registry, Bootstrap, Discovery Layer, Knowledge
   Governance, or any Underboss subsystem — reject it. CRE is a standalone
   `cre-core` library; Underboss stays outside as a development tool, never a
   dependency.

## Self-contained by design

CRE must work with only:

```
git clone https://github.com/akturt/ContextRecoveryEngine
uv sync
cre recover https://github.com/fastapi/fastapi
cre publish
```

No Runtime, no Bootstrap, no Registry, no agent rules required.
