# AGENTS.md

## What this is
Megh Publishers' public catalogue site. It is a single static page that lists books and links to their PDFs. There is no framework, no package.json and no build step. Netlify publishes `public/` as-is (see `netlify.toml`).

## Key files
- `public/index.html` contains all markup, CSS and JS. The catalogue is the `BOOKS` array in the inline script, and `render()` builds the grid and runs the client-side search on title and author.
- `public/404.html` is the not-found page.
- `public/books/*.pdf` holds the books and `public/covers/*.jpg` holds the covers. `public/img/logo.png` is the logo.

## Conventions and decisions
- UI text is in Bengali (`lang="bn"`). Keep new copy in Bengali.
- Images always go through Netlify Image CDN (`/.netlify/images?url=/covers/x.jpg&w=400&fm=webp`). Don't link the original files from the page.
- The logo used to be a ~700 KB base64 data URI inside index.html. It was moved to `public/img/logo.png` to keep the HTML small. Don't inline it again.
- Two of the original cover files were JPEGs with a `.png` extension. They were renamed to `.jpg`.
- Use absolute paths (`/books/...`) so links also work from the 404 page and from nested URLs.
- When you add a book, update both `BOOKS` and the `<noscript>` fallback list.
- Don't add a build tool unless the site really needs one.
