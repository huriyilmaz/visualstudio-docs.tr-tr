---
title: İçeri aktarma öğelerini gösterme
description: İçe Aktarma Öğelerini Göster'i kullanarak IntelliSense'i Mac için Visual Studio.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3159eba2984049783207bcb550e08cdd277cc1c272ae0cd4814c3a87a0d3c4a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381919"
---
# <a name="show-import-items"></a>İçeri aktarma öğelerini gösterme

Mac için Visual Studio, projenize aktarılmış olsalar bile tüm kullanılabilir türleri IntelliSense tamamlama listeniz içinde gösterebilirsiniz. İçe aktarılmış olmayan bir öğe seçerek, kaynak `using` dosyanıza doğru deyim eklenir.

![içeri aktarma öğelerini göstermeye genel bakış](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Etkinleştirme

Bu özelliği etkinleştirmek için Tercihler'i  **Visual Studio'i** açın ve Metin Düzenleyici  >     >  **IntelliSense'e gidin.** **IntelliSense'te ek öğeleri etkinleştirmek** için İçeri aktarma öğelerini göster kutusunu işaretleyin.

![öğeleri içeri aktarmayı göster seçeneği](media/show-import-items.png)

## <a name="usage"></a>Kullanım

İçeri aktarma öğelerini **göster'i** etkinleştir ardından, bir öğeyi içeri aktarma özelliğini kullanma işlemi, IntelliSense'in içindeki normal eylemlere benzer. Siz kod yazarak geçerli olan öğeler tamamlanma listesini doldurmak için kullanılır. Bu, henüz içe aktarılmış olan öğeleri içerir. İçeri aktarılmış olmayan öğeler, öğenin sağında tam ad alanını gösterir ve projenize hangi içeri aktarmaları çekmekte olduğunu görmenizi sağlar.

![içeri aktarma öğeleri listesini göster](media/show-import-items-list.png)

IntelliSense listesinde, şu anda bir deyimi tarafından başvurulmay olan üyelerin yanında ad alanları `using` gösterilir. Listeden bu öğelerden birini seçerseniz, üye kodunuza eklenir  ve `using` deyimi dosyanın en üstüne eklenir. Kodlu içinde başvurulan türlerden üyeler ad alanlarını IntelliSense'te göstermez.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler (Visual Studio Windows)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Visual Studio üzerinde Windows)](/visualstudio/ide/refactoring-in-visual-studio)
