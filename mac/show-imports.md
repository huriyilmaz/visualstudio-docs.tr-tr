---
title: Alma maddelerini göster
description: Mac için Visual Studio'da IntelliSense'i genişletmek için İthalatı Göster Öğelerini kullanın.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451512"
---
# <a name="show-import-items"></a>Alma maddelerini göster

Mac için Visual Studio, projenize aktarılmasalar bile tüm kullanılabilir türleri IntelliSense tamamlama listenizde gösterebilir. İçe aktarılmadı bir öğe seçerek, doğru `using` ifade kaynak dosyanıza eklenir.

![alma maddelerine genel bakış ı gösterme](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Nasıl etkinleştirilir?

Bu özelliği etkinleştirmek için **Visual Studio** > **Tercihleri** aracılığıyla **Tercihleri** açın ve **Metin Editörü** > **IntelliSense'e**gidin. Kutuyu işaretleyin IntelliSense'de ek öğeleri etkinleştirmek için **içe aktarma öğelerini göster.**

![alma maddelerini gösterme seçeneğini göster](media/show-import-items.png)

## <a name="usage"></a>Kullanım

**Alma maddelerini göster'i**etkinleştirdikten sonra, bir öğeyi almak için özelliği kullanma işlemi IntelliSense'deki normal eylemlere benzer. Kod yazdıkça, geçerli olan öğeler tamamlanma listesini doldurulur. Bu, henüz aktarılmamış öğeleri içerir. İçe aktarılan öğeler, tam ad alanlarını öğenin sağında göstererek projenize hangi içeri giren içeri aldığınızı görmenizi sağlar.

![alma maddeleri listesini göster](media/show-import-items-list.png)

IntelliSense listesinde, ad alanları şu anda bir `using` deyimle başvurulmayan üyelerin yanında gösterilir. Listeden bu öğelerden birini seçerseniz, üye kodunuza _and_ eklenir `using` ve ekstre dosyanın üst bölümüne eklenir. Kodlanmış türlerdeki üyeler ad alanlarını IntelliSense'de göstermezler.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Windows'ta Visual Studio)](/visualstudio/ide/quick-actions)
- [Refactor kodu (Windows'ta Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
