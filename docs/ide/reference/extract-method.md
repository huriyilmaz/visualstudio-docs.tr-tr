---
title: Bir yöntem ayıklama
description: Kodu seçerek ve Ctrl+R, Ctrl+M yazarak kod parçasını kendi yöntemine dönüştürün.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569705"
---
# <a name="extract-a-method-refactoring"></a>Bir yöntem refactoring ayıklama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Kod parçasını kendi yöntemine dönüştürmenizi sağlar.

**Ne zaman:** Başka bir yöntemden çağrılması gereken bir yöntemde varolan kodun bir parçası var.

**Neden:** Bu kodu kopyalayabilir/yapıştırabilirsiniz, ancak bu yinelemeye yol açar. Daha iyi bir çözüm, bu parçayı başka bir yöntemle serbestçe çağrılabilen kendi yöntemine yeniden faktör haline getirmektir.

## <a name="how-to"></a>Nasıl yapılır

1. Çıkarılacak kodu vurgulayın:

   - C#:

       ![Vurgulanan kod- C #](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/extractmethod-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R**tuşuna basın, sonra **Ctrl+M**tuşuna basın. (Klavye kısayol'unuzun seçtiğiniz profile bağlı olarak farklı olabileceğini unutmayın.)
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Faktörler** menüsünü tetiklemek ve Önizleme penceresinden **Ayıklama Yöntemi'ni** seçin.
   - **Fare**
      - **Refactor > Refactor > Extract Metod'u**seçin.
      - Kodu sağ tıklatın ve **Refactor > Extract > Extract Metodu'nu**seçin.
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **Ayıklama Yöntemi'ni** seçin.

   Yöntem hemen oluşturulur. Buradan, artık yöntemi yalnızca yeni adı yazarak yeniden adlandırabilirsiniz.

   > [!TIP]
   > Ayrıca, IDE'nizin sağ üst kısmında görünen **Yeniden Adlandırma** kutusundaki onay kutularını kullanarak, bu yeni adı kullanmak için yorumları ve diğer dizeleri güncelleştirebilirsiniz ve kaydetmeden önce [değişiklikleri önizleyebilirsiniz.](../../ide/preview-changes.md)

   - C#:

      ![Yeniden adlandırma yöntemi - C #](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Yeniden adlandırma yöntemi - Visual Basic](media/extractmethod-rename-vb.png)

3. Değişiklikten memnun olduğunuzda, **Uygula** düğmesini seçin veya **Enter** tuşuna bastığında değişiklikler tamamlanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
