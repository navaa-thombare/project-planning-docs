# Python Desktop App SRS Plan — 2026 Refinement Pack (Text-Only)

This document provides a complete, text-based refinement of the planning workbook content so it can be reviewed and applied without changing binary files in this repository.

## 1) Executive Direction

### Product Intent
Build a secure, maintainable Python desktop platform with strong RBAC, migration discipline, and release governance suitable for regulated or enterprise-like environments.

### 2026 Baseline Recommendations
- **Runtime**: Python 3.12+.
- **Desktop UI**: PySide6 (Qt6) with reusable design system components.
- **Data Layer**: SQLAlchemy 2.x patterns (typed models/repositories), PostgreSQL 16+.
- **Migration Control**: Liquibase with preconditions, rollback checks, and CI migration validation.
- **Quality Tooling**: Ruff, Black, MyPy, pytest, pre-commit.
- **Packaging**: PyInstaller/Briefcase with artifact signing and release manifest.
- **Security Baseline**: Argon2id, lockout/rate limiting, least privilege RBAC, secrets externalization, supply-chain scanning, SBOM/provenance.

---

## 2) Sheet-by-Sheet Refinements

## README (Suggested Replacements)
- Recommended UI stack: emphasize responsive desktop UX, keyboard-first workflows, and reusable widgets.
- Migration strategy: add CI drift checks, migration smoke tests, and rollback validation.
- Architecture style: shift to modular monolith with hexagonal boundaries and contract-first interfaces.
- How-to-use section: explicitly call out quality gates and release criteria as planning artifacts.

## SRS (Suggested Replacements)
- **Technical stack**: Python 3.12+, PostgreSQL 16+, typed/static checks, automated migration validation.
- **Security expectations**: Argon2id with cost tuning, optional MFA readiness, signed builds, dependency governance.
- **Extensibility expectations**: module registry, event hooks, versioned contracts, additive changesets.
- **Success criteria**: acceptance requires passing automated security/quality gates, not only feature completion.

## Requirements (Suggested Replacements)
- Upgrade password requirement to memory-hard hashing with transparent rehash path.
- Expand lockout requirement into adaptive rate limiting plus testable policy.
- Add measurable performance wording (e.g., P95 <= 2 seconds for core workflows under expected desktop conditions).
- Add reliability requirement for correlation IDs and structured error events.
- Add supply-chain integrity requirement (pinned dependencies, vulnerability checks, SBOM/provenance).

## Roles_Permissions (Suggested Replacements)
- Add `security.audit` permission for posture/review workflows.
- Clarify split of duties:
  - `superadmin`: full security and governance controls.
  - `admin`: operational management with constrained security privileges.
  - `manager`/`user`: no direct security posture mutation.

## DB_Schema (Suggested Additions)
- Add/strengthen status and enum-like check constraints to reduce invalid state transitions.
- Ensure indexes cover identifier normalization lookups, RBAC joins, and audit query windows.
- Include versioning metadata for migrations and operational traceability.

## Liquibase_Plan (Suggested Replacements)
- Add explicit changeset for check constraints and invariant enforcement.
- Include precondition strategy for idempotence and safe reruns.
- Add CI command sequence expectations (validate, updateSQL, update on ephemeral DB).
- Require rollback verification for high-risk schema changes.

## Milestones (Suggested Reframing)
1. **Foundation, Architecture & Quality Gates**
2. **Data Platform & Migration Automation**
3. **Identity & Access Core**
4. **RBAC Administration**
5. **Observability, Hardening & UX Polish**
6. **Test Automation, Packaging & Release Governance**

## Plan (Suggested Task Refinements)
- Early tasks: architecture + CI quality gates + coding standards.
- Mid tasks: auth with rehash path, lockout/rate limiting, and audit hooks.
- Late tasks: structured logging/correlation IDs, resilience policy, signed artifacts, runbook/handover.
- Exit criteria: release blocked unless migration checks, automated tests, and packaging/signing checks pass.

## Prompts (Suggested Rewrites)
- Update architecture prompts for typed boundaries and test seams.
- Update auth prompts for Argon2id rehash and auditability.
- Update testing prompts for risk-based regression and release blockers.
- Update packaging prompts for signed binaries and operational diagnostics.

---

## 3) Proposed Acceptance Criteria Upgrade

Define release gates that must be green before production handoff:
- Lint/format/type checks pass.
- Unit + integration test suite pass.
- Liquibase validation/update dry-run checks pass.
- Security checks (dependencies/secrets policy) pass.
- Installer/build artifact is signed and verifiable.
- Handover package includes admin runbook + rollback notes.

---

## 4) Implementation Sequence (Practical)

- **Week 1**: Architecture decisions, project scaffold, quality gate setup.
- **Week 2**: Schema + migrations + repository baseline.
- **Week 3**: Authentication and account security controls.
- **Week 4**: RBAC admin screens and enforcement.
- **Week 5**: Audit logging, resilience, UX polish.
- **Week 6**: Full test pass, packaging/signing, release documentation.

---

## 5) Outcome

This refinement keeps the original workbook intent but upgrades it to contemporary engineering expectations: measurable quality, stronger security posture, better operational readiness, and maintainable long-term extensibility.
