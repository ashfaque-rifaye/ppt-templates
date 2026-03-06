# ppt-templates

A repo for PPT templates.

## How to Upload PPT Templates

This repository uses **Git Large File Storage (LFS)** to handle large binary files like `.ppt` and `.pptx` templates. Follow the steps below to push your templates successfully.

### Prerequisites

1. **Install Git LFS** on your machine:
   - **macOS**: `brew install git-lfs`
   - **Windows**: Download from [git-lfs.github.com](https://git-lfs.github.com)
   - **Linux (Debian/Ubuntu)**: `sudo apt-get install git-lfs`

2. **Enable Git LFS** for your Git installation (run once per machine):
   ```bash
   git lfs install
   ```

### Steps to Add a New Template

1. **Clone the repository** (if you haven't already):
   ```bash
   git clone https://github.com/ashfaque-rifaye/ppt-templates.git
   cd ppt-templates
   ```

2. **Copy your PPT/PPTX file** into the `templates/` folder:
   ```bash
   cp /path/to/your-template.pptx templates/
   ```

3. **Stage, commit, and push**:
   ```bash
   git add templates/your-template.pptx
   git commit -m "Add your-template.pptx"
   git push origin main
   ```

   Git LFS will automatically handle the large binary file — no extra steps needed after the initial setup.

### File Types Tracked via Git LFS

| Extension | Description |
|-----------|-------------|
| `.ppt`    | PowerPoint 97–2003 Presentation |
| `.pptx`   | PowerPoint Presentation |
| `.pot`    | PowerPoint 97–2003 Template |
| `.potx`   | PowerPoint Template |
| `.pdf`    | PDF Document |
| `.png` / `.jpg` / `.jpeg` / `.gif` | Images |
| `.zip`    | ZIP Archives |

### Troubleshooting

- **"this exceeds GitHub's file size limit"** — Make sure you have run `git lfs install` before committing. If you already committed without LFS, use `git lfs migrate import --include="*.pptx"` to migrate.
- **Push rejected** — Ensure you have write access to the repository. Contact the repository owner if needed.
- **LFS quota exceeded** — GitHub Free accounts have 1 GB of LFS storage and 1 GB/month of bandwidth. Consider compressing templates or using GitHub's paid plans for more storage.

