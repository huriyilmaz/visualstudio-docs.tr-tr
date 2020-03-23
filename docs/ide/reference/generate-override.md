---
title: Bir yöntem geçersiz kılma oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569250"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio'da geçersiz kılma oluşturma

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Taban sınıftan geçersiz kılınabilecek herhangi bir yöntem için kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Taban sınıf yöntemini geçersiz kılmak ve imzayı otomatik olarak oluşturmak istiyorsunuz.

**Neden:** Yöntem imzasını kendiniz yazabilirsiniz, ancak bu özellik imzayı otomatik olarak oluşturur.

## <a name="how-to"></a>Nasıl yapılır

1. C# veya `override` `Overrides` Visual Basic'e ve ardından geçersiz kılma yöntemi eklemek istediğiniz bir boşluk yazın.

   - C#:

      ![IntelliSense C'yi geçersiz kılın #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Geçersiz kılma IntelliSense VB](media/override-intellisense-vb.png)

2. Taban sınıftan geçersiz kılmak istediğiniz yöntemi seçin.

   > [!TIP]
   > - Özellik simgesini kullanma ![Özellik simgesi](media/override-property-cs.png) özellikleri listede göstermek veya gizlemek için.
   > - Yöntem simgesini kullanma ![Yöntem simgesi](media/override-method-cs.png) yöntemleri listede göstermek veya gizlemek için.

   Seçili yöntem veya özellik, uygulanmaya hazır bir geçersiz kılma olarak sınıfa eklenir.

   - C#:

       ![Geçersiz kılma sonucu C #](media/override-result-cs.png)

   - Visual Basic:

       ![Geçersiz kılma sonucu VB](media/override-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
