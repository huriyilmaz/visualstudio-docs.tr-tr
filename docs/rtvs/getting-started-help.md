---
title: R için Yardım penceresi
description: R için yardım, Visual Studio 'daki etkileşimli pencereye aracılığıyla doğrudan tümleşiktir mi? komutundaki.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62950584"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio için R Araçları Yardım

R yardımı, doğrudan Visual Studio 'daki etkileşimli pencereye tümleştirilir. Komutunu kullandığınızda, `?` Örneğin `?mtcars` , R belgelerindeki yardım bir Visual Studio penceresinde görünür:

![Visual Studio 'da Yardım penceresi](media/help-window.png)

> [!Tip]
> Visual Studio 'daki tüm diğerleri gibi Yardım penceresi, istediğiniz gibi düzenlenebilir ve yerleştirilebilir. Bkz. [Visual Studio 'da pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).
>
> Yardım sonuçlarını bir tarayıcıda açmak için **R araçları**  >  **Seçenekler** menüsünü seçin ve **R yardım Browser** özelliğini olarak ayarlayın `External` . Bkz. [Seçenekler](options-for-r-tools-in-visual-studio.md).

Yardım aramak için, komutu ve `??` ardından arama terimini kullanın. Arama terimi boşluk içeriyorsa, tırnak işaretleri kullanın:

```R
??"Motor Trend"
```

![Yardım arama sonuçları](media/help-search1.png)

Yardım penceresinde Ayrıca, R belgelerinde doğrudan daha fazla arama yapmak için kullanabileceğiniz bir arama girişi alanı vardır:

![Giriş alanını kullanarak arama sonuçlarına yardım edin](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Tümleşik Yardım araması

Geliştiriciler, genellikle işlev adları, veri kümeleri ve diğer öğeler hakkında yardım almak için R belgelerinde arama yapılır. Visual Studio için R Araçları (RTVS), yardım aramalarını doğrudan düzenleyici ve etkileşimli pencereler ile tümleştirerek işlemi basitleştirir.

- Otomatik tamamlanmış bir işlem sırasında **F1** tuşuna basmak, alt dizeyle eşleşen yardım sonuçlarının bir listesini oluşturur.
- Bir arama terimine (bir işlev gibi) sağ tıklayın ve **Yardım hakkında** komutu seçildiğinde bu işlev için yardım açılır. Ayrıca, herhangi bir seçim için **Yardım** çağırabilirsiniz.

    ![Sağ tıklama bağlam menüsünde Yardım çağırma](media/help-right-click.png)

> [!Tip]
> Tümleşik yardımı bir tarayıcıda açmak için **R araçları**  >  **Seçenekler** ' i seçin ve **F1 web tarayıcısını** olarak ayarlayın `External` . Bkz. [Seçenekler](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Tümleşik StackOverflow araması

Geliştiriciler R belgelerinde aramanın yanı sıra, genellikle kod yazarken StackOverflow arar. RTVS bu süreci de basitleştirir. Bir terime veya seçime sağ tıklayın, **Web 'de ara** komutunu seçin (**CTRL** + **F1**) ve Visual Studio StackOverflow için arama sonuçları kapsamındaki bir pencere açar:

![Visual Studio 'da Web araması sonuçları](media/help-web-search-results.png)

Eklenen kapsam dizesini, `R site:stackoverflow` **R araçları**  >  **seçenekleri**  >  **F1 web arama dizesi** seçeneği aracılığıyla değiştirebilirsiniz:

![F1 web arama dizesi seçeneğini değiştirme](media/options-dialog.png)

Sonuçları bir tarayıcıda göstermeyi tercih ediyorsanız, [Seçenekler](options-for-r-tools-in-visual-studio.md)' de açıklandığı gibi **F1 web tarayıcısı** seçeneğini değiştirin.