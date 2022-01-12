---
title: R Markdown
description: Yüksek kaliteli R Markdown, Visual Studio ve panolar oluşturmak için R Markdown belge oluşturma.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 2bfdb562eecb110ad7b859ad4d9565e00949ae40
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750772"
---
# <a name="create-r-markdown-documents"></a>Belge R Markdown oluşturma

[R Markdown,](https://rmarkdown.rstudio.com/) R'de analizi yüksek kaliteli belgelere, raporlara, sunulara ve panolara dönüştüren bir belge biçimidir.

Visual Studio için R Araçları (RTVS), R Markdown şablon, düzenleyici desteği (düzenleyicide R kodu için IntelliSense dahil), dosya oluşturma özellikleri ve canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) `pandoc`yüklemesi [](https://pandoc.org/installing.html)pandoc.org.
1. Pandoc Visual Studio almayacak şekilde yeniden başlatın.
1. etkileşimli `knitr` `rmarkdown` penceresinden ve paketlerini yükleyin: [](interactive-repl-for-r-in-visual-studio.md)

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Dosya Yeni R Markdown menü komutunu kullanarak **ve listeden**  >    >   **R** dosyası'R Markdown  >  **yeni bir** dosya oluşturun. Proje bağlamında, Çözüm Gezgini'de projeye sağ tıklayın ve R Markdown **Ekle'yi** (veya Yeni Öğe Ekle'yi ve listeden R Markdown'yi  >   seçin). 

1. Yeni dosyanın varsayılan içeriği aşağıdaki gibidir:

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>Önizlemeler

Visual Studio 2017 sürüm 15.5 ve sonraki sürümler, sürümler için otomatik olarak canlı R Markdown. Düzenleyici ile önizleme arasında otomatik eşitlemeyi açmak için **R Araçları** Markdown Otomatik Eşitleme (  >    >   **Ctrl** Shift Y ) + **seçeneğini** + **kullanın.** Otomatik eşitlemeyi kullanasanız önizlemeyi **R** Araçları Markdown Yeniden Yükleme ve Önizleme R Markdown  >    >  **yenileyin.**

Düzenleyiciye sağ tıklar ve Önizleme komutlarından birini Microsoft Word html, PDF ve Microsoft Word biçimlerde de dosyanın **önizlemesini görebilirsiniz.** Aynı komutlar **R** Araçları  >  **Markdown menüsünde de** kullanılabilir. (Önceki sürümlerde Visual Studio bu komutlar R Araçları **Yayımla**  >  **menüsünde** bulunur.)

![RMarkdown canlı önizlemesi ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
