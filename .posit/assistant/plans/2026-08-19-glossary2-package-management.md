# Plan: Glossary2 — GitHub Contribution & Independent Package Management

**Situation:** You've forked and improved `glossary` (unmaintained original by Lisa DeBruine), renamed it `glossary2`, but it still carries the original author's metadata everywhere. You want to:
1. Contribute improvements back to the original repo
2. Maintain `glossary2` as an independent package on your GitHub

**Approach:** Honor the original author's work while establishing your own fork as a recognized community-maintained alternative.

---

## Phase 1: Publish `glossary2` as Your Maintained Fork + Parallel Upstream Contact

*(You will do both simultaneously: establish your fork while respectfully reaching out to the original author.)*

### 1.1 Proceed with `glossary2` Setup (This Week)
- Update package metadata (DESCRIPTION, README, etc.)
- Make it clear in repo description that this is a maintained fork
- Publish to GitHub as `glossary2`
- Goal: Have a working, documented fork ready for immediate use

### 1.2 Contact Lisa DeBruine About Your Fork & Improvements (Concurrent)

**Two-channel contact strategy:**

**Channel 1: GitHub Issue (Primary)**
- Open an issue on `debruine/glossary` summarizing:
  - Your maintained fork: `https://github.com/petzi53/glossary2`
  - Key improvements (especially the grep-matching bugfix)
  - Explain: unmaintained state of original, bugs you've fixed
  - Ask two things:
    1. Is she open to accepting a PR for the bugfixes?
    2. Is it okay that you're maintaining `glossary2` as a community fork?
  - Offer: If she wants, you can merge improvements back or work together
- **Tone:** Respectful, collaborative, not accusatory

**Channel 2: Email (Direct Contact)**
- If no response on GitHub after 2–3 weeks, send a professional email to: **lisa.debruine@glasgow.ac.uk**
- Subject: "Maintenance of glossary R package: Community fork with bugfixes"
- Content: Same message as GitHub issue, but more formal; include link to your fork
- This is her official university email, more likely to reach her than package comments

**Timeline & Outcome:**
- Send GitHub issue immediately after setting up `glossary2`; don't wait for response before publishing
- If no GitHub response after 2–3 weeks, follow up via email
- Outcomes:
  - If she responds positively: You can explore a PR, but your fork still stands as backup
  - If she doesn't respond: Your fork is already live; community benefits
  - If she re-engages: Be open to collaboration or even handing over maintenance

---

## Phase 2: Setup & Configuration of `glossary2` Repository

### 2.1 Update Package Metadata to Reflect Authorship

**DESCRIPTION file:**
- Add yourself as contributor/maintainer (you, not DeBruine)
- Update `Authors@R` to list DeBruine as original author (`"aut"` + `"cph"`) and yourself as maintainer/contributor
- Update `Package:` name to `glossary2` (if not already)
- Update URLs to point to your repo (`github.com/petzi53/glossary2`)
- Update BugReports to your repo
- Add comment in DESCRIPTION header to clarify this is a maintained fork
- Keep the CC BY 4.0 license (respect the original)

**Example structure:**
```r
Package: glossary2
Title: Glossaries for Markdown and Quarto Documents (Community-Maintained Fork)
Description: Add glossaries to markdown and quarto documents by tagging individual 
  words. Definitions can be provided inline or in a separate file. This is a maintained 
  fork of the original glossary package with bug fixes and enhancements.
Authors@R: c(
    person(
        given = "Lisa", 
        family = "DeBruine", 
        role = c("aut", "cph"),  # Original author + copyright holder
        email = "debruine@gmail.com",
        comment = c(ORCID = "0000-0002-7523-5539")
    ),
    person(
        given = "Peter",
        family = "Baumgartner",
        role = c("ctb", "cre"),  # Contributor + current maintainer
        email = "peter@baumgartner.de"
    )
)
License: CC BY 4.0
URL: https://github.com/petzi53/glossary2,
    https://github.com/debruine/glossary
BugReports: https://github.com/petzi53/glossary2/issues
```

### 2.2 Update README.md
- Rename README.md title to clarify fork status: `# glossary2: Community-Maintained Fork`
- Add prominent "About this fork" section (high in README):
  - Original author: Lisa DeBruine
  - Why fork exists: original package unmaintained for ~2 years; critical bugs need fixing
  - Key improvements you've made (link to specifics: grep-matching bugfix, etc.)
  - Clear statement: "This respects the original CC BY 4.0 license and DeBruine's copyright"
- Keep installation instructions pointing to your repo
- Keep link to original repo

**Example header (place near top):**
```markdown
# glossary2: Community-Maintained Fork

A maintained fork of the excellent [glossary](https://github.com/debruine/glossary) 
package by [Lisa DeBruine](https://github.com/debruine).

## About This Fork

The original `glossary` package is no longer actively maintained by Lisa DeBruine (no updates since 2023). 
This fork maintains the package with:
- **Critical bugfix:** Exact case-insensitive term matching (fixes #XX in original repo)
- **Enhanced functionality:** [link to improvements]
- **Community support:** Best-effort maintenance and issue responses

**Attribution:** This is a fork of Lisa DeBruine's work. The original package remains licensed under CC BY 4.0, 
and DeBruine is credited as the original author in all distributions.

**Maintenance note:** This is a community fork maintained on a best-effort basis. While issues and PRs 
are welcome, response times may be slow due to time constraints. If you need urgent support or want to 
contribute significantly, please consider the original repository or reach out via issues.

## Installation

Install from GitHub:
```r
devtools::install_github("petzi53/glossary2")
```
```

### 2.3 Add/Update NEWS.md
- Document what you've changed from upstream (the bugfixes, enhancements)
- Make it clear which improvements are yours vs. original

### 2.4 Update License/Attribution in Code
- Add comments at the top of key improved files acknowledging DeBruine's original work
- Example for `R/glossary.R` (top of file):
```r
# Improved version of glossary package (original by Lisa DeBruine)
# Key improvement: Fixed grep-based term matching to use exact case-insensitive match
# See: https://github.com/debruine/glossary/issues/XX
```

### 2.5 Create a CONTRIBUTING.md
- Acknowledge this is a community fork
- Explain contribution guidelines
- Note: significant changes may be proposed upstream first

---

## Phase 3: Repository Setup & Release

### 3.1 GitHub Repository Status
- **Already done:** Repository is already renamed to `glossary2` at `https://github.com/petzi53/glossary2/`
- **Verify local remote:** Confirm your local git remote points to the correct URL
  - Check: `git remote -v`
  - If needed, update: `git remote set-url origin https://github.com/petzi53/glossary2.git`

### 3.2 GitHub Repository Settings
- **Description:** "Community-maintained fork of glossary with bug fixes and enhancements"
- **Topics:** Add tags like `glossary`, `r-package`, `fork`, `quarto`, `rmarkdown`
- **Link to original:** Add upstream link in about section or pin an issue

### 3.3 Create Initial Release on GitHub
- Tag current version as release (e.g., `v1.0.1`)
- **Release notes should include:**
  - Clear statement of what's new/fixed in your fork
  - Link to original package
  - Installation instructions
  - Example: "First stable release of glossary2 with critical bugfixes"

### 3.4 Keep on GitHub Only (For Now)
- **Decision:** Do NOT submit to CRAN initially
  - Rationale: Keep relationship with original clear; avoid CRAN namespace issues
  - Users can still install easily: `devtools::install_github("petzi53/glossary2")`
  - If original maintainer re-engages, easier to merge back
  - Can revisit CRAN submission later with upstream coordination

### 3.5 Add "Differences from Upstream" Documentation
- Create a new section in README or separate `FORK_NOTES.md`
- List all substantive changes from `debruine/glossary`:
  - Grep-matching bugfix (main one)
  - Any enhancements you've added
  - Version number changes
  - Example section:
    ```markdown
    ## Differences from Upstream
    
    ### Bug Fixes
    - **Term matching fix:** Replaced substring grep matching with exact case-insensitive matching
      (fixes issue where "API" would match "Capital income")
    
    ### Enhancements
    - [List any additional features]
    
    ### Version
    - Upstream: v1.0.1
    - glossary2: v1.0.1+
    ```

---

## Phase 4: Ongoing Maintenance & Community Responsibility

- Monitor upstream (`debruine/glossary`) periodically for any activity
- If debruine returns and wants to re-engage, be open to merging back
- Maintain clear attribution (DeBruine's original contributions)
- Keep license CC BY 4.0 (non-negotiable)
- **Caveat:** This is a best-effort fork. You are not committing to intensive maintenance or rapid issue response due to time constraints and incomplete knowledge of the codebase. Users should understand this is a community fork, not an official product with guaranteed support.

---

## Ethical Guidelines (TL;DR)

✅ **Do:**
- Keep DeBruine's name, copyright, and license intact
- Clearly document improvements you made
- Use "fork" language in repo name/description
- Attempt good-faith contact before publishing independently
- Welcome merging back if original maintainer re-engages

❌ **Don't:**
- Remove or obscure attribution to DeBruine
- Change the license
- Claim you wrote the original code
- Ignore upstream if it suddenly becomes active again

---

## Implementation Timeline

**Week 1 (This week):**
1. ✅ Finalize this plan
2. Update DESCRIPTION (package name, authors, URLs, description)
3. Update README.md (fork header, installation, maintenance caveat)
4. Update or create FORK_NOTES.md (differences from upstream)
5. Run `devtools::check()` to ensure package is clean
6. Verify local git remote points to `glossary2` repo
7. Push changes to GitHub
8. Create GitHub release (v1.0.1)
9. **Send GitHub issue to Lisa DeBruine** on her repo (respectful, informative)

**Weeks 2–3:**
- Wait for GitHub response from DeBruine
- If no response by week 3, send email to lisa.debruine@glasgow.ac.uk

**Week 2+:**
- Monitor for response from DeBruine (no time pressure—you've already published)
- Best-effort maintenance: address issues when you can, but no guarantee of rapid response
- If DeBruine responds: evaluate collaboration options
- If no response: continue maintaining fork independently as community project

---

## Phase 5: Integration of Personal Glossaries (e.g., glossary-pb)

### 5.1 Purpose: What We're Doing

You have a personal glossary repository (`glossary-pb`) at `https://github.com/petzi53/glossary-pb`
with a `glossary.yml` file. The goal is to:

1. Make it easy for users to load your personal glossary from glossary2 (without depending on the original `glossary` package)
2. Host your glossary documentation independently on GitHub Pages (`https://petzi53.github.io/glossary-pb`)
3. Provide a discoverable registry or example in glossary2 docs so users know about your glossary

### 5.2 Architecture: Two Separate Repos

```
glossary2 (this repo)
├── R/ package code, helper functions
├── inst/glossary.yml (example bundled glossary)
└── docs/ (GitHub Pages site) ← Phase 6

glossary-pb (separate repo at https://github.com/petzi53/glossary-pb)
├── glossary.yml (your personal glossary)
├── docs/ (GitHub Pages site at https://petzi53.github.io/glossary-pb)
└── README.md (how to load into glossary2)
```

### 5.3 Implementation: Loading Remote Glossaries

The glossary2 package already supports loading glossaries from URLs via `glossary_load_all()`.
Users can load your glossary like this:

```r
library(glossary2)
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
```

**Option A (Current): Direct URL approach**
- Users provide full URL to raw YAML file
- Simplest, no changes needed to glossary2
- Works for any public glossary repository

**Option B (Future): Registry of known glossaries**
- Add a function `glossary_load_custom()` that accepts a shorthand (e.g., `glossary_load_custom("pb")`)
- Maps shorthand → URL internally
- Requires maintaining a registry in glossary2
- More user-friendly but adds maintenance burden

**Recommendation:** Start with Option A (direct URL). Users can copy the load command from your 
glossary-pb README. If multiple glossaries accumulate, consider Option B later.

### 5.4 Documentation for glossary-pb

Update your `glossary-pb` repository with clear documentation:

**README.md** should include:

```markdown
# glossary-pb: Personal Glossary for glossary2

My personal glossary for use with the [glossary2](https://github.com/petzi53/glossary2) package.

## Installation

The glossary is stored in `glossary.yml` in this repository.

### Method 1: Load from GitHub (No Local Installation)

```r
library(glossary2)
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")

# Now use glossary() as normal in your Quarto/R Markdown
```

### Method 2: Clone Repository Locally

```bash
git clone https://github.com/petzi53/glossary-pb.git
```

Then in your R code:
```r
library(glossary2)
glossary_load_all("path/to/glossary-pb/glossary.yml")
```

## Usage Example

```r
library(glossary2)
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
glossary_style("blue", "underline")

# In Quarto/R Markdown: `glossary("your_term")`
```

## Contributing

Issues and suggestions are welcome. Please open an issue or submit a PR.

## License

CC BY 4.0 (consistent with glossary2)

## See Also

- [glossary2](https://github.com/petzi53/glossary2) — The package that loads this glossary
```

### 5.5 Link glossary-pb from glossary2 Documentation

Update glossary2's README and docs to mention your glossary as an example:

**In glossary2 README.md**, add a section:

```markdown
## Third-Party Glossaries

You can load glossaries from external sources:

```r
# Example: Load Peter Baumgartner's personal glossary
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
```

See [glossary-pb](https://github.com/petzi53/glossary-pb) for a full example.
```

---

## Phase 6: Set Up Independent GitHub Pages Documentation for glossary2

### 6.1 Objective

Create standalone documentation at `https://petzi53.github.io/glossary2` that is **independent of 
the original `glossary` package** documentation. This establishes glossary2 as its own package with 
its own identity.

### 6.2 Architecture: pkgdown Website

You already have a `pkgdown/` directory. Here's how to set up GitHub Pages:

**Files to set up:**
- `pkgdown/_pkgdown.yml` — Site configuration (already exists; may need updates)
- `docs/` — Built site (generated by `pkgdown::build_site()`)
- `.github/workflows/pkgdown.yml` — GitHub Actions to auto-build on push

### 6.3 Implementation Steps

#### Step 1: Verify pkgdown Configuration

Check/update `pkgdown/_pkgdown.yml`:

```yaml
url: https://petzi53.github.io/glossary2
title: glossary2
description: Community-maintained fork of glossary with bug fixes
template:
  bootstrap: 5
  includes:
    in_header: |
      <meta property="og:description" content="Glossaries for Markdown and Quarto Documents (Community-Maintained Fork)">

reference:
  - title: "Main Functions"
    desc: >
      Core functions for adding glossaries to documents
    contents:
      - glossary
      - glossary_add
      - glossary_table
      - glossary_load_all
  - title: "Styling & Options"
    contents:
      - glossary_style
      - glossary_options
      - glossary_popup
      - glossary_persistent
      - glossary_path
  - title: "Quarto Integration"
    contents:
      - add_to_quarto

navbar:
  title: "glossary2"
  left:
    - text: "Home"
      href: "index.html"
    - text: "Reference"
      href: "reference/index.html"
    - text: "Articles"
      href: "articles/index.html"
    - text: "Fork Notes"
      href: "https://github.com/petzi53/glossary2/blob/main/FORK_NOTES.md"
  right:
    - icon: "fa-github"
      href: "https://github.com/petzi53/glossary2"
    - icon: "fa-book"
      href: "https://github.com/debruine/glossary"

home:
  title: glossary2 — Glossaries for Quarto & Markdown
```

#### Step 2: Build Site Locally

```r
pkgdown::build_site()
```

This generates `docs/` directory with the full website.

#### Step 3: GitHub Actions Workflow

Create `.github/workflows/pkgdown.yml` to auto-build on push:

```yaml
name: pkgdown

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  pkgdown:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v3
      - uses: r-lib/actions/setup-r@v2
      - uses: r-lib/actions/setup-pandoc@v2
      
      - name: Install dependencies
        run: |
          install.packages("pkgdown")
          install.packages(c("devtools", "knitr", "kableExtra", "markdown", "rvest", "xml2", "yaml"))
        shell: Rscript {0}
      
      - name: Build site
        run: pkgdown::build_site(override = list(destination = "docs"))
        shell: Rscript {0}
      
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./docs
```

#### Step 4: Enable GitHub Pages

In your GitHub repo settings:
1. Go to **Settings** → **Pages**
2. Under "Build and deployment", select:
   - Source: `GitHub Actions`
3. Save

The site will deploy automatically on next push.

### 6.4 Customize Landing Page

Create or update `README.md` to be inviting. This gets rendered as the homepage. Key elements:

- Brief intro (what glossary2 does)
- Installation (quick copy-paste)
- Quick example
- Link to full documentation
- Fork information (transparent about being a fork)

---

## Phase 7: Cross-Linking Between Packages

### 7.1 Glossary2 Documentation Should Mention glossary-pb

In the glossary2 site docs/README, add section:

```markdown
## Example: Third-Party Glossaries

You can load external glossaries from any public GitHub repository:

**Example:** Load Peter Baumgartner's personal glossary
```r
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
```

[View glossary-pb on GitHub](https://github.com/petzi53/glossary-pb)
```

### 7.2 Glossary-pb Should Link Back to glossary2

Ensure glossary-pb's README clearly links to glossary2 as the required package.

---

## Key Decision Points (Already Answered)

✅ **Contact approach:** Publish fork first, contact DeBruine in parallel (not sequential)
✅ **Package name:** Keep `glossary2`
✅ **Distribution:** GitHub-only (not CRAN yet)
✅ **Personal glossary integration:** URL-based loading (Option A) to start; Option B later if needed
✅ **Documentation site:** pkgdown via GitHub Actions + GitHub Pages at `petzi53.github.io/glossary2`

---

## Summary of Actions

| File/Area | Change | Status |
|-----------|--------|--------|
| DESCRIPTION | Add yourself as `ctb`/`cre`; update name, URLs | ⏳ Pending |
| README.md | Add fork header, attribution, installation, maintenance caveat | ⏳ Pending |
| FORK_NOTES.md | New file documenting differences | ✅ Done |
| GitHub repo (glossary2) | Already renamed ✅ | ✅ Done |
| Git remote | Verify points to glossary2 repo | ⏳ Pending |
| devtools::check() | Verify clean build | ⏳ Pending |
| GitHub Release | Tag v1.0.1 with fork notes | ⏳ Pending |
| Contact DeBruine | GitHub issue → Email (if no response) | ⏳ Pending |
| pkgdown/_pkgdown.yml | Update to customize site | ⏳ Pending |
| .github/workflows/pkgdown.yml | Create GitHub Actions workflow | ⏳ Pending |
| GitHub Pages settings | Enable GitHub Actions deployment | ⏳ Pending |
| glossary-pb README | Add load instructions for glossary2 | ⏳ Pending (separate repo) |
| glossary2 README/docs | Link to glossary-pb as example | ⏳ Pending |

