---
title: R Markdown
description: Yüksek kaliteli R Markdown, sunumlar ve Visual Studio oluşturmak için belge oluşturma.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 1fd97d60cd3c201301a7235f0995fda6ae88432b
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114680170"
---
# <a name="create-r-markdown-documents"></a>Belge R Markdown oluşturma

[R Markdown,](https://rmarkdown.rstudio.com/) R'de analizi yüksek kaliteli belgelere, raporlara, sunulara ve panolara dönüştüren bir belge biçimidir.

Visual Studio için R Araçları (RTVS), R Markdown şablon, düzenleyici desteği (düzenleyicide R kodu için IntelliSense dahil), dosya oluşturma özellikleri ve canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) 'den `pandoc` [pandoc.org.](https://pandoc.org/installing.html)
1. Pandoc Visual Studio almayacak şekilde yeniden başlatın.
1. etkileşimli `knitr` `rmarkdown` penceresinden ve paketlerini yükleyin: [](interactive-repl-for-r-in-visual-studio.md)

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. Dosya Yeni Dosya R Markdown komutunu kullanarak **yeni** bir dosya oluşturun ve listeden  >    >   **R**  >  **R Markdown'yi** seçin. Proje bağlamında, Çözüm Gezgini'de projeye sağ tıklayın ve R Markdown **Ekle'yi** (veya Yeni Öğe Ekle'yi R Markdown  >   seçin). 

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

Ayrıca düzenleyicide sağ tıklar ve Önizleme komutlarından birini Microsoft Word html, PDF ve Microsoft Word biçimlerde dosyanın **önizlemesini de görebilirsiniz.** Aynı komutlar **R** Araçları  >  **Markdown menüsünde de** kullanılabilir. (Önceki sürümlerde Visual Studio bu komutlar **R Araçları'nın üzerinde bulunur**  >  **Yayımla** menüsü.)

![RMarkdown canlı önizlemesi ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
