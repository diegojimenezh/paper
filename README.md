# Academic Paper LaTeX Template

A comprehensive LaTeX template for academic papers in economics, statistics, and related fields. This template provides professional formatting, collaboration tools, and extensive examples to help you write and format your research papers.

**Credits:** Anne Fournier was instrumental in making this template readable and user-friendly.

## Features

### Document Formatting
- Professional typography with `newpx` fonts and `microtype` for improved readability
- Flexible spacing options (single, 1.5x, double spacing)
- Chicago bibliography style (easily customizable)
- Automatic table of contents generation
- Smart cross-referencing with `cleveref`
- Custom appendix formatting with OA- prefixes

### Collaboration Tools
- **Todo Notes**: Color-coded notes for different coauthors (`\forAll`, `\forA`, `\forB`)
- **Backreferences**: Track where figures, tables, and sections are cited
- **Draft/Final Modes**: Automatically hide todos and ToC in final mode
- **Placeholder Command**: `\xx` for marking incomplete sections

### Examples Included
- Abstract, introduction, and section templates
- Table formatting with custom column types
- Figure examples (single and subfigures)
- Mathematical environments (theorems, lemmas, definitions, proofs)
- Equation numbering and cross-references
- Bibliography examples (books, articles, working papers, data sources)

## Quick Start

### Prerequisites

- **TeX Distribution**: TeX Live 2018 or later (MacTeX on macOS, MiKTeX on Windows)
- **Required Packages**: Most packages are included in standard TeX distributions

### Installation

1. Clone or download this repository:
   ```bash
   git clone https://github.com/diegojavierjimenez/paper.git
   cd paper
   ```

2. Compile the document:
   ```bash
   pdflatex paper.tex
   bibtex paper
   pdflatex paper.tex
   pdflatex paper.tex
   ```

3. The compiled PDF will be `paper.pdf`

### Using the Template

1. Edit `paper.tex` to set your title, authors, and date
2. Write your content in the `sections/` files or create new ones
3. Add your references to `library.bib`
4. Place figures in the `figures/` directory
5. Compile as shown above

## File Structure

```
.
├── paper.tex              # Main document file
├── preamble.tex           # Package imports and formatting settings
├── preamble_appendix.tex  # Appendix-specific setup
├── commands.tex           # Custom LaTeX commands
├── library.bib            # Bibliography database
├── sections/              # Content files
│   ├── template_abstract.tex
│   ├── section_introduction.tex
│   ├── section_debugging.tex
│   ├── section_math.tex
│   ├── template_table.tex
│   └── template_figure.tex
├── figures/               # Place your figures here
├── .gitattributes         # Git configuration for LaTeX
├── .gitignore             # Git ignore rules
└── README.md              # This file
```

## Compilation

### Manual Compilation

The standard LaTeX workflow with BibTeX:
```bash
pdflatex paper.tex
bibtex paper
pdflatex paper.tex
pdflatex paper.tex
```

Note: You need to run `pdflatex` twice after `bibtex` to resolve all references.

## Customization Guide

### Switching Draft/Final Mode

Add `final` option to the document class in `paper.tex`:
```latex
\documentclass[11pt, final]{article}  % Hides todos, ToC, and list of todos
```

### Adding Coauthors to Todo System

In `preamble.tex`, add new todo commands for additional authors:
```latex
\newcommand{\forC}[2]{\td[color=orange!40,inline,caption={\thetodoListItems:
    @C -- #1}]{\textbf{@C} -- #2}}
```

### Changing Paper Size or Margins

Edit `preamble.tex`:
```latex
\geometry{letterpaper}    % or a4paper
\geometry{margin=2.5cm}   % adjust margins
```

### Using Different Bibliography Styles

In `paper.tex`, change the bibliography style:
```latex
\bibliographystyle{chicago}  % or aer, apa, plain, etc.
```

## Custom Commands

### Collaboration Commands
- `\forAll{caption}{note}` - Yellow todo for all authors
- `\forA{caption}{note}` - Green todo for Author A
- `\forB{caption}{note}` - Blue todo for Author B
- `\xx` - Placeholder marker (shows as <XX> in magenta)
- `\backreference{label}` - Shows where a label is referenced

### Mathematical Commands
- `\Prob` - Probability measure (ℙ)
- `\as` - Almost sure convergence arrow

### Formatting Commands
- `\redtext{text}` - Red colored text
- `\takeaway{text}` - Centered italic text for key takeaways
- `\outline{text}` - Text in a colored box

### Table Column Types
- `C{width}` - Centered column with fixed width
- `L{width}` - Left-aligned column with fixed width
- `R{width}` - Right-aligned column with fixed width
- `H` - Hidden column (exists but not displayed)

## Tips and Best Practices

### Tables
- Use `\begin{adjustbox}{width=\textwidth}` to fit wide tables
- Use `booktabs` commands: `\toprule`, `\midrule`, `\bottomrule`
- Place `\caption{}` before `\label{}` for correct referencing
- Use the `backreference` command in table notes to track citations

### Figures
- Save figures in PDF format when possible for best quality
- Use `\includegraphics[width=0.8\textwidth]{filename}` without file extension
- Place `\caption{}` before `\label{}` for correct referencing

### Cross-References
- Use `\cref{label}` for automatic "Figure X", "Table Y", "Section Z"
- Use `\eqref{label}` for equation references with parentheses
- Use `\ref{label}` for plain number references

### Bibliography
- Use `\citep{}` for parenthetical citations: (Author, Year)
- Use `\citet{}` for textual citations: Author (Year)
- Use `\citeauthor{}` and `\citeyear{}` for author-only or year-only citations

## Troubleshooting

### Common Errors

**"File not found" for sections/figures**
- Check that file paths are correct and case-sensitive
- Ensure `figures/` directory exists

**Bibliography not showing**
- Run the complete compilation sequence: `pdflatex` → `bibtex` → `pdflatex` → `pdflatex`
- Check that `library.bib` has no syntax errors

**Overfull hbox warnings**
- The `microtype` package helps reduce these
- Manually break long URLs or add `\sloppy` to problem paragraphs

**Package conflicts**
- Package loading order matters! See `preamble.tex` for correct order
- `hyperref` should load before `cleveref`
- `titlesec` should load before `hyperref`

### Getting Help

- Check the LaTeX Wikibook: https://en.wikibooks.org/wiki/LaTeX
- TeX Stack Exchange: https://tex.stackexchange.com/
- Report template issues: https://github.com/diegojavierjimenez/paper/issues

## Advanced Features

### Git Integration

The template includes `.gitattributes` for proper LaTeX file handling in git. The aux files and build outputs are ignored via `.gitignore`.

### Appendix System

The template has a sophisticated appendix system:
- Separate numbering with OA- prefix
- Independent table of contents for appendix
- Figures and tables automatically prefixed

### Output Directory

By default, auxiliary files go to `.textmp/` directory (set in `paper.tex` line 2). This keeps your working directory clean.

## Version Control

Latest version available at: https://github.com/diegojavierjimenez/paper

To update to the latest version:
```bash
git pull origin main
```

## License

See the LICENSE file for details.

## Acknowledgments

- Anne Fournier for making this template readable and user-friendly
- Contributors and users who have provided feedback

---

**Happy writing!** If you find this template useful, please consider citing it or giving it a star on GitHub.
