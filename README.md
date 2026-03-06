# ppt-templates

A repo for PPT templates. Large binary files (`.ppt`, `.pptx`, images, etc.) are stored with **Git LFS** so they don't bloat the repository history.

---

## ⬆️ Upload a Template — no local setup required

You can add a new template entirely from your browser using a built-in GitHub Actions workflow. No need to install Git, Git LFS, or clone the repo locally.

### Steps

1. **Host your file somewhere accessible** with a direct download link — Google Drive, Dropbox, OneDrive, or any public URL works (see [Getting a direct link](#getting-a-direct-download-link) below).

2. **Go to the Actions tab** of this repository, select **"Upload PPT Template"** in the left sidebar, then click **"Run workflow"** (top-right of the workflow table).

3. Fill in the form:

   | Field | Description |
   |-------|-------------|
   | **File URL** | Direct download URL of your file (see below) |
   | **File name** | The filename to save, e.g. `q1-roadmap.pptx` |
   | **Branch** | Branch to commit to (default: `main`) |
   | **Commit message** | Optional — auto-generated if left blank |

4. Click **"Run workflow"** — the runner downloads your file, stores it in `templates/` via Git LFS, and commits it automatically.

That's it. You'll see the new file in `templates/` once the workflow finishes (usually under a minute).

---

### Getting a direct download link

| Service | How to get a direct link |
|---------|--------------------------|
| **Google Drive** | Share the file → "Anyone with the link" → copy the file ID from the URL and use: `https://drive.google.com/uc?export=download&id=FILE_ID` |
| **Dropbox** | Use the share link and change `?dl=0` → `?dl=1` at the end |
| **OneDrive** | Click the **Download** button; copy the URL from your browser's address bar (it starts with `https://...download.aspx?...`) |
| **Any other host** | Any URL that downloads the file directly when opened in a browser |

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

## Uploading from the command line (optional)

If you prefer the command line, you'll need Git LFS installed locally:

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

---

## Troubleshooting

- **Workflow fails with "Downloaded file is empty"** — Your URL isn't a direct download link. See [Getting a direct link](#getting-a-direct-download-link) above.
- **"this exceeds GitHub's file size limit"** (command-line) — Run `git lfs install` before committing, then use `git lfs migrate import --include="*.pptx"` if you've already committed without LFS.
- **Push rejected** — Ensure you have write access to the repository.
- **LFS quota exceeded** — GitHub Free accounts have 1 GB of LFS storage and 1 GB/month of bandwidth. Consider compressing templates or upgrading to a paid plan.

