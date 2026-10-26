# Structured Products

**Structured Products Research & Analytics** — a GitHub Pages-ready static research site.

## Site map

| Path | Description | Status |
| --- | --- | --- |
| `index.html` | Landing page and navigation | Ready |
| `els-comparison/index.html` | **Final supplied `ELS_Map.html`**, used unchanged | Ready for static deployment |
| `pricing/index.html` | Separate future structured-products pricing area | Roadmap only (no pricing engine) |
| `data/` | Reserved for optional future external market/ELS datasets | Not connected |
| `scripts/` | Reserved for future data preprocessing and Python pricing source | Not implemented |

### ELS comparison functionality

The supplied HTML includes an embedded reference dataset and interfaces for KI mapping, issuer comparisons, and product search. Its chart library and fonts are loaded from external CDNs. No Node.js build or server-side code is required.

The comparison HTML is preserved **byte-for-byte** from the latest uploaded `ELS_Map.html`. No business logic, pricing assumptions, or embedded data were changed while packaging.

**Manual data update:** The current supplied HTML embeds its dataset inside the file. Its navigation hides data management/upload controls, and any IndexedDB-based locally loaded data is browser-specific. Therefore **uploading a file inside one browser does not update what other visitors see**. For a universally visible manual refresh *without modifying the application*, replace `els-comparison/index.html` in GitHub with a freshly regenerated `ELS_Map.html` containing the updated embedded dataset. Later development could extract data into versioned `data/*.json` files and implement `fetch()` loading.

### Pricing

The `/pricing/` URL is a clearly labeled roadmap page; it does **not** calculate ELS PV, early-redemption probabilities, Greeks, or risk measures. Do not interpret a future interface or any hidden legacy controls as a validated valuation model.

## Publish to GitHub Pages

1. Create an empty GitHub repository called `Structured-Products` (do **not** pre-add a README, .gitignore, or license).
2. Extract this ZIP. Open Command Prompt in the **`Structured-Products-Final`** folder.
3. Install `git` and [GitHub CLI](https://cli.github.com/) if needed, then run:

```bat
gh auth login
git init -b main
git add .
git commit -m "Initialize Structured Products research site"
gh repo create Structured-Products --public --source=. --remote=origin --push
```

If you already created the remote repository, skip the `gh repo create ...` step and use `git remote add origin https://github.com/YOUR_USERNAME/Structured-Products.git` then `git push -u origin main`.

4. GitHub repository **Settings > Pages > Build and deployment > Deploy from a branch > main > /(root) > Save**.
5. Open `https://YOUR_USERNAME.github.io/Structured-Products/`. The comparison page is `/Structured-Products/els-comparison/`, pricing is `/Structured-Products/pricing/`.

If the repository is public, the HTML and embedded reference dataset are **publicly downloadable**.

## Local preview

From the repository folder:

```bat
python -m http.server 8000
```

Open `http://localhost:8000/`. The comparison page requires network access for its chart and font CDNs.

## Disclaimer

This project is for research and educational use. ELS and other structured products entail material downside risk, and the HTML's disclosures/data may be incomplete or outdated. Independently check the issuer prospectuses, issue notices, and original regulatory filings before interpreting or using numbers.
