# Folio

**Document control without the repetitive work.**

Folio is being rebuilt in Codex as a focused, single-screen workbench for the document controller at Adleans. Its purpose is to reconcile batches of engineering Word/PDF documents against a **client-supplied Master Document Register (MDR)**, correct supported fields, and keep the MDR working copy updated for Adleans staff review.

**The product is not a CRM, email client, or general document-management platform.** Its daily workflow is:

**Add MDR + documents → match each document to its MDR row → compare and correct in bulk → update MDR → export corrected documents and revised MDR.**

## Status

**Codex handoff / rebuild starting point.** The repository is intentionally not represented as production-ready.

- [Codex working instructions](AGENTS.md)
- [Complete product brief](docs/PRODUCT_BRIEF.md)
- [MDR data mapping and preservation rules](docs/MDR_REQUIREMENTS.md)
- [Design references and GitHub resources](docs/DESIGN_REFERENCES.md)
- [Acceptance tests and engineering checks](docs/ACCEPTANCE_TESTS.md)
- [Legacy prototype](legacy/folio-workbench.html) — functional reference only, **not** an approved architecture or UX.

## Use with Codex

1. Open [Codex](https://chatgpt.com/codex) and select **Jude-coedz/Folio**.
2. Ask it to read `AGENTS.md`, audit `legacy/folio-workbench.html`, and implement the first tested vertical slice described in `docs/PRODUCT_BRIEF.md`.
3. Require a PR with screenshots, test results, and sample exports before merging.
4. Configure Codex's project trust if you want it to load `.codex/config.toml` (shadcn MCP). The MCP command requires Node/npm and any network access the environment needs.

## Security

This repository is **public**. Never commit a real MDR, client documents, customer contacts, API tokens, or screenshots containing company data. Use fictional/generated fixtures only. The sample app must not upload files to a server by default. Process files locally unless there is an explicitly reviewed storage architecture and the company's authorization.

## Existing demo

The old browser app lives at `legacy/folio-workbench.html` (single self-contained HTML file). It includes synthetic test data and demonstrates some document matching, file correction and spreadsheet export capabilities. It also has known UX, format-preservation and maintainability limitations. **Do not build more dashboard layers on top of it.** Replace it incrementally with tested modular code.

## Definition of success

A nontechnical document controller can process a representative batch without switching between Word and Excel to locate and copy matching fields. Measure time and error rate against the existing manual workflow; **80% time reduction is a target, not a verified result**.
