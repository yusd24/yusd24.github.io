---
title: How to typeset with Latex? A walking example
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

一般而言，Latex 的指令一般都是用斜線 \\ 開頭。斜線後面接指令。

以下我們逐行解釋例子中展示的程式碼。

## Preamble 

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

文件內容為夾在 `\begin{document}` 與 `\end{document}` 之間的部分。現在我們來解釋文件內容裡的程式碼代表的意義。

```
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
```

### 第一行
```
\maketitle
```
代表要生成文件標題。這個指令會在文件的第一頁產生標題與作者。

### 第二行
```
\section{Introduction}
```
指的是以下內容（直至下次 \section 出現前）均為第一節的內容，這節的名稱叫做 Introduction。

### 第三行至第七行
```
Test with an equation \(x^{2}+y^{2}=1\). Here is an displayed equation
\begin{equation}
\frac{\mathrm{d}}{\mathrm{d}x}\int_{c}^{x} f(t)\mathrm{d}t = f(x)
\end{equation}
```
為文件內容的一部分。數學模式的起點與終點用 `\(` 與 `\)` 表示。所以 `\(x^{2}+y^{2}=1\)` 表示用數學模式編譯 `x^{2}+y^{2}=1`，其中 "^" 表示上標。因此這段程式碼編譯出來得到 $x^{2}+y^{2}=1$。沒有被 `\(` 與 `\)` 包住的地方為一般的文字模式。所以第一句話編譯出來會得到

Test with an equation $x^{2}+y^{2}=1$.

之後有一段程式碼被 `\begin{equation}` 與 `\end{equation}` 夾住。`\begin{environment}` 與 `\end{environment}` 意思是中間夾住的程式碼要使用 environment 環境編譯。這裡我們使用的環境為 equation，意思是中間夾住的數學式要用數學展式表現；即要從上面的段落獨立出來打在下一行上。注意到上面的數學式 $x^{2}+y^{2}=1$ 是鑲嵌在段落裡面，這通常叫做「隨文模式」。展示中有一些常用的數學符號：`\frac{A}{B}` 表示分數 $B$ 分之 $A$。`\mathrm{d}` 表示 d 這個字母要使用 roman 字體，有別於一般的數學斜體字母，如後面的 $x$。`\int_{c}^{x}` 表示積分符號，上限為 $x$，下限為 $c$。所以整段表示出來會變成

Test with an equation $x^{2}+y^{2}=1$. Here is an displayed equation

$$\begin{equation}\frac{\mathrm{d}}{\mathrm{d}x}\int_{c}^{x} f(t)\mathrm{d}t = f(x) \end{equation}$$

where \\(f(x)\\) is a continuous function on \\(\mathbf{R}\\).


注意到在數學式的最右邊有一個編號 (1)，這是它的編號；使用 equation 環境會自動把數學式按照順序編號。而最後的 `\mathbf{R}` 表示字母 R 要使用數學粗體字。

### 第八行到第十行

```
\begin{theorem}[Fundamental theorem of algebra]
Every non-constant polynomial over \(\mathbf{C}\) has a root in \(\mathbf{C}\\).
\end{theorem}
```
這段意思是告訴 Latex 要使用我們剛剛在 preamble 定義的 theorem 環境編譯。編譯出來的內容為

**Theorem 1.1**. (Fundamental theorem of algebra) _Every non-constant polynomial over \\(\mathbf{C}\\) has a root in \\(\mathbf{C}\\)_.

其中 **1.1** 表示第一節的第一個定理（即以 section 來計數定理）。使用者可以在後面多寫幾個 `\begin{theorem} ... \end{theorem}` 或是在文章內容前後加入幾個 `\section{}` 來測試定理編號的變化。以上文件內容結束。

