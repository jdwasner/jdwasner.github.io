# Data Science Portfolio Website

A professional Jekyll-based portfolio website for showcasing data science projects, hosted on GitHub Pages.

## 🌟 Features

- **Dark Mode Theme**: Professional dark theme optimized for data science content
- **Responsive Design**: Mobile-friendly layout that works on all devices
- **Project Showcase**: Dedicated pages for detailed project documentation
- **Math Support**: MathJax integration for displaying equations
- **Syntax Highlighting**: Beautiful code highlighting for multiple languages
- **SEO Optimized**: Built-in SEO support with jekyll-seo-tag
- **Fast Loading**: Optimized assets and efficient Jekyll configuration

## 📁 Site Structure

```
jdwasner.github.io/
├── _config.yml              # Jekyll configuration
├── _layouts/                # Custom layouts
│   ├── default.html        # Main layout with navigation
│   └── project.html        # Layout for project pages
├── _projects/              # Project collection
│   ├── customer-churn-prediction.md
│   ├── sales-forecasting.md
│   └── medical-image-classification.md
├── assets/
│   ├── css/
│   │   └── style.scss      # Custom dark mode styling
│   ├── images/             # Project images and visualizations
│   │   └── projects/       # Organized by project
│   └── resume/             # Resume PDF location
├── index.md                # Homepage
├── about.md                # About page
├── projects.md             # Projects listing page
└── README.md               # This file
```

## 🚀 Getting Started

### Prerequisites

- Ruby 2.7 or higher
- RubyGems
- GCC and Make

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/jdwasner/jdwasner.github.io.git
   cd jdwasner.github.io
   ```

2. **Install Jekyll and dependencies**
   ```bash
   gem install bundler jekyll
   bundle install
   ```

3. **Run the local server**
   ```bash
   bundle exec jekyll serve
   ```

4. **View the site**
   Open your browser to `http://localhost:4000`

### Alternative: Using Docker

```bash
docker run --rm -v "$PWD:/srv/jekyll" -p 4000:4000 jekyll/jekyll jekyll serve
```

## 📝 Content Management

### Adding a New Project

1. **Create a new markdown file** in the `_projects/` directory:
   ```bash
   touch _projects/my-new-project.md
   ```

2. **Add front matter and content**:
   ```markdown
   ---
   layout: project
   title: "Your Project Title"
   date: 2024-12-27
   description: "Brief description of your project"
   technologies:
     - Python
     - TensorFlow
     - Pandas
   github: "https://github.com/yourusername/project-repo"
   demo: "https://your-demo-link.com"
   ---

   ## Project Overview
   Your detailed project content here...
   ```

3. **Add images** to `assets/images/projects/your-project-name/`

4. **Reference images** in your markdown:
   ```markdown
   ![Description](../assets/images/projects/your-project-name/image.png)
   *Figure 1: Your caption here*
   ```

### Updating Personal Information

Edit `_config.yml` to update:
- Site title and description
- Author information
- Social media links
- Navigation menu

```yaml
# Site Settings
title: "Your Name - Data Science Portfolio"
description: "Your custom description"

# Author Information
author:
  name: "Your Name"
  email: "your.email@example.com"
  github: "yourgithub"
  linkedin: "yourlinkedin"
```

### Adding Your Resume

1. Place your resume PDF in `assets/resume/`
2. Name it `resume.pdf`
3. The download buttons will automatically link to it

See `assets/resume/README.md` for detailed instructions.

### Updating the About Page

Edit `about.md` to customize:
- Professional background
- Skills and expertise
- Education
- Work experience
- Certifications

### Modifying the Homepage

Edit `index.md` to change:
- Welcome message
- Featured projects display
- About section
- Contact information

## 🎨 Customization

### Theme Colors

Edit color variables in `assets/css/style.scss`:

```scss
:root {
    --bg-primary: #0d1117;      /* Main background */
    --bg-secondary: #161b22;    /* Card backgrounds */
    --text-primary: #e6edf3;    /* Main text */
    --accent-primary: #58a6ff;  /* Links and highlights */
    /* ... more variables */
}
```

### Navigation Menu

Edit `_config.yml`:

```yaml
navigation:
  - title: "Home"
    url: /
  - title: "Projects"
    url: /projects
  - title: "About"
    url: /about
  - title: "Blog"      # Add new pages
    url: /blog
```

### Adding New Pages

1. Create a new markdown file (e.g., `blog.md`)
2. Add front matter:
   ```markdown
   ---
   layout: default
   title: Blog
   permalink: /blog/
   ---
   ```
3. Add to navigation in `_config.yml`

## 📊 Adding Visualizations

### Matplotlib Example (Dark Theme)

```python
import matplotlib.pyplot as plt

# Use dark background
plt.style.use('dark_background')

# Create your plot
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y)
ax.set_title('Your Title')

# Save with transparent or dark background
plt.savefig('plot.png', dpi=300, bbox_inches='tight',
            facecolor='#1c2128', edgecolor='none')
```

### Including Plots in Projects

```markdown
![Performance Metrics](../assets/images/projects/my-project/metrics.png)
*Figure 1: Model performance across different metrics*
```

## 🔧 Advanced Configuration

### Adding Mathematical Equations

Use LaTeX syntax with MathJax (already configured):

**Inline math**: `$E = mc^2$` renders as $E = mc^2$

**Display math**:
```latex
$$
\hat{y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \epsilon
$$
```

### Code Syntax Highlighting

Use fenced code blocks with language specification:

````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

Supported languages: Python, R, SQL, JavaScript, Java, C++, and more.

### Custom Layouts

Create new layouts in `_layouts/` directory:

```html
---
layout: default
---
<div class="custom-content">
    {{ content }}
</div>
```

## 🌐 Deployment

### GitHub Pages Deployment

This site is configured for GitHub Pages and will automatically deploy when you push to the repository.

1. **Enable GitHub Pages**:
   - Go to repository Settings
   - Navigate to Pages section
   - Source: Deploy from a branch
   - Branch: `main` (or `master`)
   - Folder: `/ (root)`

2. **Push your changes**:
   ```bash
   git add .
   git commit -m "Update portfolio"
   git push origin main
   ```

3. **Access your site**:
   - Your site will be live at `https://jdwasner.github.io`
   - Usually takes 1-2 minutes to deploy

### Custom Domain (Optional)

1. Add a `CNAME` file to the repository root:
   ```
   yourdomain.com
   ```

2. Configure DNS settings with your domain provider:
   - Add A records pointing to GitHub Pages IPs
   - Or add a CNAME record pointing to `yourusername.github.io`

3. Enable HTTPS in repository settings

See [GitHub Pages documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site) for details.

## 🔍 SEO Optimization

The site includes SEO optimization through `jekyll-seo-tag`. Enhance it by:

1. **Adding metadata to pages**:
   ```yaml
   ---
   title: Your Page Title
   description: Your page description
   image: /assets/images/preview.png
   ---
   ```

2. **Creating a sitemap** (automatic with GitHub Pages)

3. **Adding robots.txt**:
   ```
   User-agent: *
   Allow: /
   Sitemap: https://jdwasner.github.io/sitemap.xml
   ```

## 📱 Testing

### Responsive Design Testing

Test on multiple screen sizes:
- Desktop: 1920x1080, 1366x768
- Tablet: 768x1024
- Mobile: 375x667, 414x896

### Browser Compatibility

Tested on:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

### Local Testing Commands

```bash
# Serve with drafts
bundle exec jekyll serve --drafts

# Serve with future posts
bundle exec jekyll serve --future

# Build only (no server)
bundle exec jekyll build

# Check for errors
bundle exec jekyll doctor
```

## 🐛 Troubleshooting

### Jekyll Won't Start

```bash
# Update dependencies
bundle update

# Clean the cache
bundle exec jekyll clean
```

### Images Not Displaying

- Check file paths are correct (case-sensitive)
- Verify images exist in `assets/images/`
- Ensure proper markdown syntax: `![alt](path)`

### Styling Issues

- Clear browser cache
- Check `assets/css/style.scss` for syntax errors
- Verify the theme is correctly specified in `_config.yml`

### Build Failures on GitHub Pages

- Check the Actions tab for build logs
- Ensure only GitHub Pages compatible plugins are used
- Verify `_config.yml` syntax is correct

## 📚 Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)
- [MathJax Documentation](https://www.mathjax.org/)
- [Liquid Template Language](https://shopify.github.io/liquid/)

## 🤝 Contributing

This is a personal portfolio, but feel free to:
- Fork this repository for your own portfolio
- Submit issues for bugs or suggestions
- Create pull requests for improvements

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 📧 Contact

- **GitHub**: [@jdwasner](https://github.com/jdwasner)
- **LinkedIn**: [jdwasner](https://linkedin.com/in/jdwasner)
- **Email**: contact@example.com

---

Built with ❤️ using [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://pages.github.com/)
