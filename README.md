# kanishblog

This repository contains the source code and automation setup for my personal blog, [**blog.kanishdangol.com**](https://blog.kanishdangol.com).

The blog is built with [Hugo](https://gohugo.io) and automated using PowerShell and Python.  
It was originally created to document my progress and reflections while working on my **Senior Design project**, and has since expanded to include posts about technology, cybersecurity, and personal learning.

---

## Overview

- **Static site generator:** Hugo  
- **Content editor:** Obsidian  
- **Hosting:** GitHub Pages (via the `hostinger` branch)  
- **Automation:** PowerShell + Python  

The workflow allows me to write posts in Obsidian, then run a single PowerShell command to:
1. Copy and sync markdown posts from my Obsidian vault  
2. Process embedded images and convert Obsidian-style links to Hugo-compatible Markdown  
3. Build the Hugo site locally  
4. Commit and push all source changes to GitHub  
5. Deploy the generated site to the live hosting branch  

---

## File Structure

kanishblog/
├── archetypes/ # Default content templates
├── content/posts/ # Markdown blog posts
├── static/images/ # Static image assets for posts
├── public/ # Hugo-generated static site output
├── themes/ # Hugo theme submodule
├── images.py # Python script for image handling and markdown link conversion
├── updateblog.ps1 # PowerShell script for syncing, building, and deploying the blog
├── hugo.toml # Hugo configuration file
└── .gitmodules # Theme submodule tracking


---

## Automation Details

### images.py
This Python script scans all Markdown files in the `content/posts` directory, detects embedded image links in Obsidian’s `[[image.png]]` format, converts them to proper Markdown syntax, and copies the referenced images from the Obsidian attachments folder to Hugo’s `static/images/` directory.

### updateblog.ps1
A PowerShell deployment script that:
- Syncs posts from the Obsidian folder to the Hugo `content/posts` directory  
- Executes `images.py` to fix image links  
- Builds the site with Hugo  
- Commits and pushes all updates to the `master` branch  
- Deploys the generated `public/` folder to the `hostinger` branch for production hosting  

Running this single script keeps the entire blog in sync and live within seconds.

---

## Deployment

To publish updates:
```powershell
.\updateblog.ps1
```
This will:

 - Pull new posts from Obsidian
 - Process images
 - Build the site
 - Push both source and production files to GitHub

My site will then be live at:
blog.kanishdangol.com
