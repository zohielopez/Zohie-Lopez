# Zohie Lopez Portfolio

Personal portfolio site for Zohie Lopez: styling, creative direction, marketing, and product work.

It is a plain static site with no build step and nothing to install. Open `index.html` in a browser to preview it locally.

## What's in the folder

```
index.html               the whole site: styles, page content, and navigation
images/                  every photo and slide on the site
Zohie-Lopez-Resume.pdf   resume linked from the About and Contact pages
```

## Where to edit things

Everything lives in `index.html`. Search the file for these labels:

| To change… | Search for |
|---|---|
| Your email | `const EMAIL` |
| The project list (titles, categories, cover images, team credits) | `const PROJECTS` |
| The "What I learned" paragraphs | `const LEARNED` |
| A specific project page | `PAGES['city-boots']`, `PAGES['kerr-chief']`, `PAGES['runway']`, `PAGES['for-love-lemons']`, `PAGES['ganni']`, `PAGES['j-crew']`, `PAGES['jcrew-field']`, `PAGES['graphic-design']` |
| Home page | `PAGES.home` |
| About page and resume details | `PAGES.about` |
| Contact page, LinkedIn, Instagram | `PAGES.contact` |
| Project years | `Year</dt>` |
| Colors and fonts | the `:root {` block at the top of the `<style>` |

## Adding a photo

1. Save the photo in `images/` as a `.jpg` with a short lowercase name, for example `images/new-shoot-01.jpg`. Keep it under about 1600px on the long side so the site stays fast.
2. In the page where it should appear, add:

   ```js
   ${img('Short description of the photo', '4/5', 'a', '', I('new-shoot-01'))}
   ```

   - The first value is the alt text, which screen readers and search engines use.
   - `'4/5'` is the frame shape. Use `'3/4'` or `'2/3'` for portrait, `'3/2'` or `'16/9'` for landscape, `'1/1'` for square.
   - `I('new-shoot-01')` is the file name without `images/` or `.jpg`.

To add a caption, wrap it like this:

```js
<figure style="margin:0">${img('Description', '4/5', 'a', '', I('new-shoot-01'))}<figcaption>Your caption</figcaption></figure>
```

## Adding a new project

1. Add an entry to `const PROJECTS`. Copy an existing line and change the `id`, `title`, `sub`, `cat` (`styling`, `marketing`, `product`, or `design`), `catLabel`, `role`, `focus`, and `cover`.
2. Add a page for it: copy one of the `PAGES['…'] = () => { … }` blocks, rename it to the new `id`, and replace the content.
3. The project then shows up on the Work page and in the filters automatically.

## Updating the resume

Export the new resume from Word as a PDF, name it `Zohie-Lopez-Resume.pdf`, and replace the old file. The links pick it up automatically.

## Publishing (GitHub + Netlify)

1. **GitHub:** Create a new repository (for example `zohie-lopez-portfolio`) and upload everything in this folder, or push it with Git.
2. **Netlify:** Sign in at netlify.com with GitHub → *Add new site* → *Import an existing project* → pick the repository. Leave the build command empty and set the publish directory to `/` (the root). Deploy.
3. **Domain:** In Netlify, open the site → *Domain management* → *Add a domain* to buy one (for example `zohielopez.com`) or connect one you own. Netlify turns on HTTPS automatically.

After that, every change pushed to GitHub goes live on its own in under a minute.
