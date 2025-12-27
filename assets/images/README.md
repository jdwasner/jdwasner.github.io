# Project Images Directory

This directory contains images for project pages.

## Structure

Each project has its own subdirectory:
- `customer-churn/` - Images for Customer Churn Prediction project
- `sales-forecast/` - Images for Sales Forecasting project
- `medical-imaging/` - Images for Medical Image Classification project

## Adding Images

### For Existing Projects

1. Place your images in the appropriate project subdirectory
2. Reference them in your project markdown file using relative paths:

```markdown
![Description](../assets/images/projects/project-name/image.png)
*Figure caption goes here*
```

### For New Projects

1. Create a new subdirectory with your project name (use lowercase and hyphens)
2. Add your images to that directory
3. Reference them in your project markdown file

## Image Guidelines

### Formats
- **PNG** - Recommended for plots, charts, and diagrams (lossless)
- **JPEG** - For photographs and complex images
- **SVG** - For logos and vector graphics (scalable)

### Naming Conventions
Use descriptive, lowercase filenames with hyphens:
- ✅ `confusion-matrix.png`
- ✅ `feature-importance.png`
- ✅ `model-architecture.svg`
- ❌ `IMG_1234.jpg`
- ❌ `Screen Shot 2024-01-01.png`

### Size Recommendations
- **Maximum width**: 1200px (will be responsive)
- **Charts/Plots**: 800-1000px wide
- **Screenshots**: Keep file size under 500KB
- **Optimize images** before uploading using tools like:
  - [TinyPNG](https://tinypng.com/)
  - [ImageOptim](https://imageoptim.com/)
  - `optipng` or `jpegoptim` command-line tools

### Dark Mode Compatibility
Since this portfolio uses a dark theme:
- Use **transparent backgrounds** for plots when possible
- If using white backgrounds, add a border in your code
- Consider using dark backgrounds for plots to match the theme
- Test images on both light and dark backgrounds

### Accessibility
Always include:
1. **Alt text** in your markdown:
   ```markdown
   ![Descriptive alt text for screen readers](path/to/image.png)
   ```

2. **Figure captions** using italics:
   ```markdown
   ![Alt text](path/to/image.png)
   *Figure 1: Detailed caption explaining the visualization*
   ```

## Generating Plots for Data Science Projects

### Python Example with Dark Background

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Set dark style for plots
plt.style.use('dark_background')
sns.set_palette("husl")

# Your plotting code
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y)
ax.set_title('Your Title', fontsize=16)
ax.set_xlabel('X Label')
ax.set_ylabel('Y Label')

# Save with transparent background
plt.savefig('your-plot.png', dpi=300, bbox_inches='tight', 
            facecolor='none', edgecolor='none')
```

### Alternative: Save with dark background

```python
# Save with dark background to match theme
plt.savefig('your-plot.png', dpi=300, bbox_inches='tight',
            facecolor='#1c2128', edgecolor='none')
```

## Example Project Structure

```
assets/images/projects/
├── customer-churn/
│   ├── churn_distribution.png
│   ├── feature_importance.png
│   ├── confusion_matrix.png
│   └── roc_curve.png
├── sales-forecast/
│   ├── sales_trend.png
│   ├── seasonal_decomposition.png
│   └── predictions_vs_actual.png
└── medical-imaging/
    ├── class_distribution.png
    ├── sample_images.png
    └── training_history.png
```

## Troubleshooting

### Images Not Displaying
1. Check the file path is correct (case-sensitive)
2. Verify the image file exists in the directory
3. Ensure the image format is supported (PNG, JPG, SVG, GIF)
4. Check for typos in the filename

### Images Too Large
1. Resize using image editing software
2. Compress using online tools or CLI:
   ```bash
   # PNG compression
   optipng -o5 image.png
   
   # JPEG compression
   jpegoptim --max=85 image.jpg
   ```

### Images Look Bad on Dark Background
1. Use transparent backgrounds in plots
2. Add white borders to images with dark content
3. Use light-colored text and lines in visualizations

## Need Help?

If you need to add custom CSS for specific images, edit `assets/css/style.scss` and add styles under the "Project Detail Page" section.
