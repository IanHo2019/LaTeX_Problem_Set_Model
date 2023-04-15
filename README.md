# LaTeX Coding for Writing Solutions to a Problem Set
In this repository, I share my LaTeX coding ([here](./main.tex)) for producing a pdf file with solutions to a problem set in Economics. Using my coding, you can
  * customize a short table (e.g., specifying the column width, merging multiple columns/rows, etc.);
  * draw a picture (e.g., game tree and plot of a function) by `tikz`;
  * customize some mathematical operators/symbols;
  * construct a shaded frame for showing solutions;
  * print external coding (e.g., Stata, MATLAB, R, etc.);
  * construct in-text citations and a reference list.

## Notes for Preamble
* The `babel` package ([documentation](https://ctan.org/pkg/babel)) manages culturally-determined typographical rules for a wide range of languages. For a monolingual document, we just need to pass the language (e.g., `english`, `french`, `polish`, etc.) as an argument.
* The `times` package supports Times Roman text and matching mathematics. The official website of this package says it is obsolete and nowadays the `mathptmx` package ([documentation](https://ctan.org/pkg/mathptmx)) is more popular. I keep using `times` just because I prefer its font for mathematics.
* The `geometry` package ([documentation](https://ctan.org/pkg/geometry)) provides a flexible way to customize page layout. For example, we can specify the paper size by name (e.g., `letterpaper` and `a4paper`), specify the size of the margins (including `left`, `right`, `top`, `bottom`, etc.), and more.
