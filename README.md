# PDF Region Extractor

Turn a pile of similar PDFs into a spreadsheet by drawing boxes on one of them.

**Live app:** https://rgs2007.github.io/pdf-data-extraction/

Everything runs in the browser. No document is ever uploaded — the page reads your
PDFs with the File API, parses them with pdf.js, and OCRs scanned ones with
Tesseract compiled to WebAssembly, all on your own machine. The only network
traffic the page ever makes is downloading the OCR engine the first time a scanned
PDF needs it.

## How it works

1. **Import PDFs.** Drag them in, or pick a whole folder.
2. **Draw the group anchor.** Drag a box around the text that identifies the document
   type — a vendor name, a form title. That single action creates a *group*, named after
   the text it captures. Two PDFs belong to the same group when the text inside that exact
   rectangle matches (fuzzy, with an adjustable threshold).
3. **Add columns.** `+ Field` for a single value, `+ Table` for a whole table — mark its
   header band and the columns are split out automatically, with the inferred grid drawn
   over the page so you can see what it will read. Headers on the top, bottom, left or
   right all work; the data is read from the opposite side.
4. **Run.** Every PDF is matched against every group's anchor. Matches get their regions
   extracted — straight from the text layer when there is one, by OCR when there isn't.
5. **Review.** Step through the results with the values printed on the page itself; tables
   get a crop of the region shown above the grid that was read out of it, columns aligned.
6. **Export.** Fix anything by typing into the table, then download an `.xlsx`.

PDFs that match no group are flagged; draw an anchor on one and it becomes the next group.
If one document in a group needs a region nudged, the app asks whether that change belongs
to the whole group or just that document — the second option forks a new version of the
group rather than disturbing rows you already checked.

## Running it

It is a single self-contained HTML file. Open
[`index.html`](index.html) from disk, or use the hosted copy above. Nothing to
install, no build step, no server.

### Working offline

OCR pulls its engine (~8 MB) from a CDN the first time a scanned PDF is processed, then the
browser caches it. To avoid that entirely, serve a folder containing `worker.min.js`, the
`tesseract-core-simd-lstm` files and `eng.traineddata`, and point
**Settings → OCR engine files** at its URL. Digital PDFs never need any of it.

## Privacy

Your PDFs stay on your machine. The app holds file handles, not copies, and reads bytes only
when a page needs rendering or extracting. `localStorage` keeps your settings and your last
template — group names, region coordinates, column names and the anchor's extracted text —
and nothing else. Extracted values live in memory only, so download the spreadsheet before
closing the tab.

## Third-party components

pdf.js, SheetJS, tesseract.js and the Tesseract engine, all under Apache-2.0.
See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
