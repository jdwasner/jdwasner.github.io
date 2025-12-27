# Jekyll Portfolio - Deployment Guide

## 🚀 Quick Start

Your Jekyll portfolio website is **ready to deploy**! Follow these steps to get it live on GitHub Pages.

## Step 1: Enable GitHub Pages

1. Go to your repository on GitHub: https://github.com/jdwasner/jdwasner.github.io
2. Click **Settings** (top menu)
3. Scroll down to **Pages** (left sidebar)
4. Under **Source**, select:
   - **Branch**: `main` (or `master`)
   - **Folder**: `/ (root)`
5. Click **Save**

Your site will be live at: **https://jdwasner.github.io** in 1-2 minutes!

## Step 2: Customize Your Site

### Update Personal Information

Edit `_config.yml`:

```yaml
title: "Data Science Portfolio - [Your Name]"
description: "Your custom description"

author:
  name: "Your Name"
  email: "your.email@example.com"
  github: "yourgithub"
  linkedin: "yourlinkedin"
```

### Add Your Resume

1. Place your resume PDF in: `assets/resume/resume.pdf`
2. Recommended size: Under 2MB
3. File name must be exactly: `resume.pdf`

### Update About Page

Edit `about.md` with your:
- Professional background
- Skills and expertise
- Education
- Work experience
- Certifications
- Contact information

## Step 3: Add Your Projects

### Option A: Modify Example Projects

Edit the existing project files in `_projects/`:
- `customer-churn-prediction.md`
- `sales-forecasting.md`
- `medical-image-classification.md`

Update:
- Project title and description
- GitHub repository URL
- Demo link (if applicable)
- Technologies used
- Content and visualizations

### Option B: Create New Projects

1. Create a new file in `_projects/` (e.g., `my-project.md`)
2. Add front matter:

```yaml
---
layout: project
title: "Your Project Title"
date: 2024-12-27
description: "Brief description"
technologies:
  - Python
  - TensorFlow
github: "https://github.com/yourusername/project"
demo: ""
---
```

3. Write your project content in Markdown

## Step 4: Add Project Images

1. Create a subdirectory: `assets/images/projects/your-project-name/`
2. Add your visualization images (PNG recommended)
3. Reference in your project markdown:

```markdown
![Description](../assets/images/projects/your-project-name/plot.png)
*Figure 1: Your caption*
```

### Tips for Images:
- Use dark backgrounds or transparent for best appearance
- Keep images under 500KB each
- Max width: 1200px
- Use descriptive filenames: `confusion-matrix.png`, not `image1.png`

## Step 5: Test Locally (Optional)

Before deploying, test your site locally:

```bash
# Install dependencies
gem install bundler jekyll
bundle install

# Run local server
bundle exec jekyll serve

# View at: http://localhost:4000
```

## Step 6: Deploy Changes

Whenever you make changes:

```bash
git add .
git commit -m "Your commit message"
git push origin main
```

GitHub Pages will automatically rebuild and deploy your site (takes 1-2 minutes).

## 🎨 Customization Tips

### Change Theme Colors

Edit `assets/css/style.scss`:

```scss
:root {
    --bg-primary: #0d1117;      /* Main background */
    --accent-primary: #58a6ff;  /* Links and highlights */
    /* Modify other colors as needed */
}
```

### Add New Pages

1. Create a new markdown file (e.g., `blog.md`)
2. Add front matter:

```yaml
---
layout: default
title: Blog
permalink: /blog/
---
```

3. Add to navigation in `_config.yml`:

```yaml
navigation:
  - title: "Blog"
    url: /blog
```

### Add Mathematical Equations

Use LaTeX syntax (MathJax already configured):

```markdown
Inline: $E = mc^2$

Display:
$$
\hat{y} = \beta_0 + \beta_1 x_1 + \epsilon
$$
```

### Add Code Blocks

Use fenced code blocks with language:

````markdown
```python
def hello():
    print("Hello, World!")
```
````

## 🔍 Troubleshooting

### Site Not Building

1. Check GitHub Actions tab for error messages
2. Verify `_config.yml` syntax is correct
3. Ensure all front matter has proper YAML format
4. Check that only GitHub Pages supported plugins are used

### Images Not Showing

1. Verify image path is correct (case-sensitive!)
2. Ensure image exists in `assets/images/`
3. Check file format is supported (PNG, JPG, SVG, GIF)
4. Use relative paths: `../assets/images/...`

### Changes Not Appearing

1. Hard refresh browser (Ctrl+F5 or Cmd+Shift+R)
2. Wait 1-2 minutes for GitHub Pages to rebuild
3. Check GitHub Actions for deployment status
4. Clear browser cache

### Layout Issues

1. Verify front matter includes `layout: default` or `layout: project`
2. Check that YAML front matter is properly formatted
3. Ensure no spaces before `---` markers

## 📊 Monitoring

### Check Build Status

- Go to **Actions** tab in your repository
- Look for green checkmarks (✓) or red X's (✗)
- Click on workflows to see detailed logs

### Analytics (Optional)

Add Google Analytics by editing `_config.yml`:

```yaml
google_analytics: UA-XXXXXXXXX-X
```

Or add your analytics code to `_layouts/default.html` before `</head>`.

## 🎯 Best Practices

### Content
- Keep project descriptions concise but informative
- Include real metrics and results
- Add visualizations to illustrate findings
- Write in first person for authenticity

### Images
- Optimize images before uploading (use TinyPNG)
- Use consistent image sizes within projects
- Add alt text for accessibility
- Include figure captions

### Projects
- Update regularly with new work
- Remove outdated projects
- Keep most impressive projects at the top (use dates)
- Link to live demos when possible

### Maintenance
- Review and update about page quarterly
- Keep resume current
- Fix broken links promptly
- Update dependencies periodically

## 🔒 Security

### Do NOT Include:
- Sensitive personal information
- API keys or credentials
- Private company data
- Confidential research

### DO Include:
- Public GitHub repositories
- Published papers/blogs
- General skills and experience
- Professional contact information

## 📱 Sharing Your Site

Once live, share your portfolio:

- LinkedIn profile
- GitHub profile README
- Resume/CV
- Email signature
- Professional networks
- Job applications

**Your URL**: https://jdwasner.github.io

## 🆘 Need Help?

### Resources
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)

### Common Questions

**Q: Can I use a custom domain?**  
A: Yes! Add a `CNAME` file with your domain and configure DNS settings.

**Q: How do I add a blog?**  
A: Create a `_posts/` directory and add markdown files with date format: `YYYY-MM-DD-title.md`

**Q: Can I change the theme?**  
A: Yes, but you'll need to modify the CSS. The current theme is optimized for dark mode.

**Q: How do I add more pages?**  
A: Create new `.md` files in the root directory with proper front matter.

## ✅ Checklist Before Going Live

- [ ] Updated `_config.yml` with your information
- [ ] Added resume PDF to `assets/resume/resume.pdf`
- [ ] Customized About page
- [ ] Updated or replaced example projects
- [ ] Added project images
- [ ] Tested all links work
- [ ] Reviewed content for typos
- [ ] Enabled GitHub Pages in settings
- [ ] Verified site builds successfully
- [ ] Shared with colleagues for feedback

## 🎉 Congratulations!

Your professional data science portfolio is now live! Keep it updated with your latest projects and achievements.

---

**Questions or issues?** Check the main README.md or open an issue in the repository.
