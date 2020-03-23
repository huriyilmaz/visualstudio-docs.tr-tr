---
title: R için Yardım Penceresi
description: R için Yardım visual Studio interaktif pencereye doğrudan entegre edilir? Komut.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950584"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio için R Tools yardım

R için Yardım visual Studio'daki etkileşimli pencereye doğrudan entegre edilmiştir. R belgelerinden `?` yardım gibi `?mtcars`komutu her kullandığınızda Visual Studio penceresinde görünür:

![Visual Studio'da Yardım penceresi](media/help-window.png)

> [!Tip]
> Yardım penceresi, Visual Studio'daki diğer tüm kişiler gibi, istediğiniz gibi düzenlenebilir ve sabitlenebilir. [Bkz. Visual Studio'da pencere düzenlerini özelleştirin.](../ide/customizing-window-layouts-in-visual-studio.md)
>
> Bir tarayıcıda yardım sonuçlarını açmak için **R Araçları** > **Seçenekleri** menüsünü seçin ve R **Yardım Tarayıcısı** özelliğini ' ye `External`ayarlayın. [Bkz. Seçenekler](options-for-r-tools-in-visual-studio.md).

Yardım aramak için, `??` arama teriminin ardından gelen komutu kullanın. Arama terimi boşluklar içeriyorsa tırnak işaretini kullanın:

```R
??"Motor Trend"
```

![Arama sonuçlarına yardım edin](media/help-search1.png)

Yardım penceresinde ayrıca Doğrudan R belgelerinde daha fazla arama yapabileceğiniz bir arama giriş alanı vardır:

![Giriş alanını kullanarak arama sonuçlarına yardım edin](media/help-search2.png)

## <a name="integrated-help-lookup"></a>Entegre yardım arama

Geliştiriciler genellikle işlev adları, veri kümeleri ve diğer öğeler hakkında yardım için R belgelerinde arama yapar. R Tools for Visual Studio (RTVS), yardım aramalarını doğrudan düzenleyiciye ve etkileşimli pencerelere entegre ederek işlemi kolaylaştırır.

- Otomatik tamamlama işlemi sırasında **F1** tuşuna basıldığında, alt dizeyle eşleşen bir yardım sonuçları listesi üretir.
- Bir arama terimini (işlev gibi) sağ tıklatma ve **komuttaki Yardım'ı** seçmek, bu işlev için yardım açar. Ayrıca herhangi bir seçim için **Yardım** çağırabilirsiniz.

    ![Sağ tıklama bağlam menüsünden yardım çağırmak](media/help-right-click.png)

> [!Tip]
> Bir tarayıcıda tümleşik yardım açmak için **R Araçları** >  `External`**Seçenekleri'ni** seçin ve **F1 Web Tarayıcısını** ' ya ayarlayın. [Bkz. Seçenekler](options-for-r-tools-in-visual-studio.md).

## <a name="integrated-stackoverflow-search"></a>Entegre StackOverflow arama

R belgelerinde arama nın yanı sıra, geliştiriciler kod yazarken genellikle StackOverflow'da arama yapar. RTVS de bu süreci kolaylaştırır. Bir terimi veya seçimi sağ tıklatın, komut **için Arama web'ini** seçin **(Ctrl**+**F1)** ve Visual Studio StackOverflow kapsamına giren arama sonuçlarıiçeren bir pencere açar:

![Visual Studio'da web arama sonuçları](media/help-web-search-results.png)

**R Tools** > **Options** > **F1 Web arama dizesi** seçeneği aracılığıyla eklenen kapsam dizesini `R site:stackoverflow`değiştirebilirsiniz:

![F1 Web arama dizesi seçeneğini değiştirme](media/options-dialog.png)

Sonuçları bir tarayıcıda göstermeyi tercih ederseniz, [Seçenekler'de](options-for-r-tools-in-visual-studio.md)açıklandığı gibi **F1 Web Tarayıcısı** seçeneğini değiştirin.