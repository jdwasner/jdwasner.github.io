# Resume Directory

This directory is for storing your resume PDF file.

## Adding Your Resume

1. Place your resume PDF in this directory with the filename `resume.pdf`
2. The resume will be accessible via the download buttons on the homepage and about page

## File Requirements

- **Filename**: `resume.pdf` (lowercase, exactly this name)
- **Format**: PDF only
- **Size**: Recommended under 2MB for fast loading
- **Content**: Ensure the PDF is:
  - Up to date with your latest experience
  - Professionally formatted
  - Free of typos and errors
  - Optimized for both screen reading and printing

## How It Works

The download buttons link to `/assets/resume/resume.pdf`. When visitors click the button:
- The browser will prompt them to download the file
- Or open it in a new tab (depending on browser settings)

## Updating Your Resume

To update your resume:
1. Replace the `resume.pdf` file with your updated version
2. Keep the same filename (`resume.pdf`)
3. Commit and push the changes to GitHub
4. GitHub Pages will automatically update the file

## Alternative: External Link

If you prefer to host your resume elsewhere (Google Drive, Dropbox, personal website):
1. Edit the download button links in `index.md` and `about.md`
2. Replace `/assets/resume/resume.pdf` with your external URL
3. Example:
   ```markdown
   <a href="https://drive.google.com/file/d/YOUR_FILE_ID/view" 
      class="btn-resume" target="_blank">
       📄 Download My Resume
   </a>
   ```

## File Size Optimization

If your PDF is too large, you can compress it using:
- Online tools: [SmallPDF](https://smallpdf.com/compress-pdf), [iLovePDF](https://www.ilovepdf.com/compress_pdf)
- Command line: `gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf`
- Adobe Acrobat: File > Save As Other > Reduced Size PDF

## Best Practices

1. **Privacy**: Don't include sensitive information (full address, SSN, etc.)
2. **Keywords**: Include relevant keywords for ATS (Applicant Tracking Systems)
3. **Format**: Use standard fonts and avoid complex formatting
4. **Length**: 1-2 pages recommended for most positions
5. **File name on disk**: While the web URL is `/assets/resume/resume.pdf`, consider keeping versions locally like `YourName_Resume_2024.pdf`

## Security Note

⚠️ Remember that this resume will be publicly accessible on the internet. Only include information you're comfortable sharing publicly.

## Version Control

Consider keeping multiple versions:
```
assets/resume/
├── resume.pdf                 (Current public version)
└── archive/
    ├── resume_2024_01.pdf
    ├── resume_2024_06.pdf
    └── resume_2024_12.pdf
```

Add the `archive/` directory to `.gitignore` if you don't want to track it in version control.
