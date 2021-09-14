---
title: Bir alanı bir özellik olarak yeniden düzenleme
description: Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanarak bir alanı bir özele dönüştürmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3c60840fcbf0953c308bec174c49058e7f94163e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725752"
---
# <a name="encapsulate-a-field-refactoring"></a>Bir alanı yeniden düzenlemeyi kapsülleme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir alanı özelliğine çevirmenizi ve bu alanın tüm kullanımlarını yeni oluşturulan özelliği kullanmak üzere güncelleştirmenizi sağlar.

**Ne zaman:** Bir alanı bir özellik içine taşımak ve bu alana yapılan tüm başvuruları güncelleştirmek istediğiniz.

**Neden:** Diğer sınıflara bir alana erişim vermek ancak bu sınıfların doğrudan erişime sahip olmak istemiyor.  Alanı bir özellikte sarmalamanız, örneğin, atanan değeri doğrulamak için kod yazabilirsiniz.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini vurgulayın veya alanın adının içine yerleştirerek kapsülleme:

   - C#:

       ![Vurgulanan kod - C #](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/encapsulate-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R tuşlarına** ve ardından **Ctrl+E tuşlarına basın.**  (Klavye kısayolu, seçtiğiniz profile göre farklı olabilir.)
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** ve Önizleme penceresi açılır penceresinden Alan girişini kapsülle'yi seçin. 
   - **Fare**
      - Alanı **Kapsülle >'> Düzenle'yi seçin.**
      - Koda sağ tıklayın, Hızlı **Eylemler ve Yeniden** Düzenleme menüsünü  seçin ve Önizleme penceresi açılır penceresinden Alan girişini kapsülle'yi seçin.

   Seçim | Açıklama
   --------- | -----------
   **Alanı kapsülle (ve özelliğini kullan)** | alanını bir özellik ile kapsüller ve oluşturulan özelliği kullanmak için alanın tüm kullanımlarını günceller
   **Alanı kapsülle (ancak yine de alanını kullan)** | alanını bir özelliğiyle kapsüller, ancak alanın tüm kullanımlarını dokunulmadan bırakır

   özelliği oluşturulur ve seçilirse alana yapılan başvurular güncelleştirilir.

   > [!TIP]
   > Yürütmeden **önce** sonucun ne olacağını görmek için açılan pencerede [Değişiklikleri önizle](../../ide/preview-changes.md) bağlantısını kullanın.

   - C#:

      ![Özellik sonucu kapsülle - C #](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Özellik sonucu kapsülle - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
