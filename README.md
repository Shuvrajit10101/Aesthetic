# Aesthetic

Marketing website for THE AESTHETIC GYM, a gym on Kharar-Kurali Road in Kharar,
Punjab. `index.html` is one self-contained page: hero, about, six service cards,
a 20-photo gallery with lightbox, a member-review carousel, weekly gym hours,
contact details and an embedded Google map. The contact form has no backend — it
builds a pre-filled WhatsApp message and opens it.

`admin.html` is a second page for editing that content without touching the HTML
by hand. It is password-gated, keeps the content in the browser's `localStorage`,
and exports a regenerated `index.html` you can commit. Everything runs
client-side; there is no server, API or database anywhere in the repo.

The repo's homepage field points at https://aesthetic-site-tau.vercel.app, which
serves this page.

## Stack

- Plain HTML with one inline `<style>` and one inline `<script>` per page — no
  framework, no build step, no dependencies
- Vanilla JS: mobile nav, gallery lightbox (keyboard + touch), autoplaying review
  carousel, `IntersectionObserver` stat counters
- Google Fonts: Bebas Neue, DM Sans, Playfair Display
- `vercel.json`, which only sets the project name `aesthetic-site`

## Running it

Open `index.html` in a browser. Open `admin.html` the same way to edit content.
Nothing to install or compile.

## Structure

```
index.html     the public page
admin.html     content editor; writes localStorage, exports a new index.html
images/        20 gallery photos
logo/          logo_transparent.png and a photo
vercel.json
```

## Editing content

Two ways, both fine:

- Edit `index.html` directly.
- Open `admin.html`, change the fields (hero, about, stats, services, gallery,
  reviews, schedule, contact, social links, CTA, footer), hit Preview, then
  Export and replace `index.html` with the downloaded file.

Note that the `admin.html` login is client-side only — it compares a SHA-256 hash
held in `localStorage`. It keeps a casual visitor out of the editor UI; it is not
server-side access control, and the exported file is the only thing that changes
the live site.
