# HTMLSnip

Free HTML snippet hosting — embeds that work in Canva.

---

## Deploy in 5 minutes

### Step 1 — Replace YOUR_USERNAME

Find and replace `YOUR_USERNAME` with your actual GitHub username across all files.

Files to update:

- `index.html`
- `p/countdown/index.html`
- `p/animated-bg/index.html`
- `p/particles/index.html`
- `oembed/countdown.json`
- `oembed/animated-bg.json`
- `oembed/particles.json`

Quick way on Mac/Linux:

```bash
find . -type f \( -name "*.html" -o -name "*.json" \) \
  -exec sed -i 's/YOUR_USERNAME/youractualusername/g' {} +
```

### Step 2 — Create the GitHub repo

1. Go to github.com → New repository
2. Name it exactly: `htmlsnip`
3. Set it to **Public**
4. Don't add README (you already have one)

### Step 3 — Push the code

```bash
cd htmlsnip
git init
git add .
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/htmlsnip.git
git push -u origin main
```

### Step 4 — Enable GitHub Pages

1. Go to your repo → Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: **main** → **/ (root)**
4. Click Save

Wait ~60 seconds. Your site is live at:
`https://Made4Uo/gigglegoogle/sample`

### Step 5 — Test iframely

Go to: https://debug.iframely.com

Paste in: `https://Made4Uo/gigglegoogle/samplep/countdown/`

If it shows an embed preview → you're ready to submit to iframely.
If it shows "summary card only" → the JSON serving needs a Content-Type fix (see below).

---

## Fix: GitHub Pages JSON Content-Type

GitHub Pages may serve `.json` files without the correct `Content-Type: application/json` header,
which can cause iframely to not parse the oEmbed endpoint correctly.

**Workaround:** Rename your oEmbed files to `.html` and serve them as HTML with a JSON body,
OR use a `_headers` file if you switch to Netlify (which respects custom headers).

The easiest fix is to just submit to iframely and let their team handle the parsing —
they have fallbacks for this exact situation.

---

## Submit to iframely

Once the site is live with real content:

1. Go to: https://iframely.com/qa/request
2. Fill in the form
3. Select: "I am requesting to add myself as a publisher"
4. Provide these example URLs:
   - `https://Made4Uo/gigglegoogle/samplep/countdown/`
   - `https://Made4Uo/gigglegoogle/samplep/animated-bg/`
   - `https://Made4Uo/gigglegoogle/samplep/particles/`
5. Describe it as: "A free HTML snippet hosting platform. Each snippet is user-generated HTML/CSS/JS with a clean embeddable URL and oEmbed endpoint."

---

## Adding new snippets

1. Create a new folder: `p/your-snippet-name/`
2. Add `index.html` with your HTML — copy the structure from an existing snippet
3. Add `oembed/your-snippet-name.json` — copy and update an existing JSON file
4. Add the snippet card to `index.html`'s gallery grid
5. `git add . && git commit -m "Add snippet" && git push`

Done — live in ~30 seconds.
