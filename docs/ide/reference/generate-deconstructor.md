---
title: Oluşturucu kaldırma hızlı eylemi oluştur
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531892"
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
      - Şunu seçerek: ![Screwdriver](media/screwdriver.png) Sol kenar boşluğunda, metin imleci sınıfında zaten boş satırda görünen simge.

      ![Deconstructor kodu düzeltmesini oluştur](media/deconstruct-codefix.png)

3. Deconstructor oluşturmak için **' Myınternalclass. Deyapýsý ' metodunu oluştur** ' u seçin.

   ![Sonuç Deconstructor kodu](media/deconstruct-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizle](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)