# Rich Markdown Code Comments

Rich Markdown Code Comments is a JetBrains plugin that allows you to embed links to full Markdown notes directly within your source code comments. This plugin helps you keep your code comments concise while providing a way to access detailed documentation, bug reports, or refactoring notes with a single click or hover preview.

## Reporting Bugs or Other Issues
To report a bug, use the "Issues" tab above to create a new issue.

# User Guide

## 1. Organizing Your Notes

All note files must be located in a folder named `notes` at the root of your project directory. You can organize these files into subfolders as you see fit.

Example structure:
```text
ProjectRoot/
├── notes/
│   ├── design_notes.md
│   ├── bugs/
│   │   ├── bug_123.md
│   └── refactoring/
│       └── cleanup_task.md
├── src/
│   └── Main.java
```

## 2. Linking to Notes in Comments

You can link to any Markdown file in your `notes` folder from any comment in your source code using a special tag syntax. The plugin supports three types of links, each with its own customizable highlighting:

- **Notes**: `{#note:fileName}`
- **Bugs**: `{#bug:fileName}`
- **Refactoring**: `{#refactor:fileName}`

Example:
```java
// {#note:MyClassDesign} Design notes for MyClass.
public class MyClass{
}
```

### Syntax Rules (file names are case-insensitive):
- **Direct filename**: `{#note:design_notes}` (The `.md` extension is optional)
- **Nested paths**: `{#bug:bugs/bug_123}`
- **Recursive search**: Even if you just use `{#note:cleanup_task}`, the plugin will find it even if it is deep within the `notes` folder hierarchy. Note that in the case of a naming collision, the first hierarchical match will be returned.

## 3. Viewing Previews

When you hover your mouse over a note tag in a comment, a documentation popup will appear showing a rendered HTML preview of the Markdown file's content. This allows you to read detailed information without ever leaving your current file.

### How to use:
1. Hover your mouse over a tag like `{#note:my-note}`.
2. Wait for the IDE's documentation popup to appear.
3. Scroll through the rendered Markdown content.

## 4. Navigating to Note Files

There are two ways to open the actual Markdown file for editing or full-screen reading:

1. **Standard IDE Navigation**: Hold `Ctrl` (or `Cmd` on macOS) and click the link in the comment.
2. **Single-Click Navigation** (Optional): If enabled in settings, you can simply click the link without holding any modifier keys. Your cursor will change to a hand icon when hovering over a clickable link.

Note that if Single-Click Navigation is enabled, you will not be able to click into the middle of a note comment to edit/change the name. You will need to click next to it and navigate over using the keyboard.

## 5. Customizing Plugin Settings

You can customize the appearance and behavior of the plugin by going to:
**Settings/Other Settings** > **Rich Markdown Comments**

If you cannot find this menu option, search for "Rich Markdown Comments" in the Settings dialog.

### Available Options:

- **Highlight Colors**: For each type (Note, Bug, Refactor), you can choose a custom color that the tag will use in the editor.
- **Add Highlight Box**: Toggles a rounded box around the tag to make it stand out even more.
- **Clickable Note References**: When enabled, allows you to open note files with a single click (no `Ctrl` needed). This is disabled by default to avoid accidental navigation while clicking around your code.
