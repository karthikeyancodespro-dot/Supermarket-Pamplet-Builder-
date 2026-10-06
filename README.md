# Supermarket Pamphlet Builder

A no-build, browser-only app for making supermarket price-list pamphlets (vertical A4 or horizontal A5) and downloading them as **PNG, JPG, JPEG, WebP, PDF, PowerPoint (.pptx)** or printing them.

## Folder structure
```
index.html                 page markup (loads the files below)
css/styles.css             all styling (editor UI, pamphlet output, dialogs, mobile layout)
js/app.js                  all logic (state, rendering, editor, exports, tabs, undo/redo)
standalone/pamphlet-builder.html   the same app as ONE file (CSS + JS inlined)
manifest.webmanifest  sw.js  icons/   installable-app files (Add to Home screen)
vercel.json  package.json  .gitignore  CHANGELOG.md
```
`js/app.js` is organised in labelled sections: constants/state, geometry + pamphlet renderer (vertical `pages()`, horizontal `pagesH()`), product table, image editor/crop, columns, settings, downloads (`exportDlg`, `out`, `capture`), import/project, toolbar, extra features (stats, tabs, search, bulk images, undo/redo, templates, help, cursor trail), pamphlet tabs.

## Run it
* Double-click `index.html`, **or** run `npx serve .` and open the shown address.
* Needs internet for Google Fonts and the export libraries (html2canvas, jsPDF, PptxGenJS are loaded from cdnjs).

## Put it online (free)
* **Vercel:** `npm i -g vercel`, then run `vercel --prod` in this folder (framework "Other", no build). Or push the folder to GitHub and import it at vercel.com/new.
* **Netlify Drop:** drag this folder onto https://app.netlify.com/drop.
* **GitHub Pages / Cloudflare Pages:** publish the folder as a static site.
Once hosted over https, phones can "Add to Home screen" to install it like an app.

## How it works
* The pamphlet preview, PNG, PDF, PPT and print all come from the same renderer, so they always match.
* Each open pamphlet (tab) has its own columns, rows, settings, layout and undo history. Everything is saved automatically in the browser (localStorage); use **Save Project** to keep a file.
* No product data is hard-coded: new pamphlets start with one blank row; templates are optional.

## Shortcuts
Ctrl+Z undo · Ctrl+Y redo · Ctrl+S save project · Arrow keys move between cells (Ctrl+Arrow = jump to edge) · Enter next row (Product Name: Enter = new line, Ctrl+Enter = next row) · Shift+Enter previous row · Ctrl+D fill down · F2 edit cell · paste cells from Excel / Google Sheets.
