---
title: İçeri aktarma öğelerini gösterme
description: İçe Aktarma Öğelerini Göster'i kullanarak IntelliSense'i Mac için Visual Studio.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725980"
---
# <a name="show-import-items"></a>İçeri aktarma öğelerini gösterme

Mac için Visual Studio, projenize aktarılmış olsalar bile tüm kullanılabilir türleri IntelliSense tamamlama listeniz içinde gösterebilir. İçe aktarılmış olmayan bir öğe seçerek, `using` kaynak dosyanıza doğru deyim eklenir.

![içeri aktarma öğelerini göstermeye genel bakış](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Etkinleştirme

Bu özelliği etkinleştirmek için Tercihler'i  **Visual Studio'i** açın ve Metin Düzenleyici  >     >  **IntelliSense'e gidin.** **IntelliSense'te ek öğeleri** etkinleştirmek için İçeri aktarma öğelerini göster kutusunu işaretleyin.

![öğeleri içeri aktarmayı göster seçeneği](media/show-import-items.png)

## <a name="usage"></a>Kullanım

İçeri aktarma öğelerini **göster'i** etkinleştir ardından, bir öğeyi içeri aktarma özelliğini kullanma işlemi, IntelliSense'in içindeki normal eylemlere benzer. Siz kod yazarak, geçerli olan öğeler tamamlama listesini tamamlar. Bu, henüz içe aktarılmış olan öğeleri içerir. İçeri aktarılmış olmayan öğeler, öğenin sağında tam ad alanını gösterir ve projenize hangi içeri aktarmaları çekmekte olduğunu görmenizi sağlar.

![içeri aktarma öğeleri listesini göster](media/show-import-items-list.png)

IntelliSense listesinde, şu anda bir deyimi tarafından başvurulmay olan üyelerin yanında ad alanları `using` gösterilir. Listeden bu öğelerden birini seçerseniz, üye kodunuza _eklenir_ ve deyimi `using` dosyanın en üstüne eklenir. Kodlu içinde başvurulan türlerden üyeler, ad alanlarını IntelliSense'te göstermez.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio üzerinde Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)
