# CTF Writeups

CTF writeups collection built with MkDocs Material and deployed via GitHub Pages.

## 🚀 Quick Start

### Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Serve locally
mkdocs serve
```

Visit `http://127.0.0.1:8000`

### Writing in Obsidian

1. Write your writeups in Obsidian as usual
2. Use wiki-links `[[page-name]]` - they work automatically
3. Save files in the appropriate category folder:
   - `Cryptography/`
   - `Forensics/`
   - `Network/`

### Deploying

```bash
git add .
git commit -m "Add new writeup"
git push
```

GitHub Actions will automatically build and deploy to GitHub Pages.

## 📁 Structure

```
.
├── docs/                  # MkDocs source
│   ├── Cryptography/     # Crypto writeups
│   ├── Forensics/        # Forensics writeups
│   ├── Network/          # Network writeups
│   ├── assets/           # Images and files
│   └── stylesheets/      # Custom CSS
├── mkdocs.yml            # MkDocs configuration
└── .github/workflows/    # Auto-deployment
```

## 🎨 Features

- 🔍 Full-text search
- 🌓 Dark/Light mode
- 📱 Mobile responsive
- 🔗 Obsidian wiki-link support
- 💻 Syntax highlighting
- ⚡ Auto-deployment on push

## 🌐 Live Site

Visit: [https://drasogo.github.io/Write_Up/](https://drasogo.github.io/Write_Up/)
