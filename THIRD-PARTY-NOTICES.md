# Third-party notices

`index.html` is a single self-contained file that bundles the components below. Each is
used **unmodified** (as published to npm) under the Apache License, Version 2.0. Their builds
are inlined verbatim into the HTML; where a build carries its own copyright header, that
header is preserved in the inlined code.

A copy of the licence is at <http://www.apache.org/licenses/LICENSE-2.0>.

| Component | Version | Copyright | Project |
|---|---|---|---|
| pdf.js | 3.11.174 | Mozilla Foundation and contributors | <https://github.com/mozilla/pdf.js> |
| SheetJS (`xlsx`) | 0.18.5 | SheetJS LLC | <https://github.com/SheetJS/sheetjs> |
| tesseract.js | 5.1.1 | Jerome Wu and contributors | <https://github.com/naptha/tesseract.js> |
| tesseract.js-core | 5.1.0 | Jerome Wu and contributors | <https://github.com/naptha/tesseract.js-core> |
| Tesseract OCR engine | 5.x (via tesseract.js-core) | Google Inc. and contributors | <https://github.com/tesseract-ocr/tesseract> |

`tesseract.js-core` and the Tesseract language data are **not** bundled — they are fetched at
run time from a CDN the first time a scanned PDF needs OCR, and are listed here because they
execute as part of the application.

Tesseract language data files (`*.traineddata`) published by the Tesseract project are
distributed under the Apache License, Version 2.0.

> Unless required by applicable law or agreed to in writing, software distributed under the
> License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
> either express or implied. See the License for the specific language governing permissions
> and limitations under the License.

No endorsement by any of the above projects is implied.
