---
title: Bir yöntemi Ayıkla
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi yöntemine dönüştürün.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a1ec6ca273f873c82a1bb2c730a9288b5e2ae4ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654388"
---
# <a name="extract-a-method-refactoring"></a>Bir yöntemi yeniden düzenlemeyi Ayıkla

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Kodun bir parçasını kendi yöntemine açmanızı sağlar.

**Ne zaman:** Başka bir yöntemden çağrılması gereken, bazı bir yöntemde var olan kodun bir parçası var.

**Neden:** Bu kodu kopyalayabilir/yapıştırabilir, ancak çoğaltmaya yol açabilir. Daha iyi bir çözüm, bu parçayı, başka bir yöntem tarafından serbestçe çağrılabilen kendi yöntemine yeniden düzenleme yöntemidir.

## <a name="how-to"></a>Nasıl yapılır

1. Ayıklanacak kodu vurgulayın:

   - C#:

       ![Vurgulanan kod-C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/extractmethod-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **CTRL + R**, ardından **CTRL + M**tuşlarına basın. (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinden **yöntemi Ayıkla** ' yı seçin.
   - **Tığında**
      - **> ayıkla > Düzenle**' yi seçin.
      - Koda sağ tıklayın ve **> Ayıkla metodunu ayıkla > yeniden Düzenle**' yi seçin.
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **yöntemi Ayıkla** ' yı seçin.

   Yöntemi hemen oluşturulacaktır. Buradan, şimdi yeni adı yazarak yöntemi yeniden adlandırabilirsiniz.

   > [!TIP]
   > Ayrıca, bu yeni adı kullanmak için açıklamaları ve diğer dizeleri güncelleştirebilir ve IDE 'nizin sağ üst köşesinde görünen **Yeniden Adlandır** kutusunda bulunan onay kutularını kullanarak değişiklikleri kaydetmeden önce [Önizleme](../../ide/preview-changes.md) yapabilirsiniz.

   - C#:

      ![Yöntemi yeniden adlandır-C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Yöntemi yeniden adlandır-Visual Basic](media/extractmethod-rename-vb.png)

3. Değişikliğin ne kadar memnunsanız **Uygula** düğmesini seçin veya **ENTER** tuşuna basın ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)