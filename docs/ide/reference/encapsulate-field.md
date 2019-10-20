---
title: Bir alanı bir özelliğe yeniden düzenleme
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0e47a62fcea8306c22564e50adde436b4f35e549
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654474"
---
# <a name="encapsulate-a-field-refactoring"></a>Alanı yeniden düzenlemeyi yalıtma

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir alanı bir özelliğe dönüştürmenizi ve yeni oluşturulan özelliği kullanmak için o alanın tüm kullanımlarını güncelleştirmenizi sağlar.

**Ne zaman:** Bir alanı özelliğe taşımak ve bu alana yapılan tüm başvuruları güncelleştirmek istiyorsunuz.

**Neden:** Diğer sınıflara bir alana erişim vermek istiyor, ancak bu sınıfların doğrudan erişimine sahip olmasını istemiyorum.  Alanı bir özellikte sarmalayarak, atanan değeri doğrulamak için kod yazabilirsiniz.

## <a name="how-to"></a>Nasıl yapılır

1. Kapsüllemek için alanın adının içine metin imlecini vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod-C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/encapsulate-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **CTRL + R**, ardından **CTRL + E**tuşlarına basın.  (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
      - **Ctrl** + tuşuna basın **.** **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılan penceresinde **alan girişini yalıtma** ' yı seçin.
   - **Tığında**
      - > Düzenle ' yi seçin **> alanı kapsülleyebilirsiniz**.
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinde **alan girişini yalıt** ' ı seçin.

   Seçim | Açıklama
   --------- | -----------
   **Alanı kapsülle (ve özellik kullan)** | Alanı bir özelliği ile kapsüller ve oluşturulan özelliği kullanmak için alanın tüm kullanımlarını güncelleştirir
   **Alanı yalıtma (ancak yine de alan kullan)** | Alanı bir özelliği ile kapsüller, ancak alanın tüm kullanımlarını dokunulmamış halde bırakır

   Özelliği oluşturulur ve seçilirse alanın başvuruları güncellenir.

   > [!TIP]
   > Sonucun kendisine işlemeden önce [ne olacağını görmek için](../../ide/preview-changes.md) açılan penceredeki **Değişiklikleri Önizle** bağlantısını kullanın.

   - C#:

      ![Özellik sonucunu yalıtma-C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Özellik sonucunu yalıtma-Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)