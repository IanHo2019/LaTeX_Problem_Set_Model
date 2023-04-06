# LaTeX Coding for Writing Solutions to a Problem Set
In this repository, I share my LaTeX coding ([here](./main.tex)) for producing a pdf file with solutions to a problem set in Economics. Using my coding, you can
  * customize a short table (e.g., specifying the column width, merging multiple columns/rows, etc.);
  * draw a picture (e.g., game tree and plot of a function) by `tikz`;
  * customize some mathematical operators/symbols;
  * construct a shaded frame for showing solutions;
  * print external coding (e.g., Stata, MATLAB, R, etc.);
  * construct in-text citations and a reference list.

## Notes for Preamble
* The `babel` package ([documentation](https://ctan.org/pkg/babel?lang=en)) manages culturally-determined typographical rules for a wide range of languages. For a monolingual document, we just need to pass the language (e.g., `english`, `french`, `polish`, etc.) as an optional argument.
