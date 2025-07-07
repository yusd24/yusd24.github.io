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

# 簡介

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

以下我們逐行解釋上面的程式碼。

首先，第一行
```
\documentclass[11pt,reqno,a4paper]{amsart}
```
為 .tex 檔案的開頭。\documentclass 的功用在於指定文件類型，需在後面的大括號 \{\} 內輸入文件類型。常見的文件類型有 book、report 或 article，分別代表書籍，報告，或短文。不同的文件類型可以使用不同的指令排版，例如 book 類型可以使用 \chapter 指令來排版章節。例子裡面使用的是文件類型是 amsart（American Mathematical Society article，美國數學協會短文）。大括號前面中括號 \[\] 內的指令
