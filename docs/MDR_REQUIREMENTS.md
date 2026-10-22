# MDR workbook handling — do not flatten the client's register

The user provided a real multi-tab Adleans client Excel MDR during discovery. **The original workbook is not included in this public repository.** Obtain an approved, anonymized test copy directly from the project owner when necessary. Do not synthesize real client information from prior chat.

## Observed structure from earlier local testing

- The source workbook has **11 worksheets**: location-based sheets plus cover/summary material.
- **Eight location-based document tables** are used for reconciliation.
- Header rows are hierarchical/merged; section-divider rows are not document records.
- Distinct client document number and Adleans/contractor document number columns.
- Document title, revisions, current document status, transmittals, client comments and return codes.
- Separate stages (e.g., IFR, re-IFR, IFA, AFC) have date and transmittal fields.
- In the observed workbook mapping: Adleans document no. ~C, client document no. ~D, title ~E; IFR actual issue date/transmittal ~R/S; re-IFR ~Y/Z; IFA ~AE/AF; AFC ~AM/AN; latest revision ~AW and status ~AY. **These are fixture-specific observations, not universal positions. Validate against the actual worksheet headers before any write.**

## Requirements

1. Preserve the *original* workbook structure: worksheet names/order, styles, fonts, borders, merged headers, column widths, comments, formulas, validations and Excel date cell types.
2. Never use a generic blank Excel template as the exported MDR.
3. All data extraction should retain workbook sheet+row+cell addressing and source header mapping. The UI must show the real MDR row associated with each document.
4. Match by exact normalized document numbers (both schemes) and location. If duplicated across tabs or missing IDs, show a review-required state and ask for human selection.
5. Updating document administrative fields and recording transmission history are distinct actions. Don't pretend to transmit or advance approval stage.
6. Save a revised **working copy**; do not write back to a network-shared authoritative MDR unless a safe collaboration/locking workflow is approved.
7. Store change history (old/new value; sheet, row and column; document; status: proposed, applied, failed; user-provided reason where needed).
8. If an unsupported workbook feature may be lost by a chosen XLSX library, test it and block unsafe export.
9. Changing document fields and MDR fields in one operation is a staged, previewable transaction: allow approval and rollback, and never claim success when only one half applied.
10. Use fictional/generated fixtures in this repository. Never commit the actual customer MDR, even in screenshots.

## UX

One-click from the selected document to its matched MDR row. The important row fields should be directly editable in an unobtrusive inspector; a full-sheet editor can be a secondary disclosure. Show exactly which cell will change before applying.
