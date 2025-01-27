﻿---
title: Building a Platform for the Escape Game Community \break
  \large COM3610 Dissertation Project
subtitle: 
author: |
  Simon Fish | Supervisor: Andrew Stratton \
  This report is submitted in partial fulfilment of the requirement for \
  the degree of Computer Science with a Year in Industry by Simon Fish.
geometry: left=37mm,right=25mm,top=25mm,bottom=25mm
papersize: a4
links-as-notes: true
bibliography: [bibliography.bib]
link-citations: true
table-of-contents: true
documentclass: report
header-includes: |
  \usepackage{lscape}
  \newcommand{\blandscape}{\begin{landscape}}
  \newcommand{\elandscape}{\end{landscape}}
  \usepackage{fancyhdr,ragged2e}
  \fancyhead{}
  \fancyhead[CO,CE]{\leftmark}
  \pagestyle{fancy}
---
\makeatletter

\newcommand\frontmatter{%
    \cleardoublepage
  %\@mainmatterfalse
  \pagenumbering{roman}}

\newcommand\mainmatter{%
    \cleardoublepage
 % \@mainmattertrue
  \pagenumbering{arabic}}

\newcommand\backmatter{%
  \if@openright
    \cleardoublepage
  \else
    \clearpage
  \fi
 % \@mainmatterfalse
   }
\makeatother
\frontmatter
<!-- First page -->
\hspace{0pt}
\vfill
\subsubsection*{Signed Declaration} 
\addcontentsline{toc}{chapter}{Signed Declaration}

\begin{center}

All sentences or passages quoted in this report from other people's work have
been specifically acknowledged by clear cross-referencing to author, work and
page(s). Any illustrations that are not the work of the author of this report
have been used with the explicit permission of the originator and are
specifically acknowledged. I understand that failure to do this amounts to
plagiarism and will be considered grounds for failure in this project and the
degree examination as a whole.

Simon Fish
\end{center}
\vfill
\hspace{0pt}
\pagebreak
<!-- Abstract -->
<!--
This should be two or three short paragraphs (100-150 words total), summarising
the dissertation. It is important that this is not just a restatement of the
original project outline. A suggested flow is background, project aims and main
achievements. A bad abstract would have a final paragraph that just said "the
achievements will be described" - this is useless, as it says nothing. From the
abstract a reader should be able to ascertain if the project is of interest to
them and presents results of which they would like to know more details.
-->

\hspace{0pt}
\vfill
\begin{center}
\subsubsection*{Abstract} 
\addcontentsline{toc}{chapter}{Abstract}

The primary aim of this project is to build a user-friendly tool to support
escape room maintainers and their relationships with their audience. The
literature survey exposed concerns regarding use of technology within an escape
room setting, and a gap in the market for an external technological tool. The
end product was built as a web application functioning as a social network
between escape room maintainers and enthusiasts. This meets requirements
established by surveying and discussing with maintainers. This dissertation
paper documents, and justifies decisions made along, the process of development
of this product.

\begingroup
\let\clearpage\relax \subsubsection*{COVID-19 Impact Statement}
\addcontentsline{toc}{chapter}{COVID-19 Impact Statement}

The COVID-19 outbreak meant that escape rooms were completely closed to
business. This made face-to-face contact with involved escape room maintainers
impossible. Maintainers were not in a position to discuss student projects due
to the situation, which is universally jeopardising business. I had already
engaged with maintainers in person and online. It became impossible to follow
this up meaningfully. It was impractical to change the project's focus at the
point of the pandemic, so a decision was made to continue supporting the project
for after the lockdown order had been lifted.

\endgroup

\subsubsection*{Acknowledgements}
\addcontentsline{toc}{chapter}{Acknowledgements}

Thanks to Andrew Stratton for supervising and providing a guiding hand during
the project. Thanks also to the Lockup Escape Room in Sheffield for providing
helpful insights and allowing me to trial an escape room with a group. Thank you
to those working in Development at UKCloud for helping me refine the skills
needed to build Blacklight---special mentions to Ben, Chris, and Oliver.
Finally, my deepest thanks to my family, my friends at University of Sheffield
Tea Society, and my mentor Dalbinder. All have strongly supported me this year.

\end{center}
\vfill
\hspace{0pt}

<!-- Contents -->
\tableofcontents
\mainmatter