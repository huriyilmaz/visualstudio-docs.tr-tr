---
title: Türler & uzantı yöntemleri için IntelliSense tamamlama
description: Henüz bir yönergeyle içeri aktarmadığınız türler ve genişletme yöntemleri için IntelliSense tamamlamayı kullanma `using` .
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f011357c3c72d05c280c2dc19a2e7282a10920c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151502"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>İçeri aktarılmamış türler ve genişletme yöntemleri için IntelliSense tamamlama

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** IntelliSense, içeri aktarılmayan türler ve genişletme yöntemleri için tamamlama sağlar.

**Ne zaman:** Projenizde zaten bağımlılığı olan bir tür veya uzantı yöntemleri kullanmak istiyorsunuz, ancak using deyimleri dosyanıza henüz eklenmemiş.

**Neden:** Using ifadesini dosyanıza el ile eklemeniz gerekmez.

## <a name="how-to"></a>Nasıl yapılır

1. Projenize bağımlılığı olan bir tür veya genişletme yönteminin adını yazmaya başladıktan sonra, IntelliSense size öneriler verecektir. İçeri aktarılmayan ad alanlarından alınan öğeler, sonek olarak gösterilen kapsayıcı ad alanı olacaktır.

   > [!TIP]
   > Tamamlama listesinin sol alt tarafında görüntülenen **Genişleticisi düğmesini (alt + A)** kullanarak, içeri aktarılmayan ad alanlarından öğeleri isteğe bağlı olarak gösterebilir/gizleyebilirsiniz. Varsayılan davranışı değiştirmek için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **C#**  /  **temel**  >  **IntelliSense** ' e gidin ve **içeri aktarılmayan ad alanlarından öğeleri göster**' i arayın.

2. İçeri aktarılmamış bir öğeyi seçin ve işleyin.

   Using deyimleri dosyanıza otomatik olarak eklenecektir.

   ![İçeri aktarılmamış türler için IntelliSense tamamlama](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense](../using-intellisense.md)
- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
