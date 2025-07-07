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


以下我們舉一個簡單的例子來說明。

```
\documentclass[11pt,reqno,a4paper]{amsart}

\usepackage[margin=1.13in]{geometry}

\usepackage{amsmath,amsfonts,amssymb,amsthm,mathrsfs}

%\usepackage{bbm}
%\usepackage{dsfont}
%\usepackage{mathptmx}   % selects Times Roman as basic font
%\usepackage{helvet}     % selects Helvetica as sans-serif font

\newtheorem{theorem}{Theorem}[section]

\linespread{1.08}

\title{A Latex example}
\author{Tsung-Ju Lee}
\date{\today}

\begin{document}
\maketitle

\section{Introduction}

Test with an equation \(x^{2}+y^{2}=1\). Here is an displayed equation
\begin{equation}
\frac{\mathrm{d}}{\mathrm{d}x}\int_{c}^{x} f(t)\mathrm{d}t = f(x)
\end{equation}
where \(f(x)\) is a continuous function on \(\mathbf{R}\).

\begin{theorem}[Fundamental theorem of algebra]
Every non-constant polynomial over \(\mathbf{C}\) has a root in \(\mathbf{C}\).
\end{theorem}
\end{document}
```
# 結構

一般來說，一份 .tex 文件包含兩個部分：preamble 與 document（本文內容）。preamble 裡面的程式碼主要控制排版的設定，document 裡面則包含文件的內容。文件內容指夾在 `\begin{document}` 和 `\end{document}` 之間的內容，即
```
\begin{document}
\maketitle

\section{Introduction}

Test with an equation \(x^{2}+y^{2}=1\). Here is an displayed equation
\begin{equation}
\frac{\mathrm{d}}{\mathrm{d}x}\int_{c}^{x} f(t)\mathrm{d}t = f(x)
\end{equation}
where \(f(x)\) is a continuous function on \(\mathbf{R}\).

\begin{theorem}[Fundamental theorem of algebra]
Every non-constant polynomial over \(\mathbf{C}\) has a root in \(\mathbf{C}\).
\end{theorem}
\end{document}
```
在 `\begin{document}` 前面的區域叫 preamble，即 
```
\documentclass[11pt,reqno,a4paper]{amsart}

\usepackage[margin=1.13in]{geometry}

\usepackage{amsmath,amsfonts,amssymb,amsthm,mathrsfs}

%\usepackage{bbm}
%\usepackage{dsfont}
%\usepackage{mathptmx}   % selects Times Roman as basic font
%\usepackage{helvet}     % selects Helvetica as sans-serif font

\newtheorem{theorem}{Theorem}[section]

\linespread{1.08}

\title{A Latex example}
\author{Tsung-Ju Lee}
\date{\today}
```

以下我們逐行解釋例子中展示的程式碼。

## Preamble 


### 第一行

```
\documentclass[11pt,reqno,a4paper]{amsart}
```
為 .tex 檔案的開頭。`\documentclass` 的功用在於指定文件類型，需在後面的大括號 \{ \} 內輸入文件類型。常見的文件類型有 book、report 或 article，分別代表書籍，報告，或文章。不同的文件類型可以使用不同的指令排版，例如 book 類型可以使用 \chapter 指令來排版章節。例子裡面使用的是文件類型是 amsart（American Mathematical Society article，美國數學協會文章）。大括號前面中括號 \[ \] 內的指令是用來調整參數，不同的參數通常用逗號分開。上述例子中的參數有三個：11pt、reqno、a4paper。11pt 是指定文件的字體大小，reqno 是讓文件內容裡的數學展式標籤靠右，a4paper 則是指定文件的紙張大小為 A4。

### 第二行

```
\usepackage[margin=1.13in]{geometry}
```
是告訴 Latex 編譯時要引用 geometry 這個套件。`\usepackage` 是引入套件的指示，大括號 \{ \} 中的 geometry 是套件的名字。與 `\documentclass[11pt,reqno,a4paper]{amsart}` 的邏輯類似，大括號前的中括號 \[ \] 內的指令為調整參數，這裡我們的參數是 margin=1.13in，margin 指的是文章內容到紙張邊緣的距離，這邊的設定是 1.13 公寸（inch）。geometry 套件裡還有很多參數可以使用。對於一般的套件，使用者通常可以在 [CTAN](https://ctan.org) 的網站上找到說明。例如 [Link](https://ctan.org/pkg/geometry) 可以找到 geometry 套件的完整使用方式與說明。

### 第三行

```
\usepackage{amsmath,amsfonts,amssymb,amsthm,mathrsfs}
```
一次引入五個套件，不同的套件用逗號分開。這些套件包含一些在編寫數學文件時常用的指令。例如常見的數學符號、提供使用者定義 Theorem 環境與 Reference 格式等等。

### 第四行至第七行

```
%\usepackage{bbm}
%\usepackage{dsfont}
%\usepackage{mathptmx}   % selects Times Roman as basic font
%\usepackage{helvet}     % selects Helvetica as sans-serif font
```
是關於字型的套件，要引入字型時使用。但注意到這些指令前面都有一個 % 符號。% 在 .tex 文件中表示註解，即 % 後面的程式碼會直接被忽略不作用。因此這四行在這份文件中是不起任何作用的。

### 第八行

```
\newtheorem{theorem}{Theorem}[section]
```
是在呼叫 amsthm 套件之後才可以使用的指令。這個指令的一般形式是 `\newtheorem{name}{head}[counter]`，用途為定義 Theorem 環境供本文使用。其中 name 表示環境的名字、head 表示在文件中要顯示的標題名稱，而中括號內的 counter 則是計數器（或是標號），我們的程式碼 `\newtheorem{theorem}{Theorem}[section]` 定義了一個名為 "theorem" 的環境，其標題為 "Theorem"，並且用 section （章節）來做標記。

### 第九行

```
\linespread{1.08}
```
功用為指定文件的行距，這邊使用的是 1.08 倍。

### 第十行到第十二行

```
\title{A Latex example}
\author{Tsung-Ju Lee}
\date{\today}
```
是在使用適當文件格式後才可使用的指令。`\title{A Latex example}` 是告訴 Latex 文章標題為 "A Latex example"、`\author{Tsung-Ju Lee}` 表示此份文件作者為 "Tsung-Ju Lee"，最後 `\date{\today}` 表示文件的製作日期是今天。當然這些指令也可以加入參數，例如 `\title[Latex]{A Latex example}` 等。使用者可以自己上網搜尋這些參數的使用時機。

## 文件內容

現在我們來解釋文件內容裡的程式碼代表的意義。


