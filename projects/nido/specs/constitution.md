# 📜 Nido constitution

Non-negotiable principles. Every spec, plan and PR must respect them.

1. **Hexagonal architecture.** The domain doesn't depend on frameworks. Adapters live at the edges.
2. **Tests first in the domain.** Each acceptance criterion maps to at least one test.
3. **Security by default.** Every endpoint is authenticated unless the spec says otherwise; inputs are validated; no secrets in the repo.
4. **Privacy by design.** Collect the minimum data. Sensitive documents aren't stored unless the user opts in. PII is anonymised before reaching an LLM.
5. **AI is advisory.** AI output is never presented as a legal or financial verdict. It is always explained and validated against a schema.
6. **Spec before code.** Ambiguities are marked `[NEEDS CLARIFICATION]`, never guessed.
7. **Small, reviewable changes.** One issue, one branch, one PR, written with Conventional Commits.
8. **English** for code, docs and commits.
