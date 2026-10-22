# First Codex task — working vertical slice

**Goal:** stop redesigning screenshots; ship a tested document-control workflow.

1. Read `AGENTS.md` and the four files in `docs/`.
2. Audit `legacy/folio-workbench.html`. List which interactions edit real files, which are demo-only and which are unsafe or unmaintainable.
3. Set up a maintainable project with shadcn/ui-compatible components and end-to-end tests. Inspect the linked GitHub design repos and explain which components/design rules you actually reused.
4. Deliver a **single workbench**: client choice, upload MDR + many Word/PDF documents, document viewer, matched MDR row and exact differences, safe bulk edit, inline MDR row edit, finish batch.
5. For the first acceptance test, use one **fictional** multi-sheet MDR and two generated DOCX files with deliberately wrong dates. Match rows, fix both DOCX files, edit their corresponding MDR records, export corrected Word and MDR together. Read the exported files back in tests.
6. Preserve **all workbook formatting and tabs**, keep originals unchanged and block unsafe PDF edits.
7. Run tests and capture a 1280px screenshot, produce a concise report on actual results and limitations.
8. Submit your implementation in a reviewable PR. Do not deploy to production or use real Adleans/customer files.

**What the operator should see:** a list of files, the selected file's preview, the matching MDR values and clear corrections. One main action: **Finish batch**.

**What to avoid:** duplicate data entry, generic dashboards, onboarding tours, pretend AI analysis, ambiguous approval changes and “saved” notices without valid output files.

**First response from Codex:** a short evidence-based audit and implementation plan, followed by code/tests, not a new speculative product pitch.
