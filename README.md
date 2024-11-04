#Static-Site
---

### 1. **README.md**

This file will serve as the main documentation for the repository.

```markdown
# Neon Covenant Blog

This repository contains the source code for the Neon Covenant Blog, a static website built using [Hugo](https://gohugo.io/). The blog covers topics related to nightlife, festivals, technology, and more. The site is automatically deployed to [GitHub Pages](https://pages.github.com/) using a GitHub Actions workflow.

## Features

- **SEO Optimized**: Includes meta tags for SEO, Open Graph, and Twitter Cards.
- **Fast & Lightweight**: Uses Hugo for blazing fast static site generation.
- **Automated Deployment**: GitHub Actions pipeline automates the deployment process to GitHub Pages.
- **Custom Domain**: Hosted at [https://blog.neoncovenant.com](https://blog.neoncovenant.com).

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Development](#development)
- [Deployment](#deployment)
- [Asset Management](#asset-management)
- [Contributing](#contributing)
- [License](#license)

## Installation

To install and run the project locally:

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/blog-neoncovenant.git
   cd blog-neoncovenant
   ```

2. Install Hugo:

   Follow the [Hugo installation guide](https://gohugo.io/getting-started/installing/) for your operating system.

3. Start the Hugo server:

   ```bash
   hugo server
   ```

   Visit `http://localhost:1313` to preview the site locally.

## Configuration

The Hugo configuration is located in the `config.toml` file. Update this file to customize metadata, SEO options, and other site-wide settings.

### Example `config.toml`:

```toml
baseURL = "https://blog.neoncovenant.com/"
languageCode = "en-us"
title = "Neon Covenant Blog"
theme = "your-theme"
enableRobotsTXT = true

[params]
  description = "Welcome to the Neon Covenant Blog"
  keywords = ["Neon Covenant", "Blog", "Nightlife", "Festivals", "Tech"]
  author = "Jesse Veils"
  twitterHandle = "@neoncovenant"
  opengraph = true
```

## Development

You can add new content to the blog by creating new markdown files in the `content/blog/` directory.

Example of creating a new blog post:

```bash
hugo new blog/my-first-post.md
```

## Deployment

Deployment is fully automated with GitHub Actions. Once you push changes to the `main` branch, the site will be automatically deployed to GitHub Pages. The configuration for the GitHub Actions workflow is located in `.github/workflows/gh-pages.yml`.

## Asset Management

- **Images**: Stored in `static/images/` or `content/uploads/images/`.
- **Documents**: Stored in `static/docs/` or `content/uploads/documents/`.

To include assets in blog posts:

```markdown
![Sample Image](uploads/images/sample-image.jpg)

[Download PDF](uploads/documents/sample-document.pdf)
```

## Contributing

We welcome contributions! Please read the [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on how to contribute to this project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
```

---

### 2. **Dependencies**

If you are using Python for automation, scripts, or any other dependency management tool, include a `requirements.txt` file. If no Python dependencies exist, you can skip this file.

#### **requirements.txt**
```plaintext
# Add any Python packages if required, e.g.
hugo-bin==0.77.0
```

This file would include any specific packages you use for testing, automation, etc. Since Hugo is a Go-based system, it may not require many Python dependencies unless you use custom scripts.

---

### 3. **Configuration Documentation**

#### **config.rst**

This `.rst` file will document the configuration parameters for your blog.

```rst
=======================
Neon Covenant Blog Config
=======================

This section explains the main configuration settings used for the Neon Covenant blog.

Base URL:
---------
The `baseURL` sets the main URL of your site.

Example:

    baseURL = "https://blog.neoncovenant.com/"

Metadata Settings:
-------------------
- **title**: Title of the site.
- **languageCode**: Language code, such as "en-us".
- **description**: A brief description of the blog.

SEO Configuration:
-------------------
- **enableRobotsTXT**: Set to true to enable robots.txt file generation.
- **opengraph**: Enable Open Graph for social sharing.

Content Configuration:
------------------------
- **params**: Custom parameters for the blog. This includes fields like `author`, `description`, and `keywords`.

Deployment Configuration:
--------------------------
The deployment settings are managed using GitHub Actions.
```

---

### 4. **Requirements Documentation**

#### **requirements.rst**

This `.rst` file provides information about the required dependencies and how to install them.

```rst
==================
Neon Covenant Blog Requirements
==================

This project uses the following tools:

Hugo:
-----
The Neon Covenant Blog is powered by [Hugo](https://gohugo.io/). You need to install Hugo to run the blog locally.

To install Hugo, follow the instructions here: https://gohugo.io/getting-started/installing/

GitHub Actions:
---------------
Deployment is automated via GitHub Actions. No additional manual setup is required once the actions are in place.

Optional Dependencies:
----------------------
If you plan to extend the functionality using Python scripts or other tools, install dependencies via `pip` using the `requirements.txt` file.

    pip install -r requirements.txt
```

---

### 5. **GitHub Actions Workflow (`.github/workflows/gh-pages.yml`)**

Ensure you have the workflow configured to deploy your blog automatically upon each push to the `main` branch.

```yaml
name: Deploy Hugo Blog to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'

      - name: Build site
        run: hugo --minify

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
          cname: blog.neoncovenant.com
```

This workflow file automates deployment to GitHub Pages every time you push to the `main` branch.

---

### 6. **Folder Structure**

To summarize, here's the structure for the static blog site:

```plaintext
.
├── content/              # Main content
│   ├── blog/             # Blog posts
│   └── uploads/          # Uploaded files (images, docs)
│       ├── images/
│       └── documents/
├── static/               # Static assets like CSS, JS, images
│   ├── images/           # Public images
│   ├── docs/             # Public documents
├── layouts/              # HTML layout files for themes
├── .github/              # GitHub Actions workflows
│   └── workflows/
│       └── gh-pages.yml  # GitHub Pages deployment workflow
├── config.toml           # Hugo configuration
├── README.md             # Project documentation
├── requirements.txt      # Dependencies (optional)
├── config.rst            # Configuration documentation
├── requirements.rst      # Requirements documentation
└── LICENSE               # Project license
```

---
