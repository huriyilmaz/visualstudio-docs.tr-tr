---
title: Bir yöntemi geçersiz kılma oluştur
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668441"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio 'da bir geçersiz kılma oluştur

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** , Bir temel sınıftan geçersiz kılınabilen her bir yöntem için kodu hemen oluşturmanıza olanak sağlar.

**Ne zaman:** Bir temel sınıf yöntemini geçersiz kılmak ve imzayı otomatik olarak oluşturmak istiyorsunuz.

**Neden:** Yöntem imzasını kendiniz yazabilirsiniz, ancak bu özellik imzayı otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. @No__t_0, ardından C# bir geçersiz kılma yöntemi eklemek istediğiniz Visual Basic içine veya `Overrides` yazın.

   - C#:

      ![IntelliSense 'i geçersiz kılC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense VB 'yi geçersiz kıl](media/override-intellisense-vb.png)

2. Temel sınıftan geçersiz kılmak istediğiniz yöntemi seçin.

   > [!TIP]
   > - Özellik simgesini kullanın ![Özellik simgesi](media/override-property-cs.png) Listedeki özellikleri göstermek veya gizlemek için.
   > - Yöntem simgesini kullanın ![Yöntem simgesi](media/override-method-cs.png) listedeki yöntemleri göstermek veya gizlemek için.

   Seçilen yöntem veya özellik, bir geçersiz kılma olarak sınıfa eklenir ve uygulanmasına hazırlanın.

   - C#:

       ![Geçersiz kılma sonucuC#](media/override-result-cs.png)

   - Visual Basic:

       ![Geçersiz kılma sonucu VB](media/override-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)