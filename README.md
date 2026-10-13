# GradeSnap — GitHub Pages edition

A mobile-first static web app to upload an Excel workbook, view an uploaded photo of a handwritten class record, enter/verify scores, and download an updated **copy** of the Excel file. No backend or SharePoint needed.

## Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `gradesnap`).
2. Upload `index.html`, `style.css`, `app.js`, `manifest.webmanifest`, and `icon.svg` to the repository **root** (not inside another folder).
3. In the repository, open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, `main`, `/ (root)`, and **Save**.
4. Wait for GitHub Pages to publish. Your URL will typically be `https://YOUR-USERNAME.github.io/gradesnap/`.
5. Open that URL on your iPhone in Safari. Use Share → Add to Home Screen if desired.

## Use

1. Upload an `.xlsx` workbook.
2. Choose the target worksheet and specify student-name column, student row range, first score column, and number of score columns.
3. Tap **Load student roster**. Check the student list carefully.
4. Take a photo of your paper class record; optionally run experimental OCR to get a rough text draft.
5. Manually enter or paste verified scores into the roster table. Blank fields are skipped; `0` is a real score.
6. Check the verification box and tap **Download updated Excel**.

## Important limitations

- **GitHub Pages is static hosting.** It cannot run Python, server-side AI, or directly update a file on your laptop. This version processes Excel **in the browser** and downloads an updated copy. It does not overwrite the original.
- **Automatic handwriting-to-student matching is NOT implemented.** The OCR draft is only a reference and may be inaccurate for handwriting. Do not trust it without checking every value.
- ExcelJS may not preserve every advanced Excel workbook feature (some drawings, specialized formulas, pivot objects, and other complex components). **Test with a disposable copy** and compare before using actual grades. Formula cells are blocked from being overwritten, but that does not guarantee all workbook features survive re-export.
- Browser libraries (ExcelJS and Tesseract.js) are loaded from public CDNs, so the first load needs internet. Files are processed locally by app JavaScript and not intentionally uploaded by this application.
- Uploaded photo and Excel data are not stored on GitHub Pages. Do not commit student workbooks or student photos to a public GitHub repository.
- There is no user authentication or cross-device sync. The file must be selected each session.
