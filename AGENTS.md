# Codex instructions — Folio

Read `docs/PRODUCT_BRIEF.md`, `docs/MDR_REQUIREMENTS.md`, `docs/DESIGN_REFERENCES.md`, and `docs/ACCEPTANCE_TESTS.md` before writing code.

## Product principles
- Solve one job: **reconcile engineering documents with a client MDR, batch-correct supported administrative fields, update the MDR, export both**.
- Do not reintroduce email sending, approval dashboards, project analytics, complex onboarding, or separate workflows without a concrete user need.
- The app has a single daily workbench. The document, the matching MDR row and the proposed correction are visible together.
- Avoid needless dialogs, toggles, navigation, and repeated typing. Progressively disclose rare fields.
- Preserve multiple client workspaces, each with its own MDR and document batch.
- Never guess the next IFR/re-IFR/IFA/AFC/AFD stage or issue/transmittal code. Client procedure and actual client feedback govern these.

## Accuracy, privacy, file safety
- Never modify uploaded originals. Export revised copies and a change log.
- Require deterministic document-to-MDR row matching using client/contractor number plus location when ambiguous. No confident match means human confirmation.
- Do not silently overwrite PDF text. Scanned/signed/complex PDFs require visual review or manual editing unless independently demonstrated safe.
- All changes must identify **field, original value, MDR/reference value, chosen new value, source, and document/row**.
- Update an **MDR working copy**, retaining sheets, formulas, merged cells, formatting, date types, comments, and transmittal history. Show any preservation failure.
- Do not transmit company documents to external APIs, telemetry, or AI providers without explicit authorization.
- This GitHub repository is public: **never commit the real uploaded Adleans MDR or real client files**.

## Engineering process
1. Audit the legacy monolithic browser app; document existing behavior and failure modes.
2. Propose a minimal, testable modular architecture. Preferred UI: React + TypeScript + Tailwind + shadcn/ui, if justified. Choose reliable spreadsheet/docx/PDF libraries based on actual format-preservation tests.
3. Build a single end-to-end slice first: upload synthetic MDR and two Word files → identify date mismatch → apply to both → update the proper MDR rows → export valid XLSX and DOCX files.
4. Test changes by reading back exported Office files; render and visually compare pages for formatting. Add unit + browser tests.
5. Then add side-by-side viewer, editable MDR row, batch selection, multi-client switching, and safe PDF support.
6. Create a PR with before/after screenshots, precise test commands, and remaining unsupported cases. Do not present mock interactions as implemented functionality.

## Interaction design
- Use the reference repos in `docs/DESIGN_REFERENCES.md` as researched design guidance, not mere keywords. Evaluate component licenses and compatibility.
- Prioritize legible modern sans serif typography (16px+ body where useful), generous but disciplined spacing, clear contrast, keyboard accessibility, and calm neutral surfaces.
- Borrow ChatGPT's low cognitive load and Craft's document clarity, **not** their unrelated features.
- Avoid ornamental glass effects over documents and tabular values. Respect reduced motion.
- Explain issues plainly: “Document says X · MDR says Y · Use MDR value”. Do not display raw codes without a tooltip/meaning.

## Codex execution
- Project-scoped shadcn MCP settings are in `.codex/config.toml` and require trusted project configuration. Do not claim installation before testing `npx shadcn@latest mcp`.
- Run/test the app and inspect the exported files before saying a feature works.
