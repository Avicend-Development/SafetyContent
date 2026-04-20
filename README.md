# Aviation Safety Frameworks — Static Website

Twenty-five A4 two-pagers covering aviation safety frameworks, wrapped in a static site with a dropdown navigation menu. Each document explains the model, its use, benefits, limitations, cross-domain notes, APA 7 references, and further reading.

## What's in this repo

| File | Purpose |
| --- | --- |
| `index.html` | Site shell — header, dropdown menu, iframe viewer, hash routing |
| `overview.html` | Landing grid of framework cards (embedded inside `index.html`) |
| `<FRAMEWORK>.html` | One print-ready A4 two-pager per framework |
| `.nojekyll` | Tells GitHub Pages to serve files as-is (no Jekyll processing) |

### Framework catalog (25)

Classical barrier & defence-in-depth models — `SWISS-CHEESE`, `HDL-REASON`, `HDL-HOLLNAGEL`, `BOWTIE`
Systems & management risk models — `STAMP`, `BORA`, `ARAMIS`, `I-RISK`, `SAM`, `HCL`
Cognitive control & resilience (Hollnagel) — `COCOM`, `CREAM`, `ECOM`, `ETTO`, `FRAM`, `SAFETY-I-II`, `RESILIENCE`
Theoretical & sociological perspectives — `NORMAL-ACCIDENTS`, `HRO`
Risk concept & quantification — `ACU`, `ISO31000`, `RISK-MATRIX`, `FAIR`
Operational programmes — `SMS`, `FRMS`

## Run it locally

Because `index.html` loads the framework pages in an iframe, browsers need files served over HTTP rather than `file://`.

```bash
# From this folder
python3 -m http.server 8080
# then open http://localhost:8080/
```

Any static server (`npx serve`, `php -S`, nginx, …) works.

## Deploy to GitHub Pages

1. Create a new GitHub repository (public or private — Pages is free for public repos).
2. Commit the contents of this folder at the repo root:
   ```bash
   git init
   git add .
   git commit -m "Add Aviation Safety Frameworks static site"
   git branch -M main
   git remote add origin https://github.com/<your-user>/<your-repo>.git
   git push -u origin main
   ```
3. In the repo, open **Settings → Pages**.
4. Under **Build and deployment**, set **Source = Deploy from a branch**, **Branch = main**, **Folder = / (root)**. Click **Save**.
5. Wait ~30–60 seconds. Your site will be live at:
   `https://<your-user>.github.io/<your-repo>/`

### Custom domain (optional)

Add a `CNAME` file containing your domain (`safety.example.com`) in the repo root, then configure the DNS record as documented in GitHub's Pages docs.

### Why `.nojekyll`?

GitHub Pages runs Jekyll on uploaded content by default, which skips files and folders starting with `_` or `.`. The empty `.nojekyll` file disables that — guaranteeing every HTML file here is published verbatim.

## Deep links

The shell uses URL hashes so individual framework pages can be linked directly:

- `https://<your-site>/#STAMP.html`
- `https://<your-site>/#HRO.html`
- `https://<your-site>/#SWISS-CHEESE.html`

`#home` (or no hash) returns to the overview grid.

## Printing

Every framework page is designed around `@page { size: A4; margin: 0 }` and produces a clean two-page PDF. Use the **Print** button in the header or `Ctrl/Cmd + P` while a framework is open. The shell chrome is hidden automatically in print stylesheets.

## License / attribution

These documents are summaries for educational use. All primary sources are cited in APA 7 format on the second page of each two-pager. Respect the copyrights of the underlying books, standards, and articles when redistributing.
