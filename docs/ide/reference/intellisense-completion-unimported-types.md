---
title: İthal edilmeyen türler için IntelliSense tamamlama
description: Bir `using` yönergeyle henüz almadığınız türler için IntelliSense tamamlama nasıl kullanılır?
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094258"
---
# <a name="intellisense-completion-for-unimported-types"></a>İthal edilmeyen türler için IntelliSense tamamlama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** IntelliSense, içe aktarılmamış türler için tamamlama sağlar.

**Ne zaman:** Projenizde zaten bir bağımlılık olan bir tür eklemek istiyorsunuz, ancak içeri aktarma ekstresi henüz dosyanıza eklenmedi. 

**Neden:** İçe aktarma ekstresini dosyanıza el ile eklemeniz gerekmez.

## <a name="how-to"></a>Nasıl yapılır

1. Projenizde bağımlılık olan bir tür kullanmaya başladığınızda, IntelliSense size önerilerde bulunacaktır.
2. **Sekme tuşuna**basın. 

   İçe aktarma deyimi dosyanıza eklenir.

   ![İthal edilmeyen türler için IntelliSense tamamlama](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
