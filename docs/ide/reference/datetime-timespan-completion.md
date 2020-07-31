---
title: IntelliSense menüsünde DateTime ve TimeSpan tamamlama
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471564"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>IntelliSense menüsünde DateTime ve TimeSpan tamamlama

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** DateTime ve TimeSpan dize değişmez değeri ve IntelliSense menüsünde dize tamamlamayı Biçimlendir.

**Ne zaman:** DateTime ve TimeSpan dize değişmez değeri ve biçim dizesi yazmak istiyorsunuz. IntelliSense, karakterlerin her birinin ne anlama geldiğini temel tamamlamayı ve bir açıklama sağlar. 

**Neden:** DateTime biçimlerini hatırlama zordur ve IntelliSense bunu yazmanıza yardımcı olabilir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi tarih/saat veya TimeSpan Biçim dizesine yerleştirin.
2. **Ctrl** + **IntelliSense** menüsünü tetiklemek için CTRL +**boşluk** tuşlarına basın.
3. Eklemek istediğiniz karakteri seçin.

   ![Tarih saat tamamlama IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
