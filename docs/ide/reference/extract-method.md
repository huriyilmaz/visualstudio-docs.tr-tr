---
title: Bir yöntemi
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi yöntemine dönüştürün.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 50f14cc2a7eafe5d65e0c6a6af54bafa2ebb5a1f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569705"
---
# <a name="extract-a-method-refactoring"></a>Ayıklama yöntemi yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** kendi yönteme kodun bir parçasını kapatmanızı sağlar.

**Ne zaman:** başka bir yöntemden çağrılması gereken bazı yöntemi mevcut kodun bir parçasını sahip.

**Neden:** , Kopyala/kod Yapıştır, ancak çoğaltma için neden. Bu parça halinde diğer herhangi bir yöntemle serbestçe çağrılabilir kendi yöntemi yeniden düzenleme daha iyi bir çözümdür.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Ayıklanacak kod vurgular:

   - C#:

       ![Vurgulanan kod-C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu - Visual Basic](media/extractmethod-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl + R**, ardından **Ctrl + M**. (Bağlı olarak hangi profilinde seçtiğiniz klavye kısayolu farklı olabileceğini unutmayın.)
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **yöntemi ayıklama** gelen önizleme penceresi açılır.
   - **Fare**
      - Seçin **Düzenle > yeniden düzenleyin > yöntemi Ayıkla**.
      - Kod sağ tıklayıp **yeniden düzenleyin > Ayıkla > yöntemi ayıklama**.
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **yöntemi ayıklama** gelen önizleme penceresi açılır.

   Yöntem hemen oluşturulur. Buradan, yeni bir ad yazarak artık yöntemi adlandırabilirsiniz.

   > [!TIP]
   > Ayrıca açıklamalar ve diğer dizeleri bu yeni adı kullanacak şekilde güncelleştirebilirsiniz yanı [değişiklik önizlemesi](../../ide/preview-changes.md) önce kaydetme, içinde onay kutularını kullanarak **Yeniden Adlandır** en üstünde açılan kutusunda IDE'nizi sağında.

   - C#:

      ![Metodu yeniden adlandır-C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Yöntemi - Visual Basic yeniden adlandır](media/extractmethod-rename-vb.png)

3. Değişiklik ile tamamladığınızda seçin **Uygula** düğme veya basın **Enter** ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
