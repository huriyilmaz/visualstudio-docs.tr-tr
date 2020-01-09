---
title: İçeri aktarma öğelerini göster
description: Mac için Visual Studio içinde IntelliSense 'i genişletmek için Içeri aktarma öğelerini göster ' i kullanın.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451512"
---
# <a name="show-import-items"></a>İçeri aktarma öğelerini göster

Mac için Visual Studio, IntelliSense tamamlanma listenizde projenize aktarılmasa bile, tüm kullanılabilir türleri gösterebilir. İçeri aktarılmamış bir öğe seçerek, kaynak dosyanıza doğru `using` ifade eklenecektir.

![İçeri aktarma öğelerine genel bakış](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Nasıl etkinleştirilir

Bu özelliği etkinleştirmek için **Visual Studio** > **tercihleri** aracılığıyla **tercihleri** açın ve **IntelliSense** > **metin Düzenleyicisi** ' ne gidin. IntelliSense 'de ek öğeleri etkinleştirmek için **içeri aktarma öğelerini göster** kutusunu işaretleyin.

![öğeleri içeri aktarma seçeneğini göster](media/show-import-items.png)

## <a name="usage"></a>Kullanım

**İçeri aktarma öğelerini göster**' i etkinleştirdikten sonra, bir öğeyi içeri aktarmak için özelliğini kullanma işlemi IntelliSense içindeki normal eylemlere benzerdir. Kod yazdığınızda geçerli olan öğeler tamamlanma listesini dolduracaktır. Bu, henüz içeri aktarılmayan öğeleri içerir. İçe aktarılmayan öğeler öğenin sağında tam ad alanını gösterir. bu sayede, projenizde hangi içeri aktarma yaptığınız içeri aktarmaları görebilirsiniz.

![İçeri aktarma öğeleri listesini göster](media/show-import-items-list.png)

IntelliSense listesinde, ad alanları `using` bir bildirim tarafından şu anda başvurulmayan üyelerin yanında gösterilir. Listeden bu öğelerden birini seçerseniz, bu üye kodunuza eklenir _ve_ `using` deyimin dosyanın en üstüne eklenir. Kodlanmış olarak zaten başvurulan türlerin üyeleri IntelliSense 'de ad alanını göstermez.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı eylemler (Windows üzerinde Visual Studio)](/visualstudio/ide/quick-actions)
- [Kodu yeniden düzenleme (Windows üzerinde Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
