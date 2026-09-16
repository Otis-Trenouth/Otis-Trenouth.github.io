# My Portfolio Site

A single-page personal portfolio. No build step, no frameworks, no dependencies.
Double-click `index.html` and it opens in your browser exactly as it will look online.

```
index.html        ← ALL your content. The only file you need to edit.
robots.txt        ← keeps the site out of Google. Don't delete unless you want to be findable.
.nojekyll         ← tells GitHub to serve the files as-is. Leave it alone.
assets/
  style.css       ← all the design. You don't need to open this.
  photo.jpg       ← YOU ADD THIS: your headshot
  resume.pdf      ← YOU ADD THIS: your resume
  projects/       ← YOU ADD THESE: your project PDFs
```

---

## Step 1 — Fill in your content

Open `index.html` in Notepad, or better, [VS Code](https://code.visualstudio.com/) (free).

Everything you need to change is marked with a comment containing the word **EDIT**.
Search the file for `EDIT` and work through the hits top to bottom:

| What | Where |
|---|---|
| Page title and link preview text | top of the file, in `<head>` |
| Your name | appears in the nav, hero, and footer |
| Role line and tagline | the `hero__role` and `hero__tagline` paragraphs |
| About paragraphs | the `#about` section |
| Projects | the `#projects` section |
| Skills | the `#skills` section |
| LinkedIn URL | appears twice — hero buttons and contact section |
| Your email | the two lines at the very bottom, in the `<script>` |

**Adding a project:** copy one entire `<article class="card"> ... </article>` block and paste it
below the last one. Change the text. Removing a project is just deleting its block.

**Your email** is split into two variables at the bottom of the file:

```js
var EMAIL_USER   = "yourname";
var EMAIL_DOMAIN = "example.com";
```

That's deliberate — it stops the simplest address-harvesting bots from scraping it out of the page
source. The page puts it back together in the browser, so visitors see a normal clickable address.

**Changing the colour:** open `assets/style.css` and change the `--accent` line in the block at the
very top. That one value drives the whole site.

---

## Step 2 — Add your files

- **Headshot** → save as `assets/photo.jpg`. Square crops look best; anything from 400×400 to
  1000×1000 pixels is fine. Until you add it, the page shows your initials in a circle instead —
  change the `YN` in the `photoFallback` div to your own initials.
- **Resume** → save as `assets/resume.pdf`
- **Project reports** → put them in `assets/projects/` and update the filenames in the card links.

### Before you upload a PDF, scrub it

Everything in this repository is public and directly downloadable. The `robots.txt` keeps the *page*
out of search results, but it does not make the files private.

- Remove your **phone number** and **home address** from the resume copy you upload. Keep email and
  LinkedIn. Recruiters who want to call will email first.
- Check project reports for your **student number**, and for teammates' names and student numbers —
  those aren't yours to publish. Ask them first or remove them.
- If a project was done for a company or a sponsor, check you're allowed to publish the report.
  Describing what you did is almost always fine; the full technical report often isn't.

---

## Step 3 — Put it online (free)

1. **Make a GitHub account** at [github.com](https://github.com) if you don't have one.

   Pick the username carefully — **it becomes your web address.** A repository named
   `yourusername.github.io` publishes at `https://yourusername.github.io`. That URL goes on your
   resume, so choose something you'd be happy to print.

2. **Create a repository** named exactly `yourusername.github.io` (your real username). Set it to
   **Public** — GitHub Pages on a private repo requires a paid plan. Don't add a README, this folder
   has one.

3. **Upload.** On the new empty repository page, click *"uploading an existing file"*, then drag in
   the **contents** of this folder — not the folder itself. Include the `assets` folder. Commit.

   Note: `.nojekyll` starts with a dot, so Windows may hide it. If it doesn't appear in the drag
   selection, turn on *View → Hidden items* in File Explorer.

4. **Turn on Pages.** Repository *Settings → Pages →* Source: *Deploy from a branch*, branch `main`,
   folder `/ (root)`. For a `username.github.io` repo this is usually on already.

5. Wait 1–5 minutes, then visit `https://yourusername.github.io`.

To make changes later you can click any file on github.com and edit it right in the browser — no
tools to install.

---

## Step 4 — Connect the contact form (optional)

The form works as soon as you connect it, and until then it tells visitors to email you instead, so
the page is never broken.

GitHub Pages only serves files — it can't run code, so it can't send email on its own. The usual free
fix is [Formspree](https://formspree.io):

1. Sign up (free tier: 50 messages/month, no card).
2. Create a new form. You'll get an ID that looks like `xaybqwer`.
3. In `index.html`, find `YOUR_FORM_ID` and replace it with yours:
   ```html
   <form ... action="https://formspree.io/f/xaybqwer" method="POST">
   ```
4. Submit the form once yourself — Formspree asks you to confirm your email on the first message.

Don't want another account? Delete the whole `<form>` block. The LinkedIn and email buttons above it
are enough.

---

## Privacy: what "public" actually means here

- **Anyone with the link can open the site.** There's no password option on free GitHub Pages.
- **The repository is public too**, so the raw files and PDFs can be downloaded directly.
- **`robots.txt` + the `noindex` tag** ask search engines to stay away, which is why your name won't
  turn up this page in Google. It's a request that well-behaved crawlers honour — not security.
  Someone who guesses the URL still gets in.

The practical rule: **treat everything you put here as permanently public.** If you wouldn't want a
stranger reading it, it doesn't go on the site or in a PDF.

**Want to be findable later?** Delete `robots.txt` and delete the `<meta name="robots" ...>` line
near the top of `index.html`. Takes ten seconds and is fully reversible.

---

## Later, if you want it

- **Your own domain** (`yourname.com`) — GitHub Pages supports custom domains for free; you just pay
  for the domain, roughly $15/year. Nothing here needs rebuilding.
- **Separate pages per project** — worth it once a project has enough images and detail to outgrow
  its card.
