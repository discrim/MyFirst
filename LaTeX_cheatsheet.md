# LaTeX Cheatsheet
1. [Web-related Icons](#web-related-icons)

### Web-related Icons
Ref: [StackExchange](https://tex.stackexchange.com/questions/190927/linkedin-logo-in-latex)  
Use `fontawesome` package.
``` latex
\documentclass{article}
\usepackage{fontawesome} % For web-related icons
\usepackage{hyperref} % For \href

\begin{document}

\begin{tabular}{l c l}
	\faHome & & Gotham City, NJ \\
	\faPhone & & +1 (123) 456 - 7890 \\
	\faEnvelope & & \href{mailto:bruce.wayne@gmail.com}{bruce.wayne@gmail.com} \\
	\faEnvelopeO & & \href{mailto:bruce.wayne@gotham.edu}{bruce.wayne@gotham.edu} \\
	\faLinkedinSquare & & \href{https://www.linkedin.com/in/bruce-wayne/}{linkedin.com/in/bruce-wayne/} \\
	\faGithubSquare & & \href{https://github.com/batman}{github.com/batman}
\end{tabular}

\end{document}

```
