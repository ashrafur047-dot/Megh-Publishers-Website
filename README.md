# মেঘ পাবলিশার্স (Megh Publishers)

The public website for Megh Publishers. Visitors can browse the catalogue, search by book title or author, and read each book as a PDF in the browser or download it.

Books currently published: **হেনা ভিলা** (Hena Villa), **জল জ্যোৎস্না** (Jol Jotsna) and **মৃন্ময়ী** (Mrinmoyi), all by আশরাফুর রহমান.

## Technologies

- Plain HTML, CSS and a small amount of vanilla JavaScript, with no framework and no build step
- Netlify for hosting, configured in `netlify.toml`
- Netlify Image CDN (`/.netlify/images`) to resize book covers and the logo and serve them as WebP
- Google Fonts: Noto Serif Bengali and Hind Siliguri

## Project layout

```
public/
  index.html     catalogue page (book list lives in the BOOKS array)
  404.html       not-found page
  books/         book PDFs
  covers/        cover images (JPEG)
  img/logo.png   publisher logo
netlify.toml     publish directory and response headers
```

## Adding a book

1. Put the PDF in `public/books/` and the cover image in `public/covers/`. Use lowercase hyphenated filenames, for example `new-book.pdf`.
2. Add an entry to the `BOOKS` array in `public/index.html`:
   ```js
   {title:"বইয়ের নাম", author:"লেখকের নাম", file:"/books/new-book.pdf", cover:"/covers/new-book.jpg"}
   ```
3. Add a link to the `<noscript>` fallback in the same file.

## Running locally

```bash
netlify dev
```

Run it with the Netlify CLI so the `/.netlify/images` URLs for covers and the logo work. A plain static server shows the page without images.
