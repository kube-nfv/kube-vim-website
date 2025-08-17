# Kube-VIM Website

This repository contains the Hugo-based website for Kube-VIM, a Kubernetes-native NFV Virtual Infrastructure Manager.

## Local Development

### Prerequisites

- Hugo Extended v0.110.0+ ([installation guide](https://gohugo.io/installation/))
- Node.js 16+ and npm
- Git

### Setup

1. Clone the repository with submodules:
```bash
git clone --recursive https://github.com/kube-nfv/kube-vim-website.git
cd kube-vim-website
```

2. Install Node.js dependencies:
```bash
npm install
```

3. Start the development server:
```bash
hugo server --buildDrafts
```

The site will be available at `http://localhost:1313/`

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch.

### Manual Deployment

To build the site locally:

```bash
hugo --minify --environment production
```

The built site will be in the `public/` directory.

## Content Structure

- `content/` - Website content in Markdown
- `static/` - Static assets (images, CNAME, etc.)
- `themes/docsy/` - Docsy theme (git submodule)
- `hugo.yaml` - Hugo configuration

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally with `hugo server`
5. Submit a pull request

## Technology Stack

- **Static Site Generator**: Hugo with Docsy theme
- **Deployment**: GitHub Actions + GitHub Pages
- **Domain**: kubevim.kubenfv.io
- **CI/CD**: Automatic deployment on push to main

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.