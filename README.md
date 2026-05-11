# XJTU Bachelor thesis LaTeX template.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

This is an opensource LaTeX thesis template for XJTU B.S. candidates. It can be used directly on Overleaf. The overleaf template is [here](https://www.overleaf.com/latex/templates/xian-jiaotong-university-bachelor-thesis-latex-template/rdpykcmzdrjp).

For supplements and corrections, please issue.

## Environments

* Compler: XeLaTeX
* TeX Live Version: 2019

```sh
# compiling
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

## Attention

This project has not been tested on other platforms. 

## Ack

This project is modified from the Overleaf project [Doctorate Thesis LaTeX Template](https://www.overleaf.com/latex/templates/latex-template-for-doctoral-thesis-of-xjtu/bmrqcdhbdrcw) by XJTU alumni Zhang Ming, thanks for his work.

## Usecases

The `body/` directory contains both template examples and thesis body chapters. Use `body/usecases.tex` as the formatting reference, and use `body/chapter_3.tex` and `body/chapter_5.tex` as practical examples for mixing text, equations, figures, tables, algorithms, and code listings.

### Chapters And Sections

Use bilingual section commands:

```tex
\BiChapter{中文章标题}{English Title}
\BiSection{中文节标题}{English Title}
\BiSubsection{中文小节标题}{English Title}
```

The English title can be left empty:

```tex
\BiSection{设计目标}{}
```

### Citations And References

Use normal citations or superscript citations:

```tex
普通引用：\cite{IAM_in_Cloud}
上标引用：\upcite{Manolakis2005}
```

Use `\label{}` with `\ref{}` for cross references:

```tex
\label{policy_format}
公式\ref{policy_format}
图\ref{regex_breakdown}
表\ref{tab_check}
算法\ref{access_summary}
```

Avoid duplicate labels. For example, prefer names such as `tab_code_stat`, `tab_perf_result`, `fig_system_overview`, and `alg_access_summary`.

### Lists

Unordered list:

```tex
\begin{itemize}
    \item 第一项
    \item 第二项
\end{itemize}
```

Numbered list:

```tex
\begin{enumerate}
    \item 第一项
    \item 第二项
\end{enumerate}
```

Formatted numbered list used frequently in the body:

```tex
\begin{enumerate}[wide, label=\arabic*),  labelindent=21pt]
    \item 第一项
    \item 第二项
\end{enumerate}
```

### Figures

The common figure format is:

```tex
\begin{figure}[H]
\centering
\includegraphics[width=\textwidth]{overview.pdf}
\caption{系统组件交互示意图} \label{overview}
\end{figure}
```

`[H]` fixes the figure near the current position. The template example also uses `[!ht]`.

### Tables

Use three-line tables with `tabularx`:

```tex
\begin{table}[H]
    \renewcommand{\arraystretch}{1.2}
    \centering\wuhao
    \caption{代码统计表} \label{tab_code_stat} \vspace{2mm}
    \begin{tabularx}{\textwidth} {
        >{\centering\arraybackslash}X
        >{\centering\arraybackslash}X
    }
    \toprule[1.5pt]
        列1 & 列2 \\
    \midrule[1pt]
        A & B \\
    \bottomrule[1.5pt]
    \end{tabularx}
\end{table}
```

### Equations

Single numbered equation:

```tex
\begin{equation}\label{general_encoding}
\left( \bigvee_{S \in \text{Allow}} [S] \right)
\land
\neg \left( \bigvee_{S \in \text{Deny}} [S] \right)
\end{equation}
```

Multiline equation:

```tex
\begin{equation}\label{statement_encoding}
\begin{aligned}
[S] := &\left( \bigvee_{v \in P(S)} p=v \right) \land \\
       &\left( \bigvee_{v \in A(S)} a=v \right)
\end{aligned}
\end{equation}
```

Unnumbered equation:

```tex
\begin{equation*}
\text{str} = \text{a*b*} \to \text{r} = \text{a.*b.*}
\end{equation*}
```

Subequations:

```tex
\begin{subequations} \label{equ_ch2_fourier}
\begin{align}
X(f) &= ... \\
x(t) &= ...
\end{align}
\end{subequations}
```

### Code Listings

Use `lstlisting` for source code:

```tex
\begin{lstlisting}[language=Java, caption={策略类定义}, label={java_policy}]
public class Policy {
    String version;
    List<Statement> statements;
}
\end{lstlisting}
```

It can also be used for shell commands:

```tex
\begin{lstlisting}[language=Bash, caption={AWS CLI 命令示例}, label={aws_cli}]
aws s3api put-bucket-policy --bucket <bucket> --policy file://<file_name>
\end{lstlisting}
```

### Algorithms

Algorithms use the `algorithm` environment:

```tex
\begin{algorithm}[H]
    \caption{AccessSummary \label{access_summary}}
    \IncMargin{2em}
    \DontPrintSemicolon
    \KwIn{Policy $p$}
    \KwOut{Set of findings $\Sigma$}

    $\text{results} \gets \emptyset$
    \While{$\text{work\_list} \not= \emptyset$}{
        \Return results
    }
\end{algorithm}
```

Common keywords:

```tex
\KwIn{}
\KwOut{}
\For{}{}
\While{}{}
\If{}{}
\Else{}
\Return
\tcp*{行内注释}
```

### Text Markup

Term definition:

```tex
\textbf{键}。一个键代表……
```

Inline code or commands:

```tex
\texttt{\textbackslash upcite}
```

Footnote and URL:

```tex
\footnote{这是一个注脚}
\url{https://example.com}
```

### Minimal Chapter Skeleton

```tex
% !Mode:: "TeX:UTF-8" 

\BiChapter{你的章节名}{}

\BiSection{你的一级节}{}

正文内容，引用文献\cite{your_bib_key}。如图\ref{fig_example}所示。

\begin{figure}[H]
\centering
\includegraphics[width=\textwidth]{your_figure.pdf}
\caption{你的图题} \label{fig_example}
\end{figure}

\BiSubsection{你的二级节}{}

\begin{enumerate}[wide, label=\arabic*),  labelindent=21pt]
    \item 第一项。
    \item 第二项。
\end{enumerate}
```
