---
title: R için Yardım Penceresi
description: R yardımı, ? aracılığıyla doğrudan Visual Studio tümleşiktir Komut.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 26b21e82b0a792301e7a6fea2bce454aab591a65
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750531"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio için R Araçları'da yardım

R yardımı, doğrudan R'de etkileşimli pencereyle Visual Studio. gibi komutunu her `?` `?mtcars` kullanırken, R belgelerinden gelen yardım bir Visual Studio görünür:

![Visual Studio'de yardım penceresi](media/help-window.png)

> [!Tip]
> Yardım penceresi, diğer tüm Visual Studio gibi düzenlenebilir ve yerleştirebilirsiniz. Bkz. ['de pencere düzenlerini Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md)
>
> Yardım sonuçlarını bir tarayıcıda açmak için **R Araçları** Seçenekler menüsünü seçin ve R Yardım Browser  >   **özelliğini** olarak `External` ayarlayın. Bkz. [Seçenekler.](options-for-r-tools-in-visual-studio.md)

Yardım araması yapmak için komutunu `??` ve ardından arama terimini kullanın. Arama terimi boşluk içeriyorsa tırnak kullanın:

```R
??"Motor Trend"
```

![Yardım arama sonuçları](media/help-search1.png)

Yardım penceresinde ayrıca doğrudan R belgelerinde daha fazla arama yapmak için bir arama girişi alanı vardır:

![Giriş alanını kullanarak yardım arama sonuçları](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Tümleşik yardım arama

Geliştiriciler genellikle işlev adları, veri kümeleri ve diğer öğelerle ilgili yardım için R belgelerinde arama kullanır. Visual Studio için R Araçları (RTVS), yardım aramalarını doğrudan düzenleyiciye ve etkileşimli pencerelere tümleştirerek süreci basitleştirmektedir.

- Otomatik tamamlama işlemi sırasında **F1** tuşuna basılarak alt dizeyle eş değere uygun bir yardım sonuçları listesi elde edersiniz.
- Bir arama terimine (işlev gibi) sağ tık tıklar ve Yardım on komutu **seçerek** ilgili işlev için yardım açılır. Ayrıca, herhangi bir **seçim için Yardım'ı** da çağırarak.

    ![Sağ tıklama bağlam menüsü aracılığıyla yardım faturalama](media/help-right-click.png)

> [!Tip]
> Tümleşik yardımı bir tarayıcıda açmak için R Araçları **Seçenekleri'ne tıklayın** ve  >   **F1 Web Tarayıcısı seçeneğini olarak** `External` ayarlayın. Bkz. [Seçenekler.](options-for-r-tools-in-visual-studio.md)

## <a name="integrated-stackoverflow-search"></a>Tümleşik StackOverflow araması

Geliştiriciler R belgelerinde aramanın yanı sıra genellikle kod yazarken StackOverflow araması da sağlar. RTVS bu süreci de basit hale getirmek için kullanılabilir. Bir terime veya seçime sağ tıklayın, **Web'de** ara komutunu (**Ctrl** + **F1**) seçin Visual Studio arama sonuçlarının kapsamı StackOverflow olarak belirtilen bir pencere açılır:

![Web araması sonuçları Visual Studio](media/help-web-search-results.png)

R Araçları Seçenekleri F1 Web arama dizesi seçeneği aracılığıyla eklenen `R site:stackoverflow`   >    >  **scoping dizesini değiştirebilirsiniz:**

![F1 Web arama dizesi seçeneğini değiştirme](media/options-dialog.png)

Sonuçları bir tarayıcıda göstermeyi tercih ederseniz, **F1 Web Tarayıcısı seçeneğini** Seçenekler'de açıklandığı gibi [değiştirebilirsiniz.](options-for-r-tools-in-visual-studio.md)