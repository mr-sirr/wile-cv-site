# Wile CV Site - Portfolio Website

**Live Site:** https://wilethecoyote.com
**Repository:** https://github.com/mr-sirr/wile-cv-site
**Netlify Dashboard:** https://app.netlify.com/

---

## Overview

This is a dark-themed, cyberpunk-inspired portfolio website for Ryan Smith, AI Architect. The site features:

- **Single-page design** with smooth scrolling navigation
- **Dark theme** with neon gradient accents (cyan, green, magenta)
- **Animated background effects** (floating gradient orbs, grid pattern)
- **Responsive layout** optimized for desktop and mobile
- **Static HTML** - no build process required

---

## Tech Stack

- **HTML5** - Single `index.html` file with embedded CSS and JavaScript
- **CSS3** - Custom properties, animations, gradients, flexbox/grid
- **Vanilla JavaScript** - Intersection Observer for scroll animations
- **Fonts:**
  - [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) - Main headings/body
  - [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) - Technical text/code elements
- **Hosting:** Netlify (auto-deploys from `main` branch)
- **Domain:** GoDaddy (DNS via Netlify nameservers)

---

## Project Structure

```
wilethecoyote_landing/
├── index.html          # Main website file (all HTML, CSS, JS)
├── resume.pdf          # Downloadable resume PDF
├── .gitignore          # Git ignore file
└── README.md           # This file
```

**Note:** All styles and scripts are embedded in `index.html` - no separate CSS/JS files.

---

## Quick Start

### Local Development

**Option 1: Direct File Open**
```bash
open index.html
```
Opens directly in your browser - works perfectly for this static site.

**Option 2: Local Server (Recommended)**
```bash
# Navigate to project directory
cd /path/to/wilethecoyote_landing

# Start Python server
python3 -m http.server 8000

# Visit in browser
open http://localhost:8000
```

**Option 3: Live Server (Auto-refresh)**
```bash
# Using npx (no install required)
npx live-server .
```

---

## Making Changes

### Content Updates

All content is in `index.html`. Key sections to edit:

#### 1. **Navigation** (Line ~686)
```html
<div class="nav-brand">rsmith.ai</div>
<div class="nav-links">
    <a href="#projects" class="nav-link">Projects</a>
    <!-- Add/remove nav links here -->
</div>
```

#### 2. **Hero Section** (Line ~700)
```html
<div class="hero-badge">
    <span class="status-dot"></span>
    Available for Opportunities • US/EU Authorized
</div>
<h1 class="hero-title">
    Building <span class="gradient-text">Intelligent Systems</span><br>
    That Understand Context
</h1>
```

#### 3. **Stats Bar** (Line ~720)
Update metrics like "30M+ Clients Served", "90%+ Token Reduction", etc.

#### 4. **Projects Section** (Line ~750)
Each project card includes:
- Icon (`.project-icon` with gradient background)
- Title and type
- Description
- Tech tags (`.tech-tag`)
- Status badge (⚡ In Development, 🔒 Private, 🧪 Research)

#### 5. **Experience Timeline** (Line ~850)
Chronological work history with:
- Date range (`.timeline-date`)
- Title and company
- Description and achievements list

#### 6. **Skills Section** (Line ~950)
Skill categories with progress bars:
- Skill name and level
- Progress bar (adjust `style="width: 95%"` to change)

#### 7. **Contact Section** (Line ~1050)
Links to email, LinkedIn, GitHub

### Design Changes

#### Color Scheme (Line ~10)
```css
:root {
    --bg-primary: #0a0a0f;        /* Main background */
    --bg-secondary: #13131a;      /* Cards/sections */
    --accent-primary: #00ff9f;    /* Neon green */
    --accent-secondary: #00ccff;  /* Cyan */
    --accent-tertiary: #ff0080;   /* Magenta */
    --text-primary: #ffffff;      /* White text */
    --text-secondary: #a0a0b0;    /* Gray text */
    --border-color: #2a2a35;      /* Borders */
}
```

#### Typography (Line ~8)
Change fonts by replacing Google Fonts URL:
```html
<link href="https://fonts.googleapis.com/css2?family=YourFont..." rel="stylesheet">
```

#### Animations (Line ~64, ~94, ~236)
- **Orb floating**: Adjust `@keyframes float` timing/movement
- **Gradient shift**: Modify `@keyframes gradient-shift` speed
- **Pulse effect**: Change `@keyframes pulse` for status dot

---

## Git Workflow

### Making Changes

```bash
# 1. Navigate to project
cd /Users/ryansmith/Desktop/eudaimonia/ai_coding/wilethecoyote_landing

# 2. Make your edits to index.html or other files

# 3. Check what changed
git status
git diff

# 4. Stage changes
git add .

# 5. Commit with descriptive message
git commit -m "Update project descriptions and add new skill"

# 6. Push to GitHub (triggers auto-deploy)
git push origin main
```

### Deployment Process

**Automatic deployment happens when you push to `main` branch:**

1. Push code to GitHub → 2. Netlify detects changes → 3. Site rebuilds (instant for static HTML) → 4. Live at https://wilethecoyote.com

**Check deployment status:**
- Go to: https://app.netlify.com/
- View: Build logs, deploy history, error messages

---

## Common Tasks

### Update Resume PDF

```bash
# 1. Replace the file
cp /path/to/new-resume.pdf resume.pdf

# 2. Commit and push
git add resume.pdf
git commit -m "Update resume PDF"
git push origin main
```

### Add New Project Card

Copy an existing `.project-card` block in `index.html` (around line ~770):

```html
<div class="project-card fade-in">
    <div class="project-header">
        <div class="project-icon icon-1">XX</div>
        <div>
            <h3 class="project-title">Your Project Name</h3>
            <p class="project-type">Project Type</p>
        </div>
    </div>
    <p class="project-description">
        Description of your project...
    </p>
    <div class="project-tech">
        <span class="tech-tag">Python</span>
        <span class="tech-tag">React</span>
    </div>
    <div class="project-status status-active">
        ⚡ Status Here
    </div>
</div>
```

### Change Domain

If you need to point to a different domain:

1. **In Netlify:**
   - Go to Site Settings → Domain management
   - Add/remove custom domains

2. **In GoDaddy (or your registrar):**
   - Update nameservers to Netlify's:
     - `dns1.p02.nsone.net`
     - `dns2.p02.nsone.net`
     - `dns3.p02.nsone.net`
     - `dns4.p02.nsone.net`

3. **Wait** 15 min - 48 hours for DNS propagation

---

## File Management

### Important Files

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `index.html` | Main website | Often |
| `resume.pdf` | Downloadable resume | Monthly/quarterly |
| `.gitignore` | Files to exclude from Git | Rarely |
| `README.md` | Documentation | As needed |

### Files NOT to Commit

Already configured in `.gitignore`:
- `.DS_Store` (Mac system files)
- `*.log` (Log files)
- `node_modules/` (If you add npm packages)
- `.env` (Environment variables)

---

## Troubleshooting

### Site Not Updating After Push

**Check:**
1. Did the push succeed? Run `git push origin main` and check for errors
2. Is Netlify building? Check https://app.netlify.com/ for deploy status
3. Browser cache? Hard refresh with `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)
4. Check Netlify deploy logs for errors

### Local Changes Not Showing

```bash
# Make sure changes are saved in your editor
# Hard refresh browser: Cmd+Shift+R (Mac) or Ctrl+F5 (Windows)
```

### Domain Not Working

**DNS issues take time:**
- Check https://dnschecker.org/ and enter `wilethecoyote.com`
- Ensure GoDaddy nameservers match Netlify's exactly
- Wait 24-48 hours for global DNS propagation
- SSL certificate generation can take up to 24 hours

### Git Push Rejected

```bash
# Pull latest changes first
git pull origin main

# Resolve any conflicts
# Then push again
git push origin main
```

---

## Performance & Best Practices

### Current Performance
- ✅ **Load time:** < 2 seconds
- ✅ **Mobile responsive:** Breakpoint at 768px
- ✅ **No external dependencies:** All assets embedded or from CDN
- ✅ **Animations:** Hardware-accelerated CSS animations

### Optimization Tips
1. **Images:** If adding images, compress them (use TinyPNG, ImageOptim)
2. **Fonts:** Only load font weights you use
3. **CSS:** Keep styles embedded for this small site (no extra HTTP request)
4. **JavaScript:** Minimal vanilla JS - no frameworks needed

---

## Browser Support

**Tested and working:**
- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile Safari (iOS 12+)
- ✅ Chrome Mobile (Android)

**Features requiring modern browsers:**
- CSS Custom Properties (IE11 not supported)
- Intersection Observer API (IE11 not supported)
- CSS Grid/Flexbox (IE11 partial support)

---

## Design System

### Color Palette

| Variable | Hex | Usage |
|----------|-----|-------|
| `--bg-primary` | `#0a0a0f` | Main background |
| `--bg-secondary` | `#13131a` | Cards, elevated surfaces |
| `--bg-tertiary` | `#1a1a24` | Nested elements |
| `--accent-primary` | `#00ff9f` | Neon green (primary CTA) |
| `--accent-secondary` | `#00ccff` | Cyan (secondary accents) |
| `--accent-tertiary` | `#ff0080` | Magenta (highlights) |
| `--text-primary` | `#ffffff` | Main text |
| `--text-secondary` | `#a0a0b0` | Secondary text |
| `--text-tertiary` | `#606070` | Muted text |
| `--border-color` | `#2a2a35` | Borders, dividers |

### Typography Scale

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Hero Title | 5rem (80px) | 700 | Space Grotesk |
| Section Title | 3rem (48px) | 700 | Space Grotesk |
| Project Title | 1.5rem (24px) | 700 | Space Grotesk |
| Body Text | 1rem (16px) | 400 | Space Grotesk |
| Small Text | 0.875rem (14px) | 500 | Space Grotesk |
| Code/Technical | varies | 400-600 | JetBrains Mono |

### Spacing System

```css
/* Consistent spacing values */
0.25rem = 4px
0.5rem = 8px
0.75rem = 12px
1rem = 16px
1.5rem = 24px
2rem = 32px
3rem = 48px
4rem = 64px
6rem = 96px
8rem = 128px
```

---

## AI Assistant Onboarding

### For Future AI Collaborators

**Project Context:**
- Static portfolio site for Ryan Smith (AI Architect)
- Single HTML file with embedded CSS/JavaScript
- Dark cyberpunk aesthetic with neon gradients
- Auto-deploys to Netlify on push to `main` branch

**Key Information:**
- **Owner:** Ryan Smith
- **Contact:** ryan@rsmith.ai
- **GitHub Repo:** https://github.com/mr-sirr/wile-cv-site
- **Live URL:** https://wilethecoyote.com
- **Backup URL:** [original-netlify-url].netlify.app

**Common Requests:**
1. "Update my work experience" → Edit timeline section (line ~850)
2. "Add a new project" → Copy project card template (line ~770)
3. "Change colors" → Modify CSS variables (line ~10)
4. "Update resume" → Replace `resume.pdf` file
5. "Fix mobile layout" → Check responsive CSS (line ~600)

**Before Making Changes:**
1. Read current content to understand context
2. Maintain existing design aesthetic and code style
3. Test locally before committing
4. Write clear commit messages
5. Verify Netlify deployment succeeded

**Code Style:**
- Indentation: 4 spaces
- CSS: Use CSS custom properties for colors
- JavaScript: Vanilla JS, no dependencies
- Comments: Add for complex sections

---

## Security & Access

### Repository Access
- **Owner:** @mr-sirr (Ryan Smith)
- **Visibility:** Public repository
- **Branch Protection:** None (direct push to `main` allowed)

### Netlify Access
- **Site Owner:** Ryan Smith
- **Deploy Key:** Auto-generated by Netlify/GitHub integration
- **Environment Variables:** None required

### Domain Access
- **Registrar:** GoDaddy
- **DNS Management:** Netlify (via nameservers)
- **SSL Certificate:** Auto-managed by Netlify (Let's Encrypt)

---

## Backup & Recovery

### Backup Strategy
- ✅ **Code:** Backed up on GitHub (public repo)
- ✅ **Deployments:** Netlify keeps deploy history
- ✅ **Domain:** Registered through GoDaddy

### Rollback Process

**If bad deploy:**
```bash
# Option 1: Revert last commit
git revert HEAD
git push origin main

# Option 2: Use Netlify UI
# Go to Deploys → Select previous working deploy → "Publish deploy"
```

**If catastrophic failure:**
1. Clone fresh copy from GitHub: `git clone https://github.com/mr-sirr/wile-cv-site.git`
2. Re-deploy to new Netlify site if needed
3. Update DNS if necessary

---

## Resources & Links

### Project Links
- **Live Site:** https://wilethecoyote.com
- **GitHub Repo:** https://github.com/mr-sirr/wile-cv-site
- **Netlify Dashboard:** https://app.netlify.com/

### External Resources
- **Netlify Docs:** https://docs.netlify.com/
- **Git Documentation:** https://git-scm.com/doc
- **Google Fonts:** https://fonts.google.com/
- **MDN Web Docs:** https://developer.mozilla.org/

### Design Inspiration
- **Space Grotesk Font:** https://fonts.google.com/specimen/Space+Grotesk
- **JetBrains Mono Font:** https://www.jetbrains.com/lp/mono/
- **CSS Gradients:** https://cssgradient.io/

---

## Contact & Support

**Site Owner:**
Ryan Smith
📧 ryan@rsmith.ai
🔗 https://rsmith.ai
💼 https://linkedin.com/in/rsmith-ai
🐙 https://github.com/mr-sirr

**For Issues:**
- Create an issue on GitHub: https://github.com/mr-sirr/wile-cv-site/issues
- Email: ryan@rsmith.ai

---

## Changelog

### 2025-09-30 - Initial Release
- Created dark cyberpunk-themed portfolio site
- Deployed to Netlify
- Connected domain wilethecoyote.com
- Added comprehensive README

---

*Last Updated: September 30, 2025*
*Version: 1.0.0*
*Status: Production*
