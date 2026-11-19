# Folder Runner

One HTML file that runs any folder of HTML, CSS and JavaScript — no server, no build step, no file-size limit.

Many computers choke on a local website made of several connected files (browsers block `file://` scripts, modules, `fetch()` and stylesheets that reference each other). Drop the whole folder onto this single page and it runs as if it were hosted.

## Use

1. Download `index.html` and open it in any modern browser.
2. Drag a folder onto the page (or use **Choose a folder…**).
3. It picks `index.html` (or the shallowest HTML file) and runs it.

Everything happens in your browser. No file is ever uploaded anywhere.

## What works

- Every page, stylesheet, script, image, font, video and audio file in the folder
- Relative paths (`css/app.css`, `../img/logo.png`) and root-absolute paths (`/css/app.css`)
- `<link>` stylesheets with `@import` and `url(...)`
- ES modules (`type="module"`) with relative `import` / `export … from` / `import()`
- `fetch()`, `XMLHttpRequest` and `srcset` against files in the folder
- Links between pages, back button and page switching
- `localStorage` / `sessionStorage` (in-memory fallback where the browser blocks them)

## What it can't do

- No server-side code: PHP, Node, Python and real HTTP endpoints don't exist here.
- `POST` forms are replayed as `GET` with the same fields.
- Module graphs with circular `import`s between files are not flattened.
- Service workers are not available to the loaded site.

## How it is fast

Files are handed to the browser as references — nothing is base64-encoded or copied. Binary assets go straight to object URLs, only the HTML/CSS/JS that a page actually uses is parsed, and each built page and module is cached so navigating back is instant.
