# Valley Aircraft Restoration Society — website

A plain static site. No build step, no framework, no JavaScript. Every page is a
single `.html` file that links to one stylesheet.

## Files

```
index.html         Home
about.html         About
join.html          Join
history.html       History — the club story and the archival gallery
photographs.html   Photographs
video.html         Video — empty for now, waiting on footage
for-members.html   Reservations and dues
contact.html       Contact form
thanks.html        Shown after the contact form is submitted
css/style.css      All styling (colors live in the :root block at the top)
images/            Site images. hero.jpg is the big homepage photo.
images/gallery/    Photographs page images
images/history/    History page archival images
```

## Editing

Open any `.html` file in a text editor. The navigation appears at the top of
every page — if you add or rename a page, the nav list has to be updated in
every file.

## Preview locally

Double-click `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000

## Before going live

Two things in `contact.html` must be changed:

1. **The Web3Forms access key.** It is currently the placeholder
   `REPLACE-WITH-YOUR-WEB3FORMS-ACCESS-KEY`. Get a real one free at
   <https://web3forms.com> — enter the address that should receive enquiries and
   the key is emailed straight back. Paste it into the `access_key` field.
   Until this is done the form will not deliver anything.
2. **The redirect URL.** It currently points at `varsflyingclub.org`. Change it
   to whatever the final domain turns out to be.

The access key is not a secret — it only says where to deliver mail.

## Images

- **Hero** — `images/hero.jpg`, the photo behind the club name on the home page.
  Replace that file with another wide landscape shot (~1600px) to change it.
- **Galleries** — each photograph needs two files with the *same name*: the
  display version in `images/gallery/` (or `images/history/`) and a smaller copy
  in the matching `thumb/` folder. The page shows the thumbnail and links to the
  larger one. To add one, copy an existing `<figure>` block in the page.

Images here are deliberately reduced for the web. The full-resolution originals
— all 290 of them, 225 MB — are archived outside this repository. Don't commit
camera files; they make the repo huge and the pages slow.

To prepare new photos (ImageMagick):

```bash
magick photo.jpg -auto-orient -resize 1600x1600\> -strip -quality 82 images/gallery/name.jpg
magick photo.jpg -auto-orient -resize 700x700\>   -strip -quality 80 images/gallery/thumb/name.jpg
```

## External services

Nothing here runs on a server. Three things live elsewhere:

- **Scheduling** — [AircraftClubs](https://www.aircraftclubs.com), linked from
  the navigation and the For Members page.
- **Membership application** — a Google Form, linked from the Join page.
- **Contact form** — posts to Web3Forms, which emails each submission on.
