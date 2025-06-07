
# Windows and Linux shortcuts 
## Common Actions

|Action|Shortcut|
|---|---|
|Copy|`Ctrl+C`|
|Cut|`Ctrl+X`|
|Paste|`Ctrl+V`|
|Paste without formatting|`Ctrl+Shift+V`|
|Undo|`Ctrl+Z`|
|Redo|`Ctrl+Shift+Z` or `Ctrl+Y`|
|Copy paragraph|`Ctrl+C` (with no selection)|
|Cut paragraph|`Ctrl+X` (with no selection)|
## Text Editing
|Action|Shortcut|
|---|---|
|Insert new line|`Enter`|
|Delete previous character|`Backspace`|
|Delete next character|`Delete`|
|Delete previous word|`Ctrl+Backspace`|
|Delete next word|`Ctrl+Delete`|
|Delete current line|`Ctrl+Shift+K`|
## Text Navigation
|Action|Shortcut|
|---|---|
|Move cursor one character|`Left/Right Arrow`|
|Move to beginning of previous word|`Ctrl+Left Arrow`|
|Move to end of next word|`Ctrl+Right Arrow`|
|Move to beginning of current line|`Home`|
|Move to end of current line|`End`|
|Move to previous line|`Up Arrow`|
|Move to next line|`Down Arrow`|
|Move to beginning of note|`Ctrl+Home`|
|Move to end of note|`Ctrl+End`|
|Move up one page|`Page Up`|
|Move down one page|`Page Down`|
## Text Selection
|Action|Shortcut|
|---|---|
|Simplify selection|`Escape`|
|Select all|`Ctrl+A`|
|Extend selection one character|`Shift+Left/Right Arrow`|
|Extend selection to previous word|`Ctrl+Shift+Left Arrow`|
|Extend selection to next word|`Ctrl+Shift+Right Arrow`|
|Extend selection to beginning of line|`Shift+Home`|
|Extend selection to end of line|`Shift+End`|
|Extend selection to beginning of note|`Ctrl+Shift+Home`|
|Extend selection to end of note|`Ctrl+Shift+End`|
|Extend selection one page up|`Shift+Page Up`|
|Extend selection one page down|`Shift+Page Down`|
# Setup
## Plugins
 - heading-level-indent
 - Style Settings
 - Remote - WSL
## Snippets
### acePalenight
```css
/* Palenight Background */
body {
  --background-primary: #292D3E;
  --background-secondary: #1E222E;
  --background-modifier-hover: #3C435E;
  --background-modifier-border: #444267;

  --text-normal: #A6ACCD;
  --text-muted: #676E95;
  --text-accent: #C792EA;

  --interactive-accent: #82AAFF;
  --interactive-accent-hover: #F07178;

  --h1-color: #82AAFF;
  --h2-color: #C792EA;
  --h3-color: #F07178;
}

/* Code blocks */
.markdown-preview-view code,
.cm-s-obsidian span.cm-inline-code {
  background-color: #1E222E;
  color: #C792EA;
}

/* Links */
a {
  color: #82AAFF;
}

```
### header_color
```CSS
/* Obsidian header colors */

.markdown-preview-view h1 {

  color: #C678DD; /* Plum Purple */

}

  

.markdown-preview-view h2 {

  color: #EBCB8B; /* Muted Yellow */

}

  

.markdown-preview-view h3 {

  color: #E06C75; /* Coral Red */

}

  

.markdown-preview-view h4 {

  color: #98C379; /* Leaf Green */

}

  

.markdown-preview-view h5 {

  color: #56B6C2; /* Soft Cyan */

}

  

.markdown-preview-view h6 {

  color: #61AFEF; /* Sky Blue */

}
```

### header-colorize
```CSS
/* Colorize headers in editor (Live Preview / Source Mode) */

.cm-header-1 {

  color: #C678DD; /* Plum Purple */

}

  

.cm-header-2 {

  color: #EBCB8B; /* Muted Yellow */

}

  

.cm-header-3 {

  color: #E06C75; /* Coral Red */

}

  

.cm-header-4 {

  color: #98C379; /* Leaf Green */

}

  

.cm-header-5 {

  color: #56B6C2; /* Soft Cyan */

}

  

.cm-header-6 {

  color: #61AFEF; /* Sky Blue */

}
```