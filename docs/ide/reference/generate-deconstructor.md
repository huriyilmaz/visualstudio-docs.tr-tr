---
title: Oluşturucu kaldırma hızlı eylemi oluştur
description: Hızlı Eylemler ve yeniden düzenlemeler menüsünü kullanarak yeni bir Deconstructor için yöntem Saplamasının hemen nasıl oluşturulacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a4c243ab46858a4c8eb944d485900718b685bf5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897960"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Visual Studio 'da bir Deconstructor oluşturma

Bu kod üretimi için geçerlidir:

- C#

**Ne:** Yeni bir Deconstructor için yöntem saplaması 'nı hemen üretmenizi sağlar.

**Ne zaman:** Türü otomatik olarak doğru bir şekilde yapılandırmak istiyorsunuz.

**Neden:** Bir deoluşturucuyu el ile yazabilirsiniz, ancak bu özellik, sizin için doğru çıkış parametreleriyle saplama oluşturur.

## <a name="generate-a-deconstructor"></a>Deconstructor oluştur

1. İstenen çıkış parametreleriyle yeni bir tür bildirin. Bu bildirim, bildiriğiniz ile eşleşen bir kaldırma örneği bulunamadığında hataya neden olur.

   ![Eksik oluşturucuyu kaldırma hatası](media/deconstruct.png)

2. Aşağıdaki adımlardan birini uygulayın:

   - **Klavye**
      - Bildirimindeki imleç ile CTRL + ' yi seçin. **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
   - **Fare**
      - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.
      - :::image type="icon" source="media/screwdriver.png":::Metin imleci, sınıftaki boş satırda varsa sol kenar boşluğunda görünen simgeyi seçin.

      ![Deconstructor kodu düzeltmesini oluştur](media/deconstruct-codefix.png)

3. Deconstructor oluşturmak için **' Myınternalclass. Deyapýsý ' metodunu oluştur** ' u seçin.

   ![Sonuç Deconstructor kodu](media/deconstruct-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)