# ppt-templates

A repo for PPT templates. Large binary files (`.ppt`, `.pptx`, images, etc.) are stored with **Git LFS** so they don't bloat the repository history.

---

## ⬆️ How to upload a template (choose one method)

### Method 1 — Upload via the GitHub website (works right now, no setup needed) ✅

> **Best for files up to 25 MB.** No Git, no command line, no merging required.

1. Navigate to the **`templates/`** folder in this repository:
   [📁 Browse templates/](../../tree/main/templates)

2. Click **"Add file"** → **"Upload files"**

3. Drag and drop your `.pptx` (or any other template file) onto the page, or click **"choose your files"** to browse.

4. Scroll down to **"Commit changes"**, enter a description (e.g. `"Add Q1 roadmap deck"`), and click **"Commit changes"**.

That's it — the file is now in the repository. No terminal, no installation, no cloning.

---

### Method 2 — Upload via GitHub Actions (for any file size, including large files)

> **Best for files larger than 25 MB**, because GitHub Actions commits via Git LFS which has a much higher limit.  
> ⚠️ **Requires this PR to be merged into `main` first.** Once merged, the workflow is available in the [Actions tab](../../actions/workflows/upload-template.yml).

**Steps (after this PR is merged):**

1. Host your file somewhere accessible with a **direct download link**:

   | Service | How to get a direct link |
   |---------|--------------------------|
   | **Google Drive** | Share → "Anyone with the link" → use `https://drive.google.com/uc?export=download&id=FILE_ID` |
   | **Dropbox** | Change `?dl=0` → `?dl=1` at the end of the share link |
   | **OneDrive** | Click the **Download** button; copy the URL from the address bar |
   | **Any other host** | Any URL that directly downloads the file when opened |

2. Go to **[Actions → Upload PPT Template](../../actions/workflows/upload-template.yml)** in this repository.

3. Click the **"Run workflow"** button (on the right-hand side of the page).

4. Fill in the form:

   | Field | Description |
   |-------|-------------|
   | **File URL** | Direct download URL from step 1 |
   | **File name** | Filename to save, e.g. `q1-roadmap.pptx` |
   | **Branch** | Branch to commit to (default: `main`) |
   | **Commit message** | Optional — auto-generated if left blank |

5. Click **"Run workflow"** — the runner downloads your file, stores it in `templates/` via Git LFS, and commits it automatically. Done in about 30 seconds.

---

### Method 3 — Command line (optional, for developers)

<details>
<summary>Click to expand command-line instructions</summary>

```bash
# 1. Install Git LFS (once per machine)
brew install git-lfs        # macOS
sudo apt-get install git-lfs # Ubuntu/Debian

# 2. Enable it
git lfs install

# 3. Clone, add your file, and push  (replace <YOUR_REPO_URL> with this repo's clone URL)
git clone <YOUR_REPO_URL>
cd ppt-templates
cp /path/to/your-template.pptx templates/
git add templates/your-template.pptx
git commit -m "Add your-template.pptx"
git push origin main
```

</details>

---

## File types tracked via Git LFS

| Extension | Description |
|-----------|-------------|
| `.ppt`    | PowerPoint 97–2003 Presentation |
| `.pptx`   | PowerPoint Presentation |
| `.pot`    | PowerPoint 97–2003 Template |
| `.potx`   | PowerPoint Template |
| `.pdf`    | PDF Document |
| `.png` / `.jpg` / `.jpeg` / `.gif` | Images |
| `.zip`    | ZIP Archives |

---

## Troubleshooting

- **I see the Actions tab but there's no "Run workflow" button** — GitHub only shows the "Run workflow" button for `workflow_dispatch` workflows when the workflow file exists on the **default branch** (`main`). This PR hasn't been merged yet, so the workflow isn't on main. Use **Method 1** (web upload) in the meantime, or ask the repository owner to merge this PR to enable Method 2.
- **Workflow fails with "Downloaded file is empty"** — Your URL isn't a direct download link. See the table in Method 2 above.
- **"this exceeds GitHub's file size limit"** — Files larger than 25 MB must be uploaded via Method 2 (Actions workflow) or Method 3 (command line with Git LFS).
- **Push rejected** — Ensure you have write access to the repository.
- **LFS quota exceeded** — GitHub Free accounts have 1 GB of LFS storage and 1 GB/month of bandwidth. Consider compressing templates or upgrading to a paid plan.

