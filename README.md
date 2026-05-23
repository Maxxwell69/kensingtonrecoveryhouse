# Kensington Recovery House

A static marketing site for **Kensington Recovery House**, a program of **First Stop Recovery** (501c3).

- **Stack**: plain HTML + CSS (zero build step)
- **Hosting**: Vercel (works out of the box — `vercel.json` enables clean URLs)
- **Forms / CRM**: GoHighLevel — embeds drop into the `<!-- GHL_FORM: ... -->` placeholders
- **Donate**: PayPal — replace `https://www.paypal.com/donate` links with the real donation URL
- **Maintained from**: Claude design (direct-edit safe — every page is self-contained HTML)

## Pages

| Route | File |
|---|---|
| `/` | `index.html` |
| `/about` | `about.html` |
| `/programs` | `programs.html` |
| `/start-your-journey` | `start-your-journey.html` |
| `/meeting-times` | `meeting-times.html` |
| `/events` | `events.html` |

## Deploy to Vercel via GitHub

1. Push this folder to a new GitHub repo.
2. In Vercel: **Add New > Project > Import Git Repository**, pick the repo.
3. **Framework Preset**: *Other* &middot; **Build Command**: *(leave blank)* &middot; **Output Directory**: *(leave blank — root)*.
4. Deploy. Done.

Each push to `main` redeploys automatically.

## Filling in GHL forms

Search the codebase for `<!-- GHL_FORM:` &mdash; each placeholder names the form it expects:

```
<!-- GHL_FORM: Contact -->
<!-- GHL_FORM: Intake -->
<!-- GHL_FORM: Referring Agency -->
<!-- GHL_FORM: Newsletter -->
<!-- GHL_FORM: Volunteer -->
```

Replace each one with the iframe / script GoHighLevel gives you when you publish that form. The `.ghl-slot` wrapper element is the placeholder UI &mdash; delete it once the real form is in.

## Filling in PayPal

Search for `paypal.com/donate` and replace with your real donate URL.

## Replacing photo placeholders

Look for `class="photo-placeholder"` &mdash; these are styled empty divs. To swap in a real photo:

```html
<!-- before -->
<div class="hero-photo photo-placeholder">Photo &mdash; Front door</div>

<!-- after -->
<div class="hero-photo" style="background-image: url('/photos/front-door.jpg'); background-size: cover; background-position: center;"></div>
```

Drop images into a `/photos` folder at the project root.

## Local preview

Open `index.html` in a browser, or run any static server:

```bash
npx serve .
# or
python3 -m http.server
```

## Editing from Claude

Open this project in Claude. Every page is one file. Edit copy directly in the chat preview or ask Claude to update any section &mdash; no build step, no JSX, no framework gotchas.
