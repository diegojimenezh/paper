# Figures Directory

Place your figure files (PNG, PDF, JPG, etc.) in this directory.

The preamble is configured to look for figures here using:
```latex
\graphicspath{{./figures/}}
```

This means you can reference figures by filename without the full path:
```latex
\includegraphics[width=0.5	extwidth]{my_figure.pdf}
```

