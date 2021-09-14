---
title: Yöntem geçersiz kılma oluşturma
description: Temel sınıftan geçersiz kılınan herhangi bir yöntem için kodu hemen nasıl oluşturabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 0724500bf90e3e0253d936facf4be62f68533ba1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726881"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio'de geçersiz kılma oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir temel sınıftan geçersiz kılınabilir herhangi bir yöntem için kodu hemen oluşturma sağlar.

**Ne zaman:** Bir temel sınıf yöntemini geçersiz kılmak ve imzayı otomatik olarak oluşturmak istediğiniz.

**Neden:** Yöntem imzasını kendiniz yazabilirsiniz, ancak bu özellik imzayı otomatik olarak üretir.

## <a name="how-to"></a>Nasıl yapılır

1. C# veya Visual Basic yazın ve ardından bir boşluk yazın; burada `override` bir geçersiz kılma yöntemi eklemek istediğiniz `Overrides` yer.

   - C#:

      ![IntelliSense C'yi geçersiz kılma #](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense VB'yi geçersiz kılma](media/override-intellisense-vb.png)

2. Temel sınıftan geçersiz kılmak istediğiniz yöntemi seçin.

   > [!TIP]
   > - Özellik simgesini kullanma ![Özellik simgesi](media/override-property-cs.png) listede özellikleri göstermek veya gizlemek için.
   > - Yöntem simgesini kullanma ![Yöntem simgesi](media/override-method-cs.png) listede yöntemleri göstermek veya gizlemek için.

   Seçilen yöntem veya özellik, uygulamaya hazır bir geçersiz kılma olarak sınıfına eklenir.

   - C#:

       ![Geçersiz kılma sonucu C #](media/override-result-cs.png)

   - Visual Basic:

       ![Geçersiz kılma sonucu VB](media/override-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
