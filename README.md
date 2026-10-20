# nstc-proposal: LaTeX classes for NSTC proposals and reports (國科會專題研究計畫 LaTeX 文件格式)

(See [below](#概要) for 中文解說)

## Overview

This package consists of LaTeX classes for preparing grant proposals to National Science and Technology Council, Taiwan, that is:

* CM03
* CM302

which support typesetting in both Chinese and English and are compatible with pdfLaTeX and XeTeX.

The package also provides `nstc-report` for progress and final research reports.
It supports **pdfLaTeX and XeLaTeX**, sharing font configuration with CM03/CM302.
It follows the layout in the supplied NSTC report-format document dated
114/10/02 (2025-10-02), with the same font substitutions as the proposal classes.

## Installation

### CTAN installation

Run the following command in a terminal (or use any TeX package manager) to install:

```bash
tlmgr install nstc-proposal
```

### Manual Installation

1. Run the following command in a terminal to build files and examples:

   ```bash
   latex nstc-proposal.ins
   ```

2. Copy the generated `.cls` files to a directory searchable by LaTeX.
   Hint. Run the following command to locate the local texmf directory:

   ```bash
   kpsewhich -var-value TEXMFLOCAL
   ```

   Placing the generated files under any subdirectory of the directory shown above should work.

3. Compile any of the examples with pdfLaTeX or XeLaTeX (see below).

## Usage

See `nstc-proposal.pdf`.

## Development

`nstc-proposal` was written and is maintained by [Liang-Ting Chen](https://l-tchen.github.io).

Please report any bug or feature request on GitHub (<https://github.com/L-TChen/nstc-proposal>).

Edit `nstc-proposal.dtx` and regenerate with `latex nstc-proposal.ins` when
changing a class or example.

All three classes share incompatible-option handling: rejected options produce
a warning naming the selected class and are removed before `article` or later
packages can apply them. This includes `landscape`, `10pt`, `11pt`, `letterpaper`,
`a5paper`, `b5paper`, `executivepaper`, `legalpaper`, `twocolumn`, `titlepage`,
`notitlepage`, and `openright`. Compatible options continue to pass to `article`.

## License

This package is distributed under the LaTeX Project Public License (LPPL),
version 1.3c or later. See [LICENSE](LICENSE).

## 概要

本套件提供台灣國家科學及技術委員會專題研究計畫申請書的 LaTeX 文件格式：

* 表 CM03
* 表 CM302

兩者皆支援中英混排，以及 pdfLaTeX 與 XeLaTeX。此格式依據民國 112 年 11 月 7 日版
[專題研究計畫申請書表 CM03 研究計畫內容頁數限制一覽表](https://www.nstc.gov.tw/nstc/attachments/ee49fe4d-e7a6-44e9-89cf-cd8ca054d6b5)。

本套件另提供進度與成果報告格式

* `nstc-report`

支援 **pdfLaTeX 與 XeLaTeX**，並與 CM03/CM302 共用字型設定。
此格式依據民國 114 年 10 月 2 日（2025-10-02）版 [國科會報告撰寫格式](https://www.nstc.gov.tw/nstc/attachments/ee49fe4d-e7a6-44e9-89cf-cd8ca054d6b5)。

## 安裝方式

### CTAN 安裝

在終端機執行以下指令安裝（或使用 TeX 套件管理程式）：

```bash
tlmgr install nstc-proposal
```

### 手動安裝

1. 在終端機執行以下指令產生檔案與範例：

   ```bash
   latex nstc-proposal.ins
   ```

2. 將產生的 `.cls` 檔案複製到 LaTeX 可搜尋的目錄。可用以下指令查詢本機 texmf 目錄：

   ```bash
   kpsewhich -var-value TEXMFLOCAL
   ```

   將檔案放在該目錄下的子目錄即可。

3. 使用 pdfLaTeX 或 XeLaTeX 編譯範例（見下方說明）。

## 使用方式

請參考 `nstc-proposal.pdf`。

### 文件選項

文件格式繼承自 `article` 額外提供以下選項：

* `libertine`: 英文字型改用 Linux Libertine（來自 [libertine](https://ctan.org/pkg/libertine) 套件）。
* `kaiti` （需用 XeTeX 編譯）: 中文字型改用 macOS 內建的常州華文「楷體-繁」。

### 文件定義之指令

以下指令可產生 CM03 的章節名稱與說明：

* `\ProposalBackground`: 研究計畫之背景
* `\ProposalMethod`: 研究方法、進行步驟及執行進度
* `\ProposalPlan`: 預期完成之工作項目及成果
* `\ProposalIntegration`: 整合型研究計畫說明

若是編輯軟體會根據 `\section` 判斷原始碼格式，支援程式碼摺疊或目錄之類的功能，則建議直接使用 `\section` 指令輸入章節名稱，最後加入 `\vskip1em` 保留足夠的留白。例如：

```latex
\section{研究計畫之背景}
請詳述本研究計畫所要探討或解決的問題、研究原創性、重要性、預期影響性及國內外有關本計畫之研究情況、重要參考文獻之評述等。如為連續性計畫應說明上年度研究進度。
\vskip1em
```

進度與成果報告格式則提供

* `\frontmatter`: 產生以大寫羅馬數字編頁的目錄，再將正文頁碼重設為阿拉伯數字第 1 頁。

### 表 CM03 範例

```latex
\documentclass{nstc-cm03}
\usepackage{microtype}

\begin{document}

\ProposalBackground
\ProposalMethod
\ProposalPlan
\ProposalIntegration

\nocite{*}

\bibliographystyle{plain}
\bibliography{sample}
\end{document}
```

以 LaTeX 或 XeTeX 編譯或加上選項 `libertine` 的四種結果如下

|           | LaTeX | XeTeX |
|-----------|-------|-------|
| （預設無選項）  |[proposal.pdf](https://github.com/user-attachments/files/17560415/proposal.pdf)  |  [proposal-xetex.pdf](https://github.com/user-attachments/files/17560554/proposal-xetex.pdf)      |
| `libertine` | [proposal-libertine.pdf](https://github.com/user-attachments/files/17560517/proposal-libertine.pdf) |[proposal-libertine-xetex.pdf](https://github.com/user-attachments/files/17560558/proposal-xetex-libertine.pdf)|

### 表 CM302 範例

若用格式 `nstc-cm302` 則會改為表 CM302 文獻目錄之格式：

1. 文件標題改為「五、著作目錄⋯⋯」
2. 隱藏 LaTeX 預設之引用章節名稱
3. 取消 CM03 相關指令 `\ProposalBackground`、`\ProposalMethod`、 `\ProposalPlan`、`\ProposalIntegration` 避免誤用。

引用載入之 `.bib` 檔裡所有的論文，只需要用 `\nocite{*}` 即可。例如以下檔案：

```latex
\documentclass{nstc-cm302}

\usepackage[hidelinks]{hyperref}
\usepackage{doi}

\usepackage{microtype}

\begin{document}

\nocite{*}

\bibliographystyle{abbrv}
\bibliography{sample}
\end{document}
```

便能產出此[結果](https://github.com/user-attachments/files/17573002/bibliography.pdf)。

### 進度與成果報告範例

使用 `nstc-report` 撰寫報告，可用 pdfLaTeX 或 XeLaTeX 編譯：

```latex
\documentclass{nstc-report}
\title{研究計畫成果報告}

\begin{document}
\frontmatter % 不需要目錄時可省略
\maketitle

\section{前言}
說明研究背景。

\section{研究方法}
說明研究方法與執行過程。

\section{結果與討論}
說明研究成果與結論。
\end{document}
```

頁碼預設使用阿拉伯數字；`\frontmatter` 會自動產生目錄並切換頁碼，請至少編譯兩次以更新目錄。
`\maketitle` 僅顯示 `\title` 設定的標題，不顯示作者或日期。
摘要與關鍵詞請於國科會成果報告系統填寫。完整結構範例見 `example/report.tex`。

## 設計

### 文件格式設定

國科會規定頁面尺寸 A4，一倍行距[^1]，字型大小 12 點，以及頁面邊界 2 公分，其他如字型並無特別規定。

### 預載套件

文件格式除設定格式必要的套件外，另載入 `amsmath` 以及 `amsthm` 兩套件以及：

* 字型相關套件
  * 用 LaTeX 編譯時額外載入 `CJKutf8`
  * 用 XeTeX 編譯時額外載入 `fontspec`. `unicode-math`, `xeCJK`

### 中文字型

* 若用 TeX 編譯，字型則為「文鼎 PL 中楷」[^2]（來自 [`arphic`](https://ctan.org/pkg/arphic) 套件）

* 若用 XeTeX 編譯，字型選用順序如下：

  1. 標楷體（Windows 以及 macOS 13.2 以前內建）
  2. 標楷體-繁（macOS 13.3 以後內建）
  3. 文鼎 PL 中楷（來自 [`arphic-ttf`](https://ctan.org/pkg/arphic-ttf?lang=en) 套件）

### 英文字型

Times 家族（如 Times New Roman）的 TeXGyre Termes（來自 [`newtx`](https://ctan.org/pkg/newtx) 套件）

## 開發維護

本套件 `nstc-proposal` 是由[陳亮廷](<https://l-tchen.github.io>)所撰寫維護。

發現任何錯誤或是有任何需求，請回報到 GitHub 上的專案網站 <https://github.com/L-TChen/nstc-proposal。>

## 版權聲明

本套件依 LaTeX Project Public License（LPPL）第 1.3c 版或任何後續版本的條款散布，
詳見 [LICENSE](LICENSE)。

[^1]: 根據 Wikipedia 的[說明](https://en.wikipedia.org/wiki/Leading#cite_ref-4)，Word 97–2010 的一倍行距實則為 1.15 倍的行距（leading）之後為 1.08 倍，所以不清楚到底行距實質規定多少。此文件格式行距以 `setspace` 套件的 `\onehalfspacing` 設定行距，印出後肉眼比對約略相等國科會網站下載的範例檔。
[^2]: 文鼎字型公眾授權字型法律聲明[在此](https://www.arphic.com.tw/2022/01/21/plfont/)。
