---
title: R Markdown
description: Yüksek kaliteli raporlar, sunular ve panolar oluşturmak için Visual Studio 'da R Markdown belgeleri oluşturma.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 32cfabfe61a8c1dc8f04cd2d024b07a92b1eb7e2
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888565"
---
# <a name="create-r-markdown-documents"></a>R Markdown belgeleri oluşturma

[R Markdown](https://rmarkdown.rstudio.com/) , R 'deki Analizi yüksek kaliteli belgeler, raporlar, sunular ve panolar halinde etkinleştiren bir belge biçimidir.

Visual Studio için R Araçları (RTVS), R Markdown bir öğe şablonu, düzenleyici desteği (düzenleyici içindeki R kodu için IntelliSense dahil), dosya oluşturma özellikleri ve Canlı önizleme sağlar.

## <a name="using-r-markdown"></a>R Markdown kullanma

1. Visual Studio’yu kapatın.
1. (Yalnızca bir kez) [Pandoc.org](https://pandoc.org/installing.html)adresinden `pandoc`.
1. Visual Studio 'yu yeniden başlatarak pandoc yüklemesini seçin.
1. [Etkileşimli pencereden](interactive-repl-for-r-in-visual-studio.md)yapabileceğiniz `knitr` ve `rmarkdown` paketlerini yükleyebilirsiniz:

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. **Dosya > ** **Yeni** > **Dosya** menü komutunu kullanarak yeni bir R Markdown dosyası oluşturun ve listeden **R** > **R Markdown** ' i seçin. Bir proje bağlamında Çözüm Gezgini projeye sağ tıklayın ve **R Markdown Ekle** ' yi seçin (veya > **Yeni öğe** **ekleyin** ve listeden **R Markdown** seçeneğini belirleyin).

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

Visual Studio 2017 sürüm 15,5 ve üzeri otomatik olarak R Markdown için Canlı önizleme sağlar. Düzenleyici ve önizleme arasındaki otomatik eşitlemeyi etkinleştirmek için **R araçları** > **Markaşağı** > **Otomatik eşitleme** (**CTRL**+**SHIFT**+**Y**) seçeneğini belirleyin. Otomatik eşitleme kullanmıyorsanız, **R araçları** ' nı kullanarak önizlemeyi yenileyebilirsiniz > **Markaşağı** > **yeniden yükleme R Markdown önizleme**' yi kullanabilirsiniz.

Ayrıca, düzenleyicide sağ tıklayıp **Önizleme** komutlarından birini seçerek dosyayı HTML, PDF ve Microsoft Word biçimlerinde da önizleyebilirsiniz. Ayrıca, **R araçları** > **markaşağı** menüsünde aynı komutlar da mevcuttur. (Visual Studio 'nun önceki sürümlerinde bu komutlar **R araçları** > **Yayımla** menüsünde bulunur.)

![Rmarkaşağı canlı önizleme ve diğer önizleme menü komutları](media/rmarkdown-live-preview.png)
