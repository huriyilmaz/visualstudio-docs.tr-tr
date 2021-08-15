---
title: R Markdown
description: yüksek kaliteli raporlar, sunular ve panolar oluşturmak için Visual Studio R Markdown belgeler oluşturma.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: bb85e77705e06e3864064aa9054f02c01993211f444d551c2eaccebbfb10219e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229110"
---
# <a name="create-r-markdown-documents"></a>R Markdown belgeleri oluşturma

[R Markdown](https://rmarkdown.rstudio.com/) , R 'deki analizi yüksek kaliteli belgeler, raporlar, sunular ve panolar halinde etkinleştiren bir belge biçimidir.

Visual Studio için R Araçları (rtvs), R Markdown bir öğe şablonu, düzenleyici desteği (düzenleyici içindeki R kodu için ıntellisense dahil), dosya oluşturma özellikleri ve canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown kullanma

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) `pandoc` [Pandoc.org](https://pandoc.org/installing.html)adresinden yükler.
1. pandoc yüklemesinin çekilmesi gereken Visual Studio yeniden başlatın.
1. `knitr` `rmarkdown` [Etkileşimli pencereden](interactive-repl-for-r-in-visual-studio.md)yapabileceğiniz ve paketlerini yükleyebilirsiniz:

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. **dosya** yeni dosya menü komutunu kullanarak yeni bir R Markdown dosyası oluşturun  >    >   ve listeden **R**  >  **R Markdown** öğesini seçin. bir proje bağlamında Çözüm Gezgini projeye sağ tıklayın ve **R Markdown ekle** ' yi seçin (veya   >  **yeni öğe** ekleyin ve listeden **R Markdown** seçeneğini belirleyin).

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

Visual Studio 2017 sürüm 15,5 ve üzeri R Markdown için canlı önizlemeyi otomatik olarak sağlar. Düzenleyici ve önizleme arasındaki otomatik eşitlemeyi etkinleştirmek için **R araçları**  >  **markaşağı**  >  **Otomatik eşitleme** (**CTRL** + **Shift** + **Y**) seçeneğini belirleyin. otomatik eşitleme kullanmıyorsanız, **R araçları**  >  **markaşağı**  >  **yeniden yükleme R Markdown önizleme**'yi kullanarak önizlemeyi yenileyebilirsiniz.

ayrıca, düzenleyicide sağ tıklayıp **önizleme** komutlarından birini seçerek dosyayı HTML, PDF ve Microsoft Word biçimlerinde da önizleyebilirsiniz. Aynı komutlar **R araçları**  >  **markaşağı** menüsünde de bulunur. (Visual Studio önceki sürümlerinde bu komutlar **R araçları**  >  'nda bulunur **Yayımla** menüsü.)

![Rmarkaşağı canlı önizleme ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
