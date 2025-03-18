# Scientific Paper LaTeX Template

This repository contains a professional LaTeX template for scientific papers, with specific focus on agricultural research, sensor systems, and data analysis.

## Files Included

- `paper.tex` - Main LaTeX document with the paper structure
- `references.bib` - BibTeX file for managing references
- `appendices.tex` - File containing appendices with code examples and technical details

## Setup Instructions

### Basic Setup

1. **Copy files to your project folder**: 
   - Place all three files in your project directory
   - Create a `figures` subfolder for your images
   - Create a `build` folder for compilation outputs

2. **Customize the template**:
   - Replace the placeholder title, authors, and content
   - Add your own references to `references.bib`
   - Modify appendices.tex with your code samples and technical information

### VS Code Setup (Recommended)

For the best editing experience with automatic compilation and a clean workspace:

1. **Install required extensions**:
   - [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) by James Yu

2. **Set up project-level settings**:
   - Create a `.vscode` folder in your project root
   - Add a `settings.json` file with the following content:

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOC%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "biber",
            "command": "biber",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "latexmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "pdflatex",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "pdflatex + biber + pdflatex × 2",
            "tools": [
                "pdflatex",
                "biber",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
    "latex-workshop.latex.outDir": "build",
    "latex-workshop.latex.autoBuild.run": "onSave",
    "latex-workshop.latex.clean.enabled": true,
    "latex-workshop.latex.clean.subfolder.enabled": true,
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux", "*.bbl", "*.blg", "*.idx", "*.ind", "*.lof", 
        "*.lot", "*.out", "*.toc", "*.acn", "*.acr", "*.alg", 
        "*.glg", "*.glo", "*.gls", "*.fls", "*.log", 
        "*.fdb_latexmk", "*.synctex.gz"
    ],
    "latex-workshop.view.pdf.viewer": "tab"
}
```

3. **Project structure**:
```
project-folder/
├── .vscode/
│   └── settings.json
├── build/         # Compilation artifacts go here
├── figures/       # Place images here
├── paper.tex      # Main LaTeX document
├── references.bib # References
└── appendices.tex # Appendices
```

This setup will:
- Automatically compile your LaTeX documents when you save them
- Place all build artifacts in the `build` folder to keep your workspace clean
- Display PDFs in a VS Code tab for easy viewing
- Handle bibliography processing with biber

## Manual Compilation Instructions

If you're not using VS Code or prefer manual compilation:

```
mkdir -p build
pdflatex -output-directory=build paper.tex
biber build/paper
pdflatex -output-directory=build paper.tex
pdflatex -output-directory=build paper.tex
```

## Template Features

### Document Structure
- Professional title page with author affiliations and corresponding author notation
- Abstract section with proper formatting
- Structured sections: Introduction, Methods, Results, Discussion, Conclusion
- Automatic reference formatting with numeric citations
- Properly formatted appendices with code listings

### Technical Features
- Configured for high-quality math typesetting with amsmath
- Code listing environment optimized for Python with syntax highlighting
- Figure and table captions with proper formatting
- Bibliography style configured for scientific publications
- Support for equations, algorithms, and technical content

## Customization

### Page Layout
The template uses 1-inch margins by default. Modify the geometry package options to change margins.

### Line Spacing
Uncomment the `\onehalfspacing` line for 1.5 line spacing if required by your publication.

### Bibliography Style
The bibliography is configured with:
- Numeric citations
- Author initials first format (e.g., J. Smith)
- DOI inclusion
- No URL, ISBN, or eprint information
- Up to 10 authors before "et al."

### Code Listings
Code listings are formatted with:
- Line numbers
- Syntax highlighting for Python (customizable)
- Break long lines automatically
- Gray background with colored syntax

## System Requirements

- A LaTeX distribution:
  - Windows: [MiKTeX](https://miktex.org/) or [TeX Live](https://tug.org/texlive/)
  - macOS: [MacTeX](https://www.tug.org/mactex/)
  - Linux: TeX Live (`sudo apt install texlive-full` on Ubuntu/Debian)
- Biber for bibliography processing
- VS Code with LaTeX Workshop extension (for the VS Code setup)

## Troubleshooting

### VS Code Issues
- If the PDF viewer doesn't open, try clicking the "View LaTeX PDF" button in the LaTeX Workshop sidebar
- Check the LaTeX Workshop output panel (View → Output → LaTeX Workshop) for error messages
- Ensure that your LaTeX distribution includes all required packages

### Compilation Errors
- Missing packages: If you get "Package not found" errors, install the missing packages via your LaTeX distribution's package manager
- Bibliography issues: Ensure biber is installed and the references.bib file is in the correct location
- Syncing issues: If figures or references don't appear, try running the full compilation sequence manually

### Common LaTeX Issues
- If bibliography doesn't update, ensure you run biber (not bibtex)
- References may require multiple compilations to appear correctly
- For figures, check that the path to your image files is correct
- Check that your images are in supported formats (PDF, PNG, JPEG)

## Tips for Best Results

1. **Figures**: For best results, prepare figures at 300+ DPI in PNG or PDF format
2. **Tables**: Use the booktabs package (already included) for professional tables
3. **Equations**: Number important equations with the equation environment
4. **Citations**: Add all references to references.bib and cite with \cite{key}
5. **Code**: Place longer code samples in the appendices using the lstlisting environment