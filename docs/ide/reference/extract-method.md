---
title: Bir yöntemi Ayıkla
description: Kodu seçip CTRL + R, CTRL + M yazarak kodun bir parçasını kendi yöntemine dönüştürün.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 10f8b09defe7c4e156b015f590f1b494ba2704a164f0ce67625d1cac5b93e653
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121304378"
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

       ![Program sınıfı için C# kodunu gösteren ekran görüntüsü. Bu sınıfın ana işlevinde, bir kod satırı vurgulanır.](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![ana Sub için Visual Basic kodu gösteren ekran görüntüsü. Bu alt öğesinde, bir kod satırı vurgulanır.](media/extractmethod-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL + R**, ardından **CTRL + M** tuşlarına basın. (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinden **yöntemi Ayıkla** ' yı seçin.
   - **Fare**
      - **> ayıkla > Düzenle**' yi seçin.
      - Koda sağ tıklayın ve **> Ayıkla metodunu ayıkla > yeniden Düzenle**' yi seçin.
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **yöntemi Ayıkla** ' yı seçin.

   Yöntemi hemen oluşturulacaktır. Buradan, şimdi yeni adı yazarak yöntemi yeniden adlandırabilirsiniz.

   > [!TIP]
   > Ayrıca, bu yeni adı kullanmak için açıklamaları ve diğer dizeleri güncelleştirebilir ve IDE 'nizin sağ üst köşesinde görünen **Yeniden Adlandır** kutusunda bulunan onay kutularını kullanarak değişiklikleri kaydetmeden önce [Önizleme](../../ide/preview-changes.md) yapabilirsiniz.

   - C#:

      ![Program sınıfı için C# kodunu gösteren ekran görüntüsü. Bir yöntem adı vurgulanır ve açılan pencereyi yeniden adlandır penceresi açıktır.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![ana Sub için Visual Basic kodu gösteren ekran görüntüsü. Bir yöntem adı vurgulanır ve açılan pencereyi yeniden adlandır penceresi açıktır.](media/extractmethod-rename-vb.png)

3. Değişikliğin ne kadar memnunsanız **Uygula** düğmesini seçin veya **ENTER** tuşuna basın ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
