# DevOps Portfolio - Alalzor

Professional portfolio for ASIR Technician specialized in DevOps and Systems Administration.

> **Note**: This is a continuation of the [portfoliok8s](https://github.com/Alalzor/Portfoliok8s) project. The portfolio has been migrated to GitHub Pages to free up server resources for other projects.

## 🚀 Tech Stack

- **Framework**: Astro 4.x
- **Styling**: Tailwind CSS  
- **Deployment**: GitHub Pages
- **Language**: TypeScript

## 📦 Features

- ✅ Responsive and professional design
- ✅ Optimized for production
- ✅ Ultra-fast static pages
- ✅ Easy to customize
- ✅ SEO optimized
- ✅ Real GitHub projects integration
- ✅ GitHub Pages ready

## 🛠️ Local Development

### Requirements

- Node.js 20+
- npm or pnpm

### Installation

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview build
npm run preview
```

Site will be available at `http://localhost:4321`

## 📁 Project Structure

```
/
├── public/          # Static assets
├── src/
│   ├── components/  # Reusable components
│   │   ├── home/    # Home page specific components
│   │   ├── About.astro
│   │   ├── Contact.astro
│   │   ├── Experience.astro
│   │   ├── Projects.astro
│   │   ├── Skills.astro
│   │   └── Certifications.astro
│   ├── layouts/     # Page layouts
│   ├── pages/       # Routes (file-based routing)
│   └── env.d.ts
└── package.json
```

## 🌐 Deploy to GitHub Pages

### Step 1: Configure Astro for GitHub Pages

The project is already configured for GitHub Pages deployment. The `astro.config.mjs` file is set to output static files.

### Step 2: Create GitHub Repository

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io.git
git push -u origin main
```

### Step 3: Configure GitHub Pages

1. Go to your repository settings on GitHub
2. Navigate to **Pages** section
3. Under **Source**, select **GitHub Actions**
4. Create `.github/workflows/deploy.yml` with the following content:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build
        run: npm run build
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Step 4: Push and Deploy

```bash
git add .github/workflows/deploy.yml
git commit -m "Add GitHub Pages deployment workflow"
git push
```

Your site will be available at `https://YOUR_USERNAME.github.io`

## 🛠️ Alternative Deploy Options

### Vercel
```bash
npm i -g vercel
vercel
```

### Netlify
```bash
npm i -g netlify-cli
netlify deploy
```

## 📝 Customization

### Personal Data

Update your information in these files:
- `src/components/home/Hero.astro` - Name and title
- `src/components/Contact.astro` - Contact information
- `src/components/Experience.astro` - Work experience
- `src/components/Projects.astro` - GitHub projects
- `src/components/Skills.astro` - Technical skills
- `src/components/Certifications.astro` - Certifications

### Colors & Themes

Tailwind configuration: `tailwind.config.mjs`

## 📄 License

MIT License - Feel free to use this template for your own portfolio!

## 👤 Author

**Alalzor**
- GitHub: [@Alalzor](https://github.com/Alalzor)
- LinkedIn: [Alalzor](https://www.linkedin.com/in/alalzor/)
