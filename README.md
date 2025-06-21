# LaTeX with VS Code Setup Guide

This guide will help you set up and use LaTeX with Visual Studio Code for document creation, particularly for documents with Thai language support.

## Prerequisites

### 1. Install MacTeX (LaTeX Distribution)

MacTeX is the standard LaTeX distribution for macOS that includes all necessary LaTeX packages and compilers.

```bash
# Download and install MacTeX from:
# https://www.tug.org/mactex/

# Or install via Homebrew (recommended)
brew install --cask mactex-no-gui
```

**Note**: MacTeX is a large download (~4GB). The `mactex-no-gui` version excludes GUI applications to save space.

### 2. Install Visual Studio Code

Download and install VS Code from [https://code.visualstudio.com/](https://code.visualstudio.com/)

### 3. Install LaTeX Workshop Extension

1. Open VS Code
2. Go to Extensions (Cmd+Shift+X)
3. Search for "LaTeX Workshop"
4. Install the extension by James Yu

## Project Structure

This project uses the following structure:

```text
thesis-proposal/
├── main.tex              # Main LaTeX document
├── main.pdf              # Generated PDF output
├── font/                 # Custom fonts directory
│   └── Sarabun/         # Thai font family
│       ├── Sarabun-Regular.ttf
│       ├── Sarabun-Medium.ttf
│       ├── Sarabun-Italic.ttf
│       └── ...
├── images/              # Images and figures
│   ├── platform_1.png
│   └── platform_2.png
└── README.md           # This guide
```

## Building the Document

### Method 1: VS Code Tasks (Recommended)

This project includes a pre-configured VS Code task for building with XeLaTeX:

1. Open the Command Palette (Cmd+Shift+P)
2. Type "Tasks: Run Task"
3. Select "Build LaTeX with XeLaTeX"

### Method 2: LaTeX Workshop Extension

The LaTeX Workshop extension provides automatic building:

1. Save your `.tex` file (Cmd+S)
2. The extension will automatically compile the document
3. View the PDF in the integrated viewer

### Method 3: Terminal Commands

You can also build manually using terminal commands:

```bash
# Build with XeLaTeX (required for Thai fonts)
xelatex -interaction=nonstopmode main.tex

# For documents with bibliography
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

## Key Features of This Setup

### XeLaTeX Compiler

This project uses XeLaTeX instead of standard LaTeX because:

- **Unicode Support**: Better handling of Thai characters
- **Font Flexibility**: Can use system fonts and custom fonts
- **Advanced Typography**: Better text rendering for non-Latin scripts

### Thai Language Support

The document includes:

- Custom Sarabun font family for Thai text
- Proper font configuration for Thai typography
- Unicode support for Thai characters

### VS Code Configuration

The project includes optimized settings for:

- Automatic compilation with XeLaTeX
- Custom build tasks
- Thai language support

## LaTeX Workshop Extension Features

### 1. Automatic Compilation

- Files are compiled automatically when saved
- Progress shown in the status bar
- Error messages displayed in the Problems panel

### 2. PDF Preview

- Integrated PDF viewer
- Sync between source and PDF (SyncTeX)
- Side-by-side editing and preview

### 3. Useful Shortcuts

- `Cmd+S`: Save and compile
- `Cmd+Option+V`: View PDF
- `Cmd+Option+J`: Navigate to PDF location
- `Cmd+Option+C`: Clean auxiliary files

### 4. Snippets and IntelliSense

- LaTeX command completion
- Environment snippets
- Symbol insertion
- Citation management

## Troubleshooting

### Common Issues

#### 1. Thai Fonts Not Displaying

**Problem**: Thai characters appear as boxes or missing characters

**Solution**:

- Ensure XeLaTeX is used (not pdfLaTeX)
- Verify font files are in the correct location
- Check font path in the LaTeX document

#### 2. Compilation Errors

**Problem**: Document fails to compile

**Solution**:

- Check the Problems panel in VS Code
- Review the LaTeX log file
- Ensure all required packages are installed

#### 3. PDF Not Updating

**Problem**: PDF doesn't reflect recent changes

**Solution**:

- Save the file (Cmd+S) to trigger compilation
- Check if there are compilation errors
- Try cleaning auxiliary files and rebuilding

### Cleaning Auxiliary Files

LaTeX generates several auxiliary files during compilation. To clean them:

```bash
# Remove auxiliary files
rm *.aux *.log *.out *.synctex.gz *.toc *.lof *.lot *.bbl *.blg
```

Or use the LaTeX Workshop command:

1. Command Palette (Cmd+Shift+P)
2. "LaTeX Workshop: Clean up auxiliary files"

## Useful Extensions

Consider installing these additional extensions:

1. **LaTeX Utilities** - Additional LaTeX tools
2. **Code Spell Checker** - Spell checking for documents
3. **Better Comments** - Enhanced comment highlighting
4. **Bracket Pair Colorizer** - Better bracket matching

## Tips for Effective LaTeX Writing

### 1. File Organization

- Keep images in a separate `images/` folder
- Use meaningful file names
- Comment your code extensively

### 2. Version Control

- Use Git for version control
- Commit frequently with meaningful messages
- Consider using `.gitignore` for auxiliary files

### 3. Writing Process

- Write content first, format later
- Use labels and references for cross-references
- Preview frequently to catch errors early

## Additional Resources

- [LaTeX Workshop Documentation](https://github.com/James-Yu/LaTeX-Workshop)
- [MacTeX Documentation](https://www.tug.org/mactex/)
- [XeLaTeX Guide](https://www.overleaf.com/learn/xelatex)
- [Thai LaTeX Guide](https://linux.thai.net/~thep/thaifonts-scalable/)

## Example Git Ignore

Create a `.gitignore` file to exclude auxiliary files:

```gitignore
# LaTeX auxiliary files
*.aux
*.bbl
*.bcf
*.blg
*.fdb_latexmk
*.fls
*.log
*.out
*.run.xml
*.synctex.gz
*.toc
*.lof
*.lot
*.acn
*.acr
*.alg
*.glg
*.glo
*.gls
*.ist
*.lol
*.nav
*.snm
*.vrb

# OS generated files
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```

---

**Happy LaTeX writing!** 🎓📝
