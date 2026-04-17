# Project Files Directory

This directory contains downloadable project files (`.koala`, DAW projects, stems, etc.) for the Xalpheric Neocities site.

## Supported File Types

### ✅ Supported by Neocities
- `.koala` - Koala Sampler project files
- `.mp3`, `.ogg`, `.wav` - Audio files
- `.mid`, `.midi` - MIDI files
- `.txt`, `.pdf` - Documentation files
- `.json` - Configuration/metadata files

### ❌ NOT Supported by Neocities
- `.zip` - Compressed archives (must be uncompressed)
- `.exe`, `.dmg`, `.app` - Executable files
- `.torrent` - Torrent files

## Adding New Project Files

### 1. Prepare Your Files

For Koala Sampler projects:
```bash
# Place .koala files here with descriptive names
cp ~/path/to/your-track.koala projects/your-track.koala
```

For other DAW projects (when .zip isn't supported):
- Upload individual project files
- Upload stems/audio separately
- Provide a text file with reconstruction instructions

### 2. Update projects.html

Add a new project card to `/public/projects.html`:

```html
<div class="project-card">
  <div class="project-header">
    <img src="assets/your-album-art.jpg" alt="Your Track" class="project-thumbnail" />
    <div class="project-info">
      <h3 class="project-title">Your Track Name</h3>
      <p class="project-meta">Duration: X:XX | Format: .koala</p>
      <p class="project-description">Description of your track and what makes it interesting.</p>
    </div>
  </div>
  <div class="project-actions">
    <a href="projects/your-track.koala" download class="download-btn">
      <span class="download-icon">⬇</span> Download Project
    </a>
    <span class="file-size">File size: <span class="size-value">XXX KB</span></span>
  </div>
</div>
```

### 3. Deploy

Use the existing deployment scripts:

```bash
# Deploy all files including new projects
npm run deploy-full-refresh

# Or use a targeted deployment (if you create one)
# This would upload only the projects directory
export NEOCITIES_API_KEY="your-key"
node deploy-projects.js
```

## File Size Considerations

Neocities has a 50MB per-file limit. For large projects:

1. **Koala files** are typically 1-10MB (samples included)
2. **DAW projects** without audio can be small (< 1MB)
3. **Stems/audio** should be compressed (MP3/OGG) to save space

## License Information

All project files should be:
- **Licensed**: Creative Commons BY-SA 4.0 (as stated on projects.html)
- **Documented**: Include track info, duration, description
- **Clean**: No copyrighted samples unless you have permission

## Automation Ideas

Future enhancements could include:

1. **Auto-generate project cards** from JSON metadata
2. **Calculate file sizes** automatically during build
3. **Validate file types** before deployment
4. **Create deployment manifest** for projects directory only

## Current Projects

- good-mood-geometry.koala
- i-believe-in-music.koala
- josh-flute.koala
- snake-taming-for-dummies.koala
- sunrise-over-alborz.koala
- who-let-the-funk-out.koala

*Note: Upload actual .koala files to this directory before deploying*
