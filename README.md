# LaTeX Coding for Writing Solutions to a Problem Set
In this repository, I share my LaTeX coding ([here](./main.tex)) for producing a pdf file with solutions to a problem set in Economics. Using my coding, you can
  * customize a short table (e.g., specifying the column width, merging multiple columns/rows, etc.);
  * draw a picture (e.g., game tree and plot of a function) by `tikz`;
  * customize some mathematical operators/symbols;
  * construct a shaded frame for showing solutions;
  * print external coding (e.g., Stata, MATLAB, R, etc.);
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
