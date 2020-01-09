---
title: Bir yöntemi geçersiz kılma oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569250"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio'da bir geçersiz kılma oluşturma

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** geçersiz kılınabilir bir yöntemi için kod bir taban sınıftan hemen oluşturmanıza olanak tanır.

**Ne zaman:** bir temel sınıf yöntemini geçersiz kılın ve imza otomatik olarak oluşturmak istiyorsunuz.

**Neden:** ancak bu özellik imzası otomatik olarak oluşturur, yöntem imzası kendiniz yazabilirsiniz.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Tür `override` içinde C# veya `Overrides` Visual Basic'te, ardından bir boşluk istediğiniz bir geçersiz kılma yöntemi eklemek için.

   - C#:

      ![IntelliSense geçersiz kılC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense VB geçersiz kıl](media/override-intellisense-vb.png)

2. Taban sınıfından geçersiz kılmak istediğiniz yöntemi seçin.

   > [!TIP]
   > - Özellik simgesi kullanın ![Özellik simgesi](media/override-property-cs.png) Özellikler listesinde gizlemek veya göstermek için.
   > - Yöntem simgesi kullanın ![Yöntem simgesi](media/override-method-cs.png) yöntemleri listesindeki gizlemek veya göstermek için.

   Seçili yöntemi veya özelliği geçersiz kılma uygulanması hazır sınıfa eklenir.

   - C#:

       ![Sonucu geçersiz kılC#](media/override-result-cs.png)

   - Visual Basic:

       ![VB sonucu geçersiz kıl](media/override-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
