# Mathematica plot options

A native **Wolfram Mathematica notebook** (`PlotOptions.nb`) containing reusable defaults and colour palettes for 2D plots: framed axes, zero-reference grid lines, Latin Modern typography, and LaTeX labels through MaTeX.

## Dependencies

- **Wolfram Mathematica** with a notebook front end to open and evaluate `.nb` files.
- **[MaTeX](https://github.com/szhorvat/MaTeX)**, a Wolfram paclet for rendering LaTeX. Install on supported versions using `ResourceFunction["MaTeXInstall"][]`.
- **A LaTeX distribution** (TeX Live, MiKTeX or MacTeX) with `pdflatex` and the packages needed by MaTeX (including `standalone`, `exscale`, `lmodern`) and the `color` package used in the notebook.
- **Ghostscript** for MaTeX. See [MaTeX setup instructions](https://szhorvat.net/pelican/latex-typesetting-in-mathematica.html) for version and configuration details.
- **Optional: LM Roman 12** installed as a system font. Otherwise change `PlotFontFamily` at the start of the notebook's input cell.

After installing MaTeX, check it in Mathematica with `MaTeX["x^2"]`. Depending on your environment, you may need to configure the paths to LaTeX and Ghostscript.

## Usage

1. Clone or download this repository.
2. Open **`PlotOptions.nb`** in Mathematica.
3. Evaluate the input cell using **Shift+Enter**.
4. Produce plots in the same kernel session.

Example after evaluating the notebook:

```wl
plot = Plot[
  Sin[x], {x, 0, 4 Pi},
  FrameLabel -> {MaTeX["x"], MaTeX["\\sin x"]},
  PlotLabel -> MaTeX["f(x)=\\sin x"]
];
```

The notebook creates palettes such as `RGBString`, `RGBStringLighter`, `RGBStringDarker`, `RGBStringTemperature`, and `RGBStringAlternative115`. For a single plot use, for example, `PlotStyle -> RGBString[[13]]`.

The default styles affect `Plot`, `ListPlot`, `ListLinePlot`, `LogPlot`, `LogLogPlot`, and `LogLinearPlot`. `ContourPlot` gets frame, grid, and label styling, but not the default plot palette. Calls to `SetOptions` modify defaults **for the current kernel session**.

**File format:** This is a genuine editable Mathematica notebook (`.nb`). A `.wl` file is a plain-text Wolfram Language script, which is optional and not required here.

## Using figures in Overleaf

Overleaf cannot execute Mathematica notebooks. Generate figures in Mathematica and export them as PDF:

```wl
Export["sine-plot.pdf", plot];
```

Upload the PDF to Overleaf, then in the LaTeX document:

```tex
% Preamble:
\usepackage{graphicx}

% Document:
\includegraphics[width=0.8\linewidth]{sine-plot.pdf}
```

## License

Licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. See [LICENSE](LICENSE) and the [official license summary](https://creativecommons.org/licenses/by/4.0/). If you share or adapt the work, attribute **phygibs**, link to [this repository](https://github.com/phygibs/mathematica-styles) and the license, and indicate any changes.

Mathematica, MaTeX, LaTeX, Ghostscript, and font software are third-party dependencies subject to their own terms.

## References

- [MaTeX source repository](https://github.com/szhorvat/MaTeX)
- [MaTeX installation resource](https://resources.wolframcloud.com/FunctionRepository/resources/MaTeXInstall)
- [MaTeX requirements and setup](https://szhorvat.net/pelican/latex-typesetting-in-mathematica.html)
