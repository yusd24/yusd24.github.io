---
title: How to typeset with Latex? A working example
output:
  md_document:
    variant: gfm+footnotes
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../_posts") })
date: 2025-07-07
permalink: /posts/2025-latex-typeset
excerpt_separator: <!--more-->
always_allow_html: true
toc: true
header:
 og_image: ""
tags:
  - Latex
---

這篇文章解釋如何使用 Latex 排版。

<!--more-->

## 簡介

一般來說，一份 .tex 文件包含兩個部分：preamble 與 document（本文內容）。preamble 裡面的程式碼主要控制排版的設定，document 裡面則包含文件的內容。以下我們舉一個簡單的例子來說明。

```
\documentclass[11pt,reqno,a4paper]{amsart}

\usepackage[margin=1.13in]{geometry}

\usepackage{amsmath,amsfonts,amssymb,amsthm,mathrsfs}

%\usepackage{bbm}
%\usepackage{dsfont}
%\usepackage{mathptmx}   % selects Times Roman as basic font
%\usepackage{helvet}     % selects Helvetica as sans-serif font

\linespread{1.08}

\begin{document}
\maketitle
Test with an equation \(x^{2}+y^{2}=1\).
\end{document}
```
