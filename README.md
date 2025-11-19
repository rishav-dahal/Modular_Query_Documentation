# Modular Query Refinement Using Latent Dirichlet Allocation

A major project implementing query refinement techniques using LDA, LSI, and other NLP methods for medical symptom analysis.

## Prerequisites

### All Platforms
- Git (for version control)
- A LaTeX distribution
- A text editor or LaTeX IDE

## Installation

### Windows

1. **Install MiKTeX** (LaTeX Distribution)
   - Download from [https://miktex.org/download](https://miktex.org/download)
   - Run the installer and follow the setup wizard
   - Choose "Install missing packages on-the-fly: Yes"

2. **Install a LaTeX Editor** (Optional but recommended)
   - **TeXstudio**: [https://www.texstudio.org/](https://www.texstudio.org/)
   - **TeXmaker**: [https://www.xm1math.net/texmaker/](https://www.xm1math.net/texmaker/)
   - **VS Code** with LaTeX Workshop extension

3. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd Major_Project
   ```

### macOS

1. **Install MacTeX** (LaTeX Distribution)
   ```bash
   # Using Homebrew
   brew install --cask mactex
   
   # Or download from: https://www.tug.org/mactex/
   ```

2. **Install a LaTeX Editor** (Optional)
   ```bash
   # TeXstudio
   brew install --cask texstudio
   
   # Or use VS Code with LaTeX Workshop extension
   ```

3. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd Major_Project
   ```

### Linux (Ubuntu/Debian)

1. **Install TeX Live** (LaTeX Distribution)
   ```bash
   sudo apt update
   sudo apt install texlive-full
   sudo apt install texlive-bibtex-extra biber
   ```

2. **Install a LaTeX Editor** (Optional)
   ```bash
   # TeXstudio
   sudo apt install texstudio
   
   # Or use VS Code
   sudo snap install code --classic
   ```

3. **Clone the Repository**
   ```bash
   git clone <repository-url>
   cd Major_Project
   ```

### Linux (Fedora/RHEL)

1. **Install TeX Live**
   ```bash
   sudo dnf install texlive-scheme-full
   sudo dnf install biber
   ```

2. **Install TeXstudio**
   ```bash
   sudo dnf install texstudio
   ```

## Project Structure

```
Major_Project/
├── main.tex              # Main document file
├── ref.bib              # Bibliography references
├── chapters/            # Chapter files
│   ├── Introduction.tex
│   ├── Problem_Statement.tex
│   ├── Literature_review.tex
│   ├── proposed_methodology.tex
│   ├── Tools and Technique.tex
│   ├── Result_And_Discussion.tex
│   ├── appendix.tex
│   └── ...
├── Figures/             # Images and diagrams
│   ├── Sprint.png
│   ├── NCITlogo.PNG
│   ├── v2 - LSI with tf-idf/
│   └── Frontend Snapshot/
└── README.md
```

## Building the Document

### Using Command Line

#### Windows (Command Prompt or PowerShell)
```bash
pdflatex -interaction=nonstopmode -synctex=1 main.tex
biber main
pdflatex -interaction=nonstopmode main.tex
```

#### macOS/Linux (Terminal)
```bash
pdflatex -interaction=nonstopmode -synctex=1 main.tex
biber main
pdflatex -interaction=nonstopmode main.tex
```

**Command Explanation:**
- `-interaction=nonstopmode` - Continues compilation even if errors occur
- `-synctex=1` - Enables synchronization between PDF and source (for editors)
- Run `pdflatex` twice after `biber` to resolve all cross-references

### Quick Build Script

#### Windows (PowerShell)
Create a file named `build.ps1`:
```powershell
pdflatex -interaction=nonstopmode -synctex=1 main.tex
biber main
pdflatex -interaction=nonstopmode main.tex
Write-Host "Build complete! Check main.pdf"
```

Run with: `.\build.ps1`

#### Windows (Batch)
Create a file named `build.bat`:
```batch
@echo off
pdflatex -interaction=nonstopmode -synctex=1 main.tex
biber main
pdflatex -interaction=nonstopmode main.tex
echo Build complete! Check main.pdf
```

Run with: `build.bat`

#### macOS/Linux (Bash)
Create a file named `build.sh`:
```bash
#!/bin/bash
pdflatex -interaction=nonstopmode -synctex=1 main.tex
biber main
pdflatex -interaction=nonstopmode main.tex
echo "Build complete! Check main.pdf"
```

Make it executable and run:
```bash
chmod +x build.sh
./build.sh
```

### Why Multiple Compilations?
1. First `pdflatex` - Generates auxiliary files and references
2. `biber` - Processes bibliography from `ref.bib`
3. Second `pdflatex` - Incorporates bibliography and resolves cross-references

### Using LaTeX Editors

#### TeXstudio / TeXmaker
1. Open `main.tex`
2. Set bibliography tool to **Biber** (Options → Configure → Build → Default Bibliography Tool)
3. Press **F5** (or click "Build & View")

#### VS Code with LaTeX Workshop
1. Install "LaTeX Workshop" extension
2. Open `main.tex`
3. Press **Ctrl+Alt+B** (Windows/Linux) or **Cmd+Option+B** (Mac) to build
4. The extension automatically handles multiple compilations and biber

## Cleaning Build Files

### Windows
```bash
del /Q *.aux *.log *.out *.toc *.lof *.lot *.fls *.fdb_latexmk *.synctex.gz *.bbl *.blg *.bcf *.run.xml
```

### macOS/Linux
```bash
rm -f *.aux *.log *.out *.toc *.lof *.lot *.fls *.fdb_latexmk *.synctex.gz *.bbl *.blg *.bcf *.run.xml
```

## Troubleshooting

### Missing Packages Error
- **Windows**: MiKTeX will prompt to install missing packages automatically
- **macOS/Linux**: Install the full TeX Live distribution or install specific packages:
  ```bash
  # For Ubuntu/Debian
  sudo apt install texlive-latex-extra texlive-fonts-recommended
  
  # For macOS
  sudo tlmgr install <package-name>
  ```

### Bibliography Not Showing
- Ensure you run `biber` (not `bibtex`)
- Delete `.aux`, `.bbl`, `.bcf` files and rebuild
- Check that `ref.bib` exists and is properly formatted

### Font Issues
- Install required fonts or use fallback fonts
- For Times/Courier fonts, ensure `texlive-fonts-recommended` is installed

