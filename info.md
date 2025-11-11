# OceanBoard Project Info

> **The complete guide to understanding the OceanBoard project!**

---

## **What is OceanBoard?**

OceanBoard is a **free, offline-first creative workspace** for writers, storytellers, and world-builders! It's a single-page web application built with vanilla JavaScript that helps you organize and write your creative projects with style!

**Think of it as:** Notion meets Scrivener meets VS Code, but simpler, prettier, and free!

---

## **Project Structure**

### **Top Level**
```
OceanBoardBeta/
├── changelog.md
# Version history
├── src/                    # Source code (the app!)
├── docs/                   # Documentation files
└── shc/                    # Shortcuts & icons
```

### **The Important Folders**

#### **src/** - The Application
Where all the magic happens! Contains the complete web app.

**What's inside:**
- `index.html` - Main entry point
- `classes/` - JavaScript modules (the brain!)
- `styles/` - CSS files (the beauty!)
- `media/` - Images, icons, fonts
- `iframes/` - Popup windows

#### **docs/** - Documentation
All user-facing and technical documentation.

---

## **Technology Stack**

### **Core Technologies**
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with Grid/Flexbox
- **Vanilla JavaScript** - No frameworks!
- **ES6 Modules** - Clean, modular code

### **Browser APIs**
- **LocalStorage** - Data persistence
- **Canvas API** - Particle system
- **File API** - File reading
- **Blob API** - File downloads

### **External Libraries**
- **JSZip** (3.10.1) - Import/export as ZIP files
- **Marked** (15.0.12) - Support for Markdown
- **lz-string** (1.5.0) - Compression algorithm
- That's it!

### **No Build Process!**
Just open `src/index.html` in a browser and you're done!

---

## **Design System**

### **Colors**
```css
/* Primary */
--primary-pink: hsl(340, 100%, 70%);
--primary-pink-light: hsl(340, 100%, 80%);
--primary-pink-dark: hsl(340, 100%, 60%);

/* Dark Theme */
--bg-darker: hsl(230, 15%, 15%);
--bg-dark: hsl(230, 10%, 20%);
--bg-medium: hsl(230, 8%, 25%);
--bg-light: hsl(230, 6%, 30%);

/* Text */
--text-primary: hsl(0, 0%, 90%);
--text-secondary: hsl(0, 0%, 70%);
--text-muted: hsl(0, 0%, 50%);
```

### **Typography**
```css
/* Fonts */
font-family: Pacifico, Dosis, 'Comfortaa', sans-serif;

/* Sizes */
--font-xs: 0.75rem;   /* 12px */
--font-sm: 0.875rem;  /* 14px */
--font-md: 1rem;      /* 16px */
--font-lg: 1.125rem;  /* 18px */
--font-xl: 1.25rem;   /* 20px */
```

### **Spacing**
```css
--spacing-xs: 0.25rem;  /* 4px */
--spacing-sm: 0.5rem;   /* 8px */
--spacing-md: 1rem;     /* 16px */
--spacing-lg: 1.5rem;   /* 24px */
--spacing-xl: 2rem;     /* 32px */
```

### **Animations**
- Duration: 200-400ms
- Easing: cubic-bezier(0.4, 0, 0.2, 1)
- 60fps target (GPU-accelerated)

---

## **Architecture Overview**

### **Module System**
```
classes/
├── index.js                  # Main Stuff
├── editors/
│   ├── tabsystem.js         # Tab management
│   └── markdowneditor.js    # Markdown editor
├── filesystem/
│   ├── seriessystem.js      # Series management
│   ├── filesmanager.js      # File operations
│   ├── importexport.js      # ZIP import/export
│   └── dragdrop.js          # Drag-and-drop
├── canvas/
│   └── particles.js         # Particle system
└── forStyles/
    └── animations.js         # Animation helpers
```

### **Data Flow**
1. User interacts with UI
2. Event handler in appropriate module
3. Update localStorage
4. Update DOM to reflect changes
5. Trigger animations

### **Storage Structure**
```javascript
localStorage = {
  'ob-seriesList': [...],          // All series
  'ob-activeSeries': 'id',         // Current series
  'ob-series-{id}': {...},         // Series data
  'ob-file-{id}': 'content',       // File contents
  'ob-settings-fontSize': '16',    // Settings
  'ob-settings-lineHeight': '1.8', // etc.
}
```

---

## **Core Features**

### **1. Series System**
Manage multiple independent projects (workspaces).

**Features:**
- Create/rename/delete series
- Custom colors & cover images
- Switch between series
- Export/import series


### **2. File Explorer**
Organize content into seasons and episodes.

**Features:**
- Drag-and-drop reordering
- Collapsible seasons
- Special file types (Components)
- Context menus

### **3. Markdown Editor**
Write with live preview!

**Features:**
- Split view (edit | preview)
- 13 formatting buttons
- Auto-wrap selection
- Syntax highlighting

---

## **Development Workflow**

### **Local Development**
1. Clone repository
2. Open `src/index.html` in browser
3. Make changes
4. Refresh to see updates
5. No build step needed!

### **Testing**
- Test in Chrome, Firefox, Safari, Edge
- Test on Windows, Mac, Linux
- Mobile testing (responsive design)
- LocalStorage limits testing

### **Release Process**
1. Update version in all files
2. Write changelog entry
3. Test everything thoroughly
4. Create backup in `backups/` (just in case)
5. Tag release
6. Push to GitHub
7. Deploy to website

---

## **Code Style**

### **JavaScript**
```javascript
// Classes
class ParticleSystem { }

// Functions/Variables
function createSeries() { }
let activeSeries = null;

// Constants
const MAX_FILE_SIZE = 2097152;

// Use ES6+
const items = [...array];
const { id, name } = object;

// Comment complex logic
// Calculate particle velocity based on mouse distance
const velocity = Math.sqrt(dx * dx + dy * dy) / 100;
```

### **CSS**
```css
/* .ob is cool naming. */
.ob-sidebar { }
.ob-sidebar-header { }
.ob-sidebar-header--active { }

/* Variables for everything */
color: var(--primary-pink);
padding: var(--spacing-md);

/* Mobile-approach */
.element { }
@media (min-width: 768px) { }
```

### **HTML**
```html
<!-- Semantic elements -->
<nav>, <section>, <article>, <aside>

<!-- Descriptive classes -->
<div class="ob-editor-container">

<!-- Data attributes for JS -->
<button data-action="save" data-id="123">
```

---

## **Adding New Features**

### **Step 1: Plan**
- What does the feature do?
- Where does it fit in the UI?
- What data needs to be stored?
- What modules need changes?

### **Step 2: Implement**
1. Create new module or update existing
2. Add HTML structure
3. Add CSS styling
4. Add JavaScript functionality
5. Update storage if needed

### **Step 3: Test**
- Does it work?
- Is it fast?
- Does it look good?
- Does it break anything?

### **Step 4: Document**
- Update relevant info.md
- Update user guide
- Update feature guide
- Add to changelog

---

## **Current Status**
### **Completed Features**
- Tab system
- Particle system & animations
- Import/export (ZIP)
- Settings system
- Context menus
- Drag-and-drop
- Auto-save
- Empty states
- Search & filter
- Keyboard shortcuts
- Command palette
- Statistics

### **In Development**
- Tags system
- Templates
- Generalized use: not only to create stories tool.
- To Do Lists
- More color themes!
- More settings (like types of icon, types of font, spellcheck)

### **Planned**
- Code editor
- Extension system (you can publish & download)
- Visual coding stuff
- PDF, docs, presentation file - export

> But keeping everything local. Everything lightweigh. Everything open. Forever

**[Full roadmap →](./docs/roadmap.md)**

---

## **Project Stats**

### **Code**
- **Languages:** JavaScript, CSS, HTML
- **Files:** 80+
- **Modules:** 25+

### **Features**
- **Series:** Unlimited
- **Files:** Unlimited
- **File Types:** 6 special types
- **Settings:** 7 options

### **Performance**
- **Load Time:** <3s
- **Storage:** 5-10MB typical
- **Bundle Size:** ~200KB

---

## **Contributing**

### **Ways to Help**
1. Report bugs
2. Suggest features  
3. Improve documentation
4. Submit code
5. Create themes
6. Spread the word


## **Philosophy**

### **Core Values**
1. **User First** - Everything serves the user
2. **Privacy** - No tracking, no accounts
3. **Simplicity** - Complex features, simple UX
4. **Easy on everyone** - Keep it simple, uncomplicated whenever possible
5. **Code open** - Always open code. Absolute freedom in every aspect

### **Design Principles**
1. **Progressive Disclosure** - Show what's needed, when needed
2. **Consistent Patterns** - Similar things work similarly
3. **Immediate Feedback** - User knows what happened
4. **Accessibility** - A tool must be always easily accessible, 3 clicks away max.

---

## **The Story**

OceanBoard started as a personal project by **umaera** to solve a simple problem: existing writing tools were either too complex, too expensive, or just not pretty enough!

**Goals:**
- ✅ Beautiful interface that inspires
- ✅ Offline-first (no internet needed)
- ✅ Privacy-respecting (no tracking, no ads)
- ✅ Free forever (open code, for everyone)
- ✅ Easy to use (everything a few clicks away)

**Result:** OceanBoard - a creative workspace that makes writing & planning fun!

---

## **Contact & Community**

- **Bug Reports:** [Forms](https://forms.gle/VD4Qn2DiFyBh8Pib6)
- **Feature Requests:** [Forms](https://forms.gle/VD4Qn2DiFyBh8Pib6)
- **Email:** umaera.dev@gmail.com

---

## **Star History**

If you like OceanBoard, give it a star on GitHub or make us a rating on our [Forms](https://forms.gle/VD4Qn2DiFyBh8Pib6)!

Every feeback motivates continued development and helps others discover the project!

---

## **Thank You**

To everyone who:
- Uses OceanBoard for their creative projects
- Reports bugs and suggests features
- Spreads the word about OceanBoard
- Contributes code or documentation
- Supports the project in any way

**You make OceanBoard possible!**

---

<div align="center">

## **OceanBoard**

[Documentation](https://umaera.github.io/OceanBoard/docs) • [Roadmap](./docs/roadmap.md) • [GitHub](https://github.com/NotYarazi/OceanBoard)
</div>
