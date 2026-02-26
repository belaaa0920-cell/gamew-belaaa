# Homepage Implementation Plan

## Overview
Complete the game homepage (index.html) with proper navigation to game files and dark/light mode toggle functionality.

## Current Issues Identified
1. **Broken Links**: Index.html links use `../` prefix but all files are in same directory
2. **Missing Theme Toggle**: No dark/light mode toggle button
3. **Game Return Links**: Game files point to `../stitch/index.html` which doesn't exist

## Required Changes

### 1. Fix Index.html Links
- Change `href="../memories cards.html"` to `href="memories cards.html"`
- Change `href="../snack.html"` to `href="snack.html"`

### 2. Add Dark/Light Mode Toggle
**HTML Changes (Header section):**
```html
<button id="theme-toggle" class="w-10 h-10 rounded-full bg-white/80 dark:bg-slate-800 backdrop-blur-sm shadow-sm flex items-center justify-center text-slate-500 hover:text-primary transition-colors" title="Toggle dark/light mode">
    <span class="material-symbols-outlined" id="theme-icon">dark_mode</span>
</button>
```

**JavaScript Implementation:**
```javascript
// Theme toggle functionality
const themeToggle = document.getElementById('theme-toggle');
const themeIcon = document.getElementById('theme-icon');
const htmlElement = document.documentElement;

// Check for saved theme preference or default to light
const currentTheme = localStorage.getItem('theme') || 'light';
htmlElement.classList.toggle('dark', currentTheme === 'dark');
updateThemeIcon(currentTheme);

themeToggle.addEventListener('click', () => {
    const isDark = htmlElement.classList.toggle('dark');
    const newTheme = isDark ? 'dark' : 'light';
    localStorage.setItem('theme', newTheme);
    updateThemeIcon(newTheme);
});

function updateThemeIcon(theme) {
    themeIcon.textContent = theme === 'dark' ? 'light_mode' : 'dark_mode';
}
```

### 3. Fix Game File Return Links
**In snack.html:**
- Change `href="../stitch/index.html"` to `href="index.html"`

**In memories cards.html:**
- Change `href="../stitch/index.html"` to `href="index.html"`

## Testing Checklist
- [ ] Homepage loads correctly
- [ ] Game cards link to correct game files
- [ ] Dark/light mode toggle works
- [ ] Theme preference persists across page reloads
- [ ] Game files can return to homepage
- [ ] Responsive design works on mobile/desktop

## Files to Modify
1. `index.html` - Fix links, add theme toggle
2. `snack.html` - Fix return link
3. `memories cards.html` - Fix return link

## Implementation Notes
- All files are in the same directory (`c:/CODE/gamew-belaaa`)
- Tailwind already configured for dark mode (`darkMode: "class"`)
- Current design uses Material Symbols icons
- No need to follow PRD.md requirements for homepage (per user instruction)