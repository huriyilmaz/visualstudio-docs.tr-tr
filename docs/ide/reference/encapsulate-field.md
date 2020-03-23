---
title: Alanı bir özelliğe yeniden düzenleme
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: db0bd17cd0bead3807f857b2198b8d4ea4c72ffb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569718"
---
# <a name="encapsulate-a-field-refactoring"></a>Bir alan refactoring kapsülleme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir alanı bir özelliğe dönüştürmenizi ve yeni oluşturulan özelliği kullanmak için bu alanın tüm kullanımlarını güncelleştirmenizi sağlar.

**Ne zaman:** Bir alanı bir özelliğe taşımak ve bu alana yapılan tüm başvuruları güncelleştirmek istiyorsunuz.

**Neden:** Diğer sınıflara bir alana erişim vermek istiyorsunuz, ancak bu sınıfların doğrudan erişimi olmasını istemiyorsun.  Alanı bir özelliğe sararak, atanan değeri doğrulamak için kod yazabilirsiniz, örneğin.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini alanın adının içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/encapsulate-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R**tuşuna basın, sonra **Ctrl+E tuşuna**basın.  (Klavye kısayol'unuzun seçtiğiniz profile bağlı olarak farklı olabileceğini unutmayın.)
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek ve Önizleme penceresinden **encapsulate alan** girişini seçin.
   - **Fare**
      - Refactor **> Encapsulate Alanını**> Edit'i seçin.
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden alan girişini **encapsulate'i** seçin.

   Seçim | Açıklama
   --------- | -----------
   **Alanı kapsülle (ve kullanım özelliği)** | Alanı bir özellik ile kapsüller ve oluşturulan özelliği kullanmak için alanın tüm kullanımlarını güncelleştirir
   **Alanı kapsülle (ancak yine de alanı kullanın)** | Alanı bir özellik ile kapsüller, ancak alanın tüm kullanımları el değmemiş bırakır

   Özellik oluşturulur ve seçilirse alana yapılan başvurular güncelleştirilir.

   > [!TIP]
   > Sonuç işlemeden önce [sonucun ne olacağını görmek için](../../ide/preview-changes.md) açılır penceredeki Önizleme **değişiklikleri** bağlantısını kullanın.

   - C#:

      ![Encapsulate Özellik sonucu - C #](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Encapsulate Özellik sonucu - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
