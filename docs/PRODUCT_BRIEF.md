# Folio — source of truth for Codex

## The user's actual job

A document controller at Adleans receives multiple engineering documents from engineers through email or WhatsApp. A client supplies its own Excel **Master Document Register (MDR)** and document-control procedure. She must check the administrative data in those Word/PDF files against the client's MDR and procedural/feedback requirements, correct what is safe to correct, send the corrected documents to the client via her existing method, and update the MDR to record the outgoing issue and what was changed for Adleans staff review.

**Do not implement email sending now.** She will download a ready batch and send it through her established email process. The tool should prepare everything together.

Her biggest time cost: manually opening many Word and PDF files, searching the MDR for each matching row, comparing numbers/titles/revisions/dates, correcting files one at a time, then repeating the updates in Excel.

## Primary experience — ONE interface

1. **Choose a client** (or add one). Each client retains its own MDR and files.
2. **Drop an MDR and 1–40+ engineering files** into one workbench. Additional files can be added at any time.
3. **Automatic reconciliation** recognizes MDR worksheets and document records and matches documents to rows. It shows uncertain/duplicate/missing matches without guessing.
4. **Review visually**: list of documents on the left; selected Word/PDF preview in the center; the exact matching MDR row, extracted document field, difference, and proposed change at the right. She can jump to the source, compare before/after, and edit the relevant value in place.
5. **Fix in bulk**: select all documents with the same supported date, title, document number or issue-field correction and apply the approved change. Do not rewrite unrelated content, invent approval codes, or claim pixel-perfect formatting.
6. **Maintain the MDR simultaneously**: for each accepted change, show the corresponding MDR working-copy update; allow editing a row's document/revision/issue/transmittal details inside the workbench; use the client's actual column mapping, never a generic replacement Excel template. Record who/what/when where appropriate.
7. **Finish batch**: one action packages corrected DOCX/PDF where safely supported, a revised MDR XLSX preserving its layout, a readable change log, and a small list of unresolved items. Originals remain unchanged.

The default view must answer **“What is wrong? What does the MDR say? Can I fix this now?”** — without a multi-page setup, tutorial, or dashboard.

## Field-level reconciliation

- Contractor/Adleans document number and client document number are distinct.
- Document title; location/station; date of issue; revision; issue purpose (IFR, re-IFR, IFA, AFC/AFD depending on client); return/comment codes; transmittal reference.
- Compare document field to the correct MDR field **and the actual transmission requirement**. Some new issue dates are legitimately different from historic MDR dates: do not naively overwrite new revisions with old values.
- Client comments may appear in the email body **or** the attached document. They can direct status transitions or engineering content changes. Present them as context for human decision, not automatic authority.
- Engineer handles technical content corrections. Folio focuses on administrative metadata and records, not editing technical engineering substance.

## Specific guardrails

- Source of truth for reference data: the **client-supplied MDR**, with client-specific procedure/feedback for actual issuance logic.
- The MDR is updated from actual transmission details. Do not mark a transmittal as sent or approved simply because files were exported.
- An IFR/re-IFR/IFA/AFC/AFD code must not progress automatically without client-specific approved procedure and client response.
- Partial edits are never silently treated as complete.
- If a file cannot be safely patched, preserve it unchanged and add a warning to the export report.
- Private company material must stay local by default.

## UI inspiration

A document reader meets a spreadsheet row editor. Think ChatGPT workspace clarity + Craft document readability: no CRM, no metrics cards, no confusing nested modals, no tiny fonts, no heavy visual decoration. Use practical design assets/references from `docs/DESIGN_REFERENCES.md`.

## MVP acceptance journey

With fictional data, load one MDR and two DOCX files containing the same incorrect issue date, locate the correct MDR rows, display “document says X / expected Y,” apply the date to both, preview results, update the MDR working copy with the correction and user-entered transmittal, and export files that open and retain layout. Complete without opening Microsoft Word or Excel. See detailed tests in `docs/ACCEPTANCE_TESTS.md`.

## Success metric

Target **80% less administrative handling time**, measured against real batches of 20–40 documents after validation. This is a hypothesis, not a proven improvement.
