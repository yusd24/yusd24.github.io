---
title: How to use Latex? Installation
output:
  md_document:
    variant: gfm+footnotes
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../_posts") })
date: 2025-07-01
permalink: /posts/2025-latex-installation
excerpt_separator: <!--more-->
always_allow_html: true
toc: true
header:
 og_image: ""
tags:
  - Latex
---

Latex 是常用的排版工具。主要是應用在數學、理工科等符號與等式較多的文章排版。本文將簡單介紹如何在電腦上安裝 Latex。

<!--more-->

# 安裝

在安裝程式之前，我們必須先理解 Latex 的運作邏輯。相較於一般的文書軟體，Latex 更接近程式語言，其設計主要目的是希望使用者可以在編寫文件時專心在文書的內容，讓後端的 Latex 主程式幫使用者處理排版細節。例如「和號」的隨文模式 $\sum_{k=1}^{n} k^{2}$ 與展式

$$\sum_{k=1}^{n} k^{2}$$

其上下標的位置就不同；一個指標在右上與右下角，另一個在正上方與正下方。可以想見如果隨文模式的指標也放在正上方與正下方，文件的文字間距要加大，不容易美觀。如果還有更多其他的符號排版就更麻煩了！這套排版系統可以自動幫使用者解決這類問題。

Latex 可以大致分為兩個部分：主程式與編輯器。使用者先利用編輯器建立一個 .tex 的文檔，在文檔中輸入文章內容與排版指令，之後執行編譯。常見的編譯指令有 Latex、PdfLatex、XeLatex 或 LuaLatex 等等。系統收到編譯指令後，主程式會自動按照使用者的文章內容與排版指令排版，隨後生出一個 DVI 或 PDF 文件，其中 XeLatex 可以處理中文或其他語言的文件。例如上面例子中產生「文章內容」 $\sum_{k=1}^{n} k^{2}$ 的指令為

```
\sum_{k=1}^{n} k^{2}
```

有了這些非常粗淺的概念後，我們下面來介紹常用的主程式與編輯器。

## 主程式

對於剛接觸 Latex 的使用者，我會建議安裝 [Tex Live](https://www.tug.org/texlive/) 作為主程式。Tex Live 在常見的平台上均可以順利運作，例如：MacOS、Windows、Linux；在 MacOS 系統叫做 [MacTex](https://www.tug.org/mactex/)、在 Windows 系統叫做 [Tex Live](https://www.tug.org/texlive/windows.html)。初學者安裝的時候盡量選擇完整安裝，這個選項會安裝 Latex 主程式與其他常用套件（package），這些套件會在主程式執行排版時使用。順帶一提，在 Windows 系統上使用者也可以選擇 [Miktex](https://miktex.org) 作為 Latex 主程式。

## 編輯器

編輯器的選擇就比較多元。MacTex 與 Miktex 都有內建的編輯器，分別叫做 TeXShop 與 TeXworks。除了內建的編輯器外，使用者也可以考慮使用其他的跨平台編輯器，例如 [Texmaker](https://www.xm1math.net/texmaker/) 或 [Texstudio](https://www.texstudio.org) 等等。除了以上這些，也可以使用有整合功能的編輯器，例如 [Sublime Text](https://www.sublimetext.com) 或 [VScode](https://code.visualstudio.com)。這些編輯器可以用來編寫除了 Latex 以外的程式語言，例如 C++、Java、Phython、SQL 等等。如果要使用這類的編輯器，通常需要先安裝相應的套件才能正常使用，詳情請參閱各個程式的網站介紹。

## PDF 瀏覽器

如上介紹，編譯完成後會跑出一個 PDF 檔案。因此使用者需要一個 PDF 瀏覽軟體來檢視檔案。要使用哪個瀏覽軟體需根據你的編輯器來決定。通常使用者在編輯器中輸入或按下編譯的指令後，編輯器會呼叫 Latex 主程式來排版，排版完成後編輯器會呼叫 PDF 瀏覽軟體來開啟剛剛跑出來的 PDF 檔案。因此使用者需注意自己的編輯器支援哪些 PDF 瀏覽軟體。使用 TeXShop 則可直接用 MacOS 內建的瀏覽軟體「預覽程式」。TeXworks 則有內建的 PDF 瀏覽軟體。使用 Sublime Text 可以搭配 [Sumatra](https://www.sumatrapdfreader.org/download-free-pdf-viewer)（Windows）或是 [Skim](https://skim-app.sourceforge.io)（MacOS）。

## 安裝方式

通常會先安裝 Latex 主程式再安裝編輯器。如果有需要最後才安裝 PDF 瀏覽軟體。在安裝編輯器的時候，安裝軟體通常會確認電腦裡的 Latex 主程式是否已安裝，若已安裝，編輯器會自動設定其路徑位置與 PDF 瀏覽器的位置，通常不需另外手動設定。建議初學者使用預設路徑安裝 Latex 主程式，才不會導致編輯器找不到 Latex 主程式的問題。

# 其他

如果只是想先體驗 Latex 不想安裝，可以使用其他線上的 Latex 軟體，例如 [Overleaf](https://www.overleaf.com) 。
