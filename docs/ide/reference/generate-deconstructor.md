---
title: Dekonstrüktör hızlı eylem oluşturma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531892"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Visual Studio'da dekonstrüktör oluşturma

Bu kod oluşturma için geçerlidir:

- C#

**Ne:** Hemen yeni bir deconstructor için yöntem saplama oluşturmanızı sağlar.

**Ne zaman:** Türünüzün düzgün bir şekilde yapısızlaştırılmasını istiyorsunuz.

**Neden:** El ile bir deconstructor yazabilirsiniz, ancak bu özellik doğru çıkış parametreleri ile sizin için saplama oluşturur.

## <a name="generate-a-deconstructor"></a>Bir dekonstrüktör oluşturun

1. İstenilen çıkış parametreleri belirtilen yeni bir tür bildirin. Bu bildirim, bildirgenizle eşleşen bir deconstruct örneği bulunamadığında hataya neden olur.

   ![Eksik dekonstrüktör hatası](media/deconstruct.png)

2. Aşağıdaki adımlardan birini izleyin:

   - **Klavye**
      - Bildiriminizdeki imleçle Ctrl+'yı seçin. **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Şunu seçerek: ![Tornavida](media/screwdriver.png) metin imleci sınıftaki boş satırda zaten duruyorsa, sol kenar boşluğunda görünen simge.

      ![Deconstructor kod düzeltmesi oluşturma](media/deconstruct-codefix.png)

3. Dekonstrüktör oluşturmak için **'MyInternalClass.Deconstruct' yöntemini** oluştur'u seçin.

   ![Ortaya çıkan dekonstrüktör kodu](media/deconstruct-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)