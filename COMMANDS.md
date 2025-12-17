# Quick Reference: Custom LaTeX Commands

This document provides a quick reference for all custom commands defined in this template.

## Table of Contents
- [Collaboration Commands](#collaboration-commands)
- [Mathematical Commands](#mathematical-commands)
- [Formatting Commands](#formatting-commands)
- [Table Column Types](#table-column-types)
- [Reference Commands](#reference-commands)

---

## Collaboration Commands

### Todo Notes

Color-coded todo notes for different team members. These automatically appear in the "List of Todos" and are hidden when using the `final` document class option.

#### `\forAll{caption}{note}`
Creates a yellow todo note for all authors.

```latex
\forAll{Review introduction}{Please review the introduction section for clarity.}
```

**Appearance:** Yellow highlighted box with "@All" prefix

#### `\forA{caption}{note}`
Creates a green todo note for Author A.

```latex
\forA{Add regression table}{Please add the main regression results table.}
```

**Appearance:** Green highlighted box with "@A" prefix

#### `\forB{caption}{note}`
Creates a blue todo note for Author B.

```latex
\forB{Check citations}{Verify that all citations are formatted correctly.}
```

**Appearance:** Blue highlighted box with "@B" prefix

**To add more authors:** See README.md section on "Adding Coauthors to Todo System"

### Placeholder Marker

#### `\xx`
Inserts a placeholder marker for incomplete sections.

```latex
The results show \xx\ percent increase in productivity.
```

**Appearance:** `<XX>` in magenta color

**Note:** Use `\xx\ ` (with backslash-space) if you need space after the marker.

---

## Mathematical Commands

These commands are defined in `commands.tex`.

### `\Prob`
Probability measure symbol (blackboard bold P).

```latex
The probability measure $\Prob$ is defined on the space $(\Omega, \mathcal{F})$.
```

**Output:** ℙ

**Note:** Previously used `\P`, but changed to `\Prob` to avoid conflicts with LaTeX's paragraph symbol.

### `\as`
Almost sure convergence arrow.

```latex
As $n \to \infty$, we have $X_n \as X$.
```

**Output:** →^(a.s.)

**Full example:**
```latex
$X_n \as X$ if $\Prob(\omega : \lim_{n \to \infty} X_n = X) = 1$
```

---

## Formatting Commands

### `\redtext{text}`
Displays text in red color.

```latex
\redtext{This requires immediate attention!}
```

**Use case:** Highlighting issues or placeholders in drafts

### `\takeaway{text}`
Centers and italicizes text for key takeaways.

```latex
\takeaway{The main result shows a 15\% improvement over baseline methods.}
```

**Appearance:** Centered, italic text

### `\outline{text}`
Displays text in a colored box.

```latex
\outline{
Section plan:
\begin{enumerate}
\item Introduce the problem
\item Present the methodology
\item Discuss results
\end{enumerate}
}
```

**Use case:** Planning section structure, temporary outlines in drafts

---

## Table Column Types

Custom column types for tables, defined in the preamble. Use these in `\begin{tabular}{...}` specifications.

### `C{width}`
Centered column with fixed width.

```latex
\begin{tabular}{C{3cm}C{2cm}C{2cm}}
Header 1 & Header 2 & Header 3 \\
Content & Content & Content \\
\end{tabular}
```

### `L{width}`
Left-aligned column with fixed width.

```latex
\begin{tabular}{L{4cm}C{2cm}}
Description & Value \\
Long description text & 123 \\
\end{tabular}
```

### `R{width}`
Right-aligned column with fixed width.

```latex
\begin{tabular}{L{3cm}R{2cm}}
Item & Price \\
Product A & \$19.99 \\
\end{tabular}
```

### `H`
Hidden column (exists in table but not displayed).

```latex
\begin{tabular}{lHl}
Visible 1 & Hidden & Visible 2 \\
Data 1 & Data 2 & Data 3 \\
\end{tabular}
```

**Use case:** Temporarily hiding columns without deleting them, A/B testing table layouts

**Width specification:** Use any LaTeX length unit: `cm`, `in`, `em`, `pt`, etc.

---

## Reference Commands

### `\backreference{label}`
Shows on which pages a figure, table, or section is referenced.

**Usage:**
1. Define a label: `\label{fig:results}`
2. Add backreference (typically in notes): `\backreference{fig:results}`
3. The system automatically tracks all `\ref{fig:results}` calls

```latex
\begin{figure}[htbp]
\caption{Main Results}
\label{fig:results}
\includegraphics[width=0.8\textwidth]{results.pdf}

{\footnotesize\textit{Notes:} This figure shows the main results.
\backreference{fig:results}}
\end{figure}
```

**Appearance in draft mode:** "Backreferenced: `fig:results` [3, 5, 12]" (showing page numbers)

**In final mode:** Hidden automatically

### Smart Cross-References (cleveref package)

The template includes `cleveref` for intelligent cross-referencing.

#### `\cref{label}`
Automatic "Figure X", "Table Y", "Section Z" formatting.

```latex
See \cref{fig:results} for details.  % Output: "See Figure 3 for details."
The regression results in \cref{tab:main} show...  % Output: "...in Table 2 show..."
```

**Compared to `\ref{}`:**
- `\ref{fig:results}` → "3"
- `\cref{fig:results}` → "Figure 3"

#### `\Cref{label}`
Capitalized version for sentence beginnings.

```latex
\Cref{fig:results} presents the main findings.  % Output: "Figure 3 presents..."
```

#### `\cref{label1,label2,label3}`
Multiple references with smart formatting.

```latex
\cref{fig:a,fig:b,fig:c}  % Output: "Figures 1, 2 and 3"
\cref{tab:1,tab:2}        % Output: "Tables 1 and 2"
```

### Equation References

#### `\eqref{label}`
References equations with automatic parentheses.

```latex
From \eqref{eq:main}, we can derive...  % Output: "From (7), we can derive..."
```

**Compared to `\ref{}`:**
- `\ref{eq:main}` → "7"
- `\eqref{eq:main}` → "(7)"

---

## Citation Commands (natbib)

The template uses `natbib` with Chicago style.

### `\citep{key}`
Parenthetical citation.

```latex
Recent studies \citep{smith2020} show...
```
**Output:** "Recent studies (Smith, 2020) show..."

### `\citet{key}`
Textual citation.

```latex
\citet{smith2020} showed that...
```
**Output:** "Smith (2020) showed that..."

### `\citeauthor{key}`
Author name only.

```latex
According to \citeauthor{smith2020}, ...
```
**Output:** "According to Smith, ..."

### `\citeyear{key}`
Year only.

```latex
Smith \citeyear{smith2020} demonstrated...
```
**Output:** "Smith 2020 demonstrated..."

---

## Adding Your Own Commands

To add custom commands, edit `commands.tex`:

```latex
% In commands.tex:
\newcommand{\Expect}{\mathbb{E}}  % Expectation operator
\newcommand{\Var}{\text{Var}}     % Variance operator
```

Then use in your document:

```latex
The expectation is $\Expect[X] = 0$ with variance $\Var(X) = 1$.
```

**Best practices:**
- Use descriptive command names
- Add comments explaining what each command does
- Avoid redefining standard LaTeX commands
- Group related commands together

---

## Quick Tips

1. **Draft vs Final Mode:**
   - Draft: `\documentclass[11pt]{article}` → shows todos, ToC, backreferences
   - Final: `\documentclass[11pt, final]{article}` → hides all draft features

2. **Caption before Label:**
   Always put `\caption{}` before `\label{}` for correct cross-referencing:
   ```latex
   \begin{figure}
   \caption{My Figure}  % Caption first
   \label{fig:myfig}    % Label second
   ...
   \end{figure}
   ```

3. **Compilation Order:**
   For references and citations to work: `pdflatex → bibtex → pdflatex → pdflatex`
   Or simply: `make`

4. **Finding Command Definitions:**
   - Custom commands: `commands.tex`
   - Template commands (`\forAll`, `\backreference`, etc.): `preamble.tex`
   - Package commands: Check package documentation

---

**For more information, see:** [README.md](README.md)
