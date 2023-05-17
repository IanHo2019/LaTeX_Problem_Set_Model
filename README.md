# LaTeX Coding for Writing Solutions to a Problem Set
In this repository, I share my LaTeX coding ([here](./main.tex)) for producing a pdf file with solutions to a problem set in Economics. Using my coding, you can
  * construct a shaded frame for showing solutions;
  * customize some mathematical operators/symbols;
  * customize a short table (e.g., specifying the column width, merging multiple columns/rows, etc.);
  * draw a picture (e.g., game tree and plot of a function) by `tikz`;
  * print out external coding (e.g., Stata, MATLAB, R, etc.);
  * construct in-text citations and a reference list.

## Language and Font
* The `babel` package ([documentation](https://ctan.org/pkg/babel)) manages culturally-determined typographical rules for a wide range of languages. For a monolingual document, we just need to pass the language (e.g., `english`, `french`, `polish`, etc.) as an argument.
* The `times` package supports Times Roman text and matching mathematics. The official website of this package says it is obsolete and nowadays the `mathptmx` package ([documentation](https://ctan.org/pkg/mathptmx)) is more popular. I keep using `times` just because I prefer its font for mathematics.

## Layout
* The `geometry` package ([documentation](https://ctan.org/pkg/geometry)) provides a flexible way to customize page layout. For example, we can specify the paper size by name (e.g., `letterpaper` and `a4paper`), specify the size of the margins (including `left`, `right`, `top`, `bottom`, etc.), and more.
* The `setspace` package ([documentation](https://ctan.org/pkg/setspace)) helps us to set the spacing between lines in a document. My eyesight is not good so I usually set the a one half spacing. We can use the command `\setstretch{baselinestretch}{#}` to customize the spacing. If a different spacing is required somewhere in the document, the `spacing` environment can help us.
```latex
\begin{spacing}{2.5}
A larger baselinestretch is used.
\end{spacing}
```

## Title and Footnote Design
* The `titlesec` package ([documentation](https://ctan.org/pkg/titlesec)) helps us to customize title styles for chapter, section, subsection, etc.
  * I use `\titleformat*{\section}` to set the font size of section title to be `large` and font style to be bold (`\bfseries`).
  * I use `\titlespacing*{\section}` to specify the spacing around the section title. The first argument specifies the *left* margin, the second specifies the vertical space *before* the title, and the last one specifies the separation between title and the following text. Note that the starred version kills the indentation of the paragraph following the title.
* The `titling` package ([documentation](https://ctan.org/pkg/titling)) controls the typesetting of the `\maketitle` command and `\thanks` commands.
  * I use the `\setlength{\droptitle}{#}` command from this package to change the vertical position of the title. Note that if `#` is a positive value then the title will be lowered, and if `#` is a negative value, then the title will be raised.
  * I use the following two lines to kill the indention of the "thanks" footnote.
```latex
\settowidth{\thanksmarkwidth}{*}
\setlength{\thanksmargin}{-\thanksmarkwidth}
```
* The `footmisc` package ([documentation](https://ctan.org/pkg/footmisc)) has a set of options to change the typesetting of footnotes. Here I only use two among them:
  * `flushmargin`: This option sets the footnote marker flush with the text of the footnote; in other words, it kills the idention of the first line of each footnote.
  * `bottom`: This option forces footnotes to the bottom of the page. If `\raggedbottom` is in force, then the excess space goes above the footnotes if any are present.

## Color
I use the `xcolor` package ([documentation](https://ctan.org/pkg/xcolor)) to select colors for hyper references, url links, plotting figures, etc. The basic color (e.g., blue and red) can be used directly by typing `\color{color_name}` to use it in the document. If additional colors are needed, I suggest to first name the color (for convenient future use) by the `\definecolor{name}{RGB}{#,#,#}` command, and then use the `\color{color_name}` command as before. The [RGB model](https://en.wikipedia.org/wiki/RGB_color_model) is my often-used model, but other models (e.g., `rgb`, `HTML`, `HSB`, etc.) are also available.

A good guideline for `xcolor` beginners can be found [here](https://steeven9.github.io/USI-LaTeX/html/packages_hyperref_babel_xcolor3.html).

## Frame
To highlight my solution to each question, I use the `shaded` environment from the `framed` package ([documentation](https://ctan.org/pkg/framed)). The color for shading can be customized by using the `\definecolor{shadecolor}` command. I use very slight gray for shading.

## Math

### Packages
* The `amsmath` package ([documentation](https://ctan.org/pkg/amsmath)) is a principal package for mathematical typesetting. Once `amsmath` is loaded, the packages `amsbsy` (for bold symbols), `amsopn` (for operator names) and `amstext` (for text embedded in mathematics) are also loaded.
* The `amssymb` package provides an extended symbol collection, especially including some additional binary relation symbols (e.g., `\boxdot`, `\boxplus`, `\boxtimes`). Something noteworthy is that this package provides the `\mathbb{ }` command for producing blackboard bold characters.
* The `bbm` package ([documentation](https://ctan.org/pkg/bbm)) provides blackboard variants of characters in math mode. The command is `\mathbbm{ }`, which produces the blackboard bold characters slighly different from those produced by `\mathbb{ }`. My preference between `\mathbb{ }` and `\mathbbm{ }` changes across different letters. For example, I prefer using `\mathbbm{R}` to denote real set, but prefer using `\mathbb{H}` to denote (null/alternative) hypothesis.
* The `dutchcal` package ([documentation](https://ctan.org/pkg/dutchcal)) reworks the mathematical calligraphic font ESSTIX13 in the package `esstix` ([documentation](https://ctan.org/pkg/esstix)) and adds a bold version. I use its command `\mathcal{ }` to produce special letters denoting support sets in Probability Theory and Statistics.

### Operators & Symbols
I contruct the following operators and symbools
```latex
\DeclareMathOperator*{\plim}{plim}    % probability limit
\DeclareMathOperator*{\argmin}{argmin}    % arguments of the minima
\DeclareMathOperator*{\argmax}{argmax}    % arguments of the maxima
\newcommand*{\defeq}{\overset{\mathrm{def}}{=\joinrel=}}    % definitional equality
\newcommand*{\seteq}{\overset{\mathrm{set}}{=\joinrel=}}    % equality by setting
\newcommand{\smp}[1]{\left(#1\right)}    % parentheses whose size is flexible
\newcommand{\medp}[1]{\left[#1\right]}    % brackets whose size is flexible
\newcommand{\bgp}[1]{\left\{#1\right\}}    % curly brackets whose size is flexible
\newcommand{\abs}[1]{\left\lvert#1\right\rvert}    % pipes (for absolute values) whose size is flexible
\newcommand{\norm}[1]{\left\lVert#1\right\rVert}    % double pipes (for vector norms) whose size is flexible
```

## Table
* The `float` package ([documentation](https://ctan.org/pkg/float)) improves the interface for defining floating objects, such as figures and tables. By default, we can use something `[h]` (here), `t` (top), and `b` (bottom) to determine the figure positioning; however, these positioning options are not strong --- LaTeX still has some flexibility to select the best position in its mind. To precisely fix the position of a floating objects, we have to use the parameter `[H]` from `float`.
* The `bookstabs` package ([documentation](https://ctan.org/pkg/booktabs)) providing extra commands for enhancing the quality of tables. My often-used commands include
  * `\cmidrule(lr){a-b}`, giving us a horizontal line extending over only some of the columns (from the *a*th column to the *b*th column). The `(lr)` option is for trimming: creating spaces to separate the lines among columns (left and right sides).
  * `\addlinespace[5pt]`, putting an extra space between certain rows of a table. The amount of space can be specified in the optional argument `[ ]`.
* The `caption` ([documentation](https://ctan.org/pkg/caption)) and `subcaption` ([documentation](https://ctan.org/pkg/subcaption)) packages allow us to customize the captions and subcaptions in floating environments like figure, table, subfigure, and subtable.
* The `multirow` package ([documentation](https://ctan.org/pkg/multirow)) permits us to create tabular cells spanning multiple rows. The most often used command may be `\multirow[vpos]{nrows}{width}{text}`, where
  * `vpos` specifies the vertical positioning of the text in the multirow block (options include `c`, `t`, and `b`);
  * `nrows` is the number of rows to span;
  * `width` specifies the width to which the text is to be set (if `*` is used, the text's natural width will be used).
* The `siunitx` package ([documentation](https://ctan.org/pkg/siunitx)) ensures the exact appearance of numbers and units. In particular, it provides the `S` column type for decimal alignments and units in the `tabular` environment.

## Figure
* The `graphicx` package ([documentation](https://ctan.org/pkg/graphicx)) provides some useful optional arguments to the `\includegraphics` command. This package is one of LaTeX "required" packages.
* The `pifont` package ([documentation](https://ctan.org/pkg/pifont)) is distributed as part of the [psnfss](https://ctan.org/pkg/psnfss) and provides the `\ding{#}` command for printing some special symbols. A table of the available symbols can be found in its documentation.
* The `asymptote` package ([documentation](https://ctan.org/pkg/asymptote)) provides a lot of commands for 2D and 3D high-quality level technical drawing.
* The `pgfplots` package ([documentation](https://ctan.org/pkg/pgfplots)) allows us to draw high-quality function plots. In particular, it supports axis scaling, axis ticks custimization, axis labels custimization, legend entries, etc. Note that `pgfplots` has been written with backwards compatibility; thus, new features occasionally lead to a different behavior. Therefore, I suggest to activate explicitly new features or bugfixes by writing `\pgfplotsset{compat=1.18}` in your preamble, where `compat=1.18` is the highest compatibility level nowadays. The lowest level is `compat=1.3`.
* `asymptote` and `pgfplots` provide basic functionalities and load the `tikz` and `pgf` packages ([documentation](https://www.ctan.org/pkg/pgf)) automatically. For special features, special libraries must be included. The libraries I use include `calc` (making complex coordinate calculations), `calligraphy` (enabling calligraphic style drawings), `decorations.pathreplacing` (defining decorations that replace the to-be-decorated path by another path), `patterns` (providing different patterns for filling in area), and `shapes.misc` (defining additional shapes).
* A good user manual for `tikz` and `pgf` packages is [here](https://tikz.dev).

## List
The `enumitem` package ([documentation](https://ctan.org/pkg/enumitem)) controls over the layout of the three basic list environments: `enumerate`, `itemize` and `description`. For example, we can use the `\setenumerate` command to customize labels, identation, vertical and horizontal spacing, etc.

## Hypertext Links and Citations
* The `hyperref` package ([documentation](https://ctan.org/pkg/hyperref)) handles cross-referencing commands in LaTeX to produce hypertext links in the document. This package has lots of options, and here I only use two of them:
  * `colorlinks=true` tells LaTeX to colors the text of links and anchors. The colors chosen depend on the the type of link: `linkcolor` (for normal internal links; default is "red"), `anchorcolor` (for anchor text; default is "black"), `citecolor` (for bibliographical citations in text; default is "green"), `filecolor` (for URLs which open local files; default is "cyan"), `menucolor` (for Acrobat menu items; default is "red"), `runcolor` (for run links; default is the same as `filecolor`), and `urlcolor` (for linked URLs; default is "magenta").
  * `allcolors=blue` tells LaTeX to set all color options as "blue".
* The `csquotes` package ([documentation](https://ctan.org/pkg/csquotes)) provides advanced facilities for inline and display quotations. I include this package due to the requirement of `biblatex` (see the next point).
* The `biblatex` package ([documentation](https://ctan.org/pkg/biblatex)) a complete reimplementation of the bibliographic facilities provided by LaTeX. The package options I use include
  * `style` specifies the bibliography style, such as `authoryear`, `authortitle`, `mla`, `apa`, etc.
  * `backend` specifies the database backend, such as `biber` supporting US-ASCII, 8-bit encodings, UTF-8, on-the-fly reencoding, locale-specific sorting, and many other features.
  * `sorting` specifies the sorting order of the bibliography. For example, `nyt` means ordering by name, year, and title.
  * `natbib=true` loads compatibility module which provides aliases for the citation commands of the `natbib` package ([documentation](https://ctan.org/pkg/natbib)). I use this option because of the additional text citation commands (e.g., `\citep`, `\citet`, `\citealp`, etc.). A good guideline can be found [here](https://journals.aas.org/natbib/).
* To cite articles, reports, books, etc., I create a [BibTeX](https://en.wikipedia.org/wiki/BibTeX) database stored as a bib file with a name of "reference". We can enter the citation information by hand, or download it from corresponding reference websites. For example, on [ScienceDirect](https://www.sciencedirect.com/), we first click the "cite" button below each article's authors' information, then click "Export citation to BibTeX", and finally get a bib file with citation information. After uploading the bib file to your LaTeX folder, you need to use `\addbibresource{reference.bib}` to load it. For customizing a BibTeX entry, [Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#BibTeX) provides a good guideline. In addition, some of my classmates at UW-Madison like to use [Mendeley](https://www.mendeley.com/) to do reference management; this software was acquired by Elsevier in 2013, so it is well competible with Elsevier's website ScienceDirect.

## Code Listing
The `listings` package ([documentation](https://ctan.org/pkg/listings)) enables the user to typeset programming code within LaTeX. Keywords, comments, and strings can be typeset using different styles (default is **bold** for keywords, *italic* for comments, and no special style for strings). Supported languages include "C++", "HTML", "Java", "Mathematica", "Matlab", "Python", "R", "SAS", "TeX", etc. Sadly, "Stata" is not supported, but we can use `\lstdefinelanguage{Stata}{...}` to add it.

The `listings` package provides a lot of commands (e.g., `\lstset`) and options for customizing the styles of typesetting programming code. Two brief guildlines are provided by [Overleaf](https://www.overleaf.com/learn/latex/Code_listing) and [Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Source_Code_Listings).

I also use the `\newcommand` command to create a new command `\comp{...}` for printing some programming commands in a specific font: `\fontfamily{cmtt}` (Computer Modern Typewriter). LaTeX typesets documents using the Computer Modern typeface family, and a full list can be found [here](https://www.overleaf.com/learn/latex/Font_typefaces).
