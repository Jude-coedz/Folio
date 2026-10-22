# Acceptance tests and quality gates

## P0: one authentic end-to-end workflow

Using **fictional files** (never the actual private MDR in CI):

1. Import an XLSX fixture preserving the source-style multi-tab layout, merged headers and Excel date cells.
2. Import at least two DOCX engineering files with the same incorrect issue date, plus a correctly matched title and distinct contractor/client document numbers.
3. Match each file to the intended MDR sheet and row. Show ambiguity when an ID occurs in multiple sheets.
4. Render the selected document inside the app. Show “Document value / MDR or planned-issue reference / proposed new value” and a clear one-click edit.
5. Batch-apply an approved date correction to the two DOCX files.
6. Record before/after details and the corresponding MDR changes in a working copy, using actual mapped columns, not a generic spreadsheet.
7. Allow an editable issue/transmittal value **only after user entry**; do not infer that an email was sent.
8. Export DOCX files, an XLSX working copy and a reconciliation report in one package.
9. Independently reopen exported DOCX and XLSX files in tests; verify the exact intended edits, unchanged unrelated fields, cell date types, formulas, sheet order and merged headers.
10. Render and compare pre/post DOCX pages; check that field edit did not corrupt title blocks or footers.
11. Reset and import a second client, then return to the first; records remain isolated.

## P0 negative and safety paths

- Missing/duplicate document number => require manual match, do not auto-write.
- Unknown revision/client return code => cannot automatically advance issuance stage.
- PDFs that are scans, digitally signed or layout-sensitive => view, warn, never silently patch.
- Incorrect/missing MDR => no “ready” status; allow document browsing without unsafe changes.
- Unsuccessful DOCX patch or workbook write => keep file out of “corrected” results, show diagnostic.
- Workbook with unsupported features => warn/block unsafe export.
- Never change originals; preserve failure case and provide recoverable working copy.
- Test empty inputs, bulk selection, additional files mid-workflow, large batches, and keyboard navigation.

## Technical tests

- Unit: parsing, metadata extraction, deterministic matching, duplicate handling, source mapping, date format normalization, safe patches.
- Integration: real generated DOCX/PDF/XLSX files, export archive read-back.
- Browser: Playwright entire workflow, screenshots, readable 1280px layout, 3-pane behavior.
- Security: no external upload unless explicitly authorized; validate MIME/content, size, filename sanitization, zip-bomb controls, and browser storage limits.
- Performance: benchmark 20–40 documents and large MDR worksheets on representative Windows machines.

## Definition of done for Codex PRs

- Actual files changed, not only the UI.
- Tests pass with commands included.
- Failure/formatting limitations documented; no claims of perfect PDF edits.
- Short before/after screenshots, export verification results and reproducible test fixtures.
- No company/client documents, confidential spreadsheets, API keys or private URLs committed.
