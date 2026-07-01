# DealDesk — Landing Page

A single-file marketing landing page for DealDesk, an agency offering six AI
services to real estate agents: market intelligence, an AI voice receptionist,
AI listing video, an AI "twin" (cloned voice + likeness), listing syndication,
and hyperlocal SEO. A realtor scans the six sections and picks the services
they want via the selector at the bottom.

## Deploy (GitHub Pages)

Everything lives in `index.html`. There is no build step.

1. Commit `index.html` to the repo root and push.
2. Settings → Pages → Source: **Deploy from a branch**, choose your branch and
   `/ (root)`.
3. The page goes live at `https://<username>.github.io/<repo>/`.

To serve from a subfolder instead, put `index.html` in `/docs` and point Pages
at `/docs`.

## What's in the file

The page is self-contained. All CSS and JavaScript are inline, and the three
demo videos in the "AI Video Content" section are embedded directly as base64
data URIs, so there are no separate asset files to manage or lose.

The only external reference is Google Fonts (DM Serif Display and DM Sans) over
their CDN. It loads normally on any online host. With no internet the page falls
back to a system sans-serif and the layout stays intact.

## Editing the demo videos

The three clips are 5-second Seedance 2.0 generations, compressed to 360x640 and
embedded as data URIs on the three `<video>` elements in the section 3 `.thumbs`
block. To swap one, replace the `src="data:video/mp4;base64,..."` value with a
new base64-encoded MP4:

```bash
base64 -i new-clip.mp4 | tr -d '\n'
```

Then paste the output after `data:video/mp4;base64,` for the clip you want to
replace.

## Status

Proof of concept. Placeholder content still to replace before going live:
service pricing (only the $149/listing video figure is grounded), the fictional
"Walker Group" agent brand and demo data, and the lead form, which currently
shows a confirmation message but does not submit anywhere. Wire the form to a
real endpoint (Formspree, an n8n webhook, etc.) before collecting leads.
