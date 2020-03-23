---
title: R Markdown
description: Yüksek kaliteli raporlar, sunumlar ve panolar oluşturmak için Visual Studio'da R Markdown belgeleri nasıl oluşturulur?
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 32cfabfe61a8c1dc8f04cd2d024b07a92b1eb7e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888565"
---
# <a name="create-r-markdown-documents"></a>R İşaretleme belgeleri oluşturma

[R İşaretlemesi,](https://rmarkdown.rstudio.com/) R'deki çözümlemi yüksek kaliteli belgelere, raporlara, sunulara ve panolara dönüştüren bir belge biçimidir.

R Tools for Visual Studio (RTVS) r markdown öğe şablonu, düzenleyici desteği (editör içinde R kodu için IntelliSense dahil), dosya oluşturma yetenekleri ve canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown kullanma

1. Visual Studio’yu kapatın.
1. (Sadece bir kez) `pandoc` [pandoc.org'dan](https://pandoc.org/installing.html)yükleyin.
1. Pandoc yüklemesini almalısınız Visual Studio, yeniden başlatın.
1. Etkileşimli `knitr` `rmarkdown` [pencereden](interactive-repl-for-r-in-visual-studio.md)yapabileceğiniz paketleri ve paketleri yükleyin:

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1.  > **Yeni** **R** >  **File** > **Dosya Dosyası** menüsü komutunu kullanarak ve listeden R R**Markdown'u** seçerek yeni bir R Markdown dosyası oluşturun. Proje bağlamında, Solution Explorer'da projeyi sağ tıklatın ve **R İşareti Ekle'yi** (veya**Yeni Öğe** **Ekle** > ve listeden **R İşareti'ni** seçin) seçeneğini belirleyin.

1. Yeni dosyanın varsayılan içeriği aşağıdaki gibidir:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Önizlemeler

Visual Studio 2017 sürüm 15.5 ve daha sonra otomatik olarak R Markdown için canlı önizleme sağlar. Düzenleyici ve önizleme arasında otomatik eşitlemeyi açmak için **R Tools** > **Markdown** > **Automatic Sync** **(Ctrl**+**Shift**+**Y)** seçeneğini belirleyin. Otomatik eşitleme kullanmıyorsanız, **R Tools** > **Markdown** > **Reload R Markdown Preview'u**kullanarak önizlemeyi yenileyebilirsiniz.

Ayrıca, düzenleyicide sağ tıklayarak ve **Önizleme** komutlarından birini seçerek dosyayı HTML, PDF ve Microsoft Word biçimlerinde önizleyebilirsiniz. Aynı komutlar **R Tools** > **Markdown** menüsünde de mevcuttur. (Visual Studio'nun önceki sürümlerinde bu komutlar **R Tools** > **Publish** menüsünde bulunur.)

![RMarkdown canlı önizleme ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
