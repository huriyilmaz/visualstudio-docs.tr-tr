---
title: Using deyimleri oluşturma
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 78786e6e6e7a8e5d8a8766138cb1a54a49416f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610884"
---
# <a name="add-missing-usings-in-visual-studio"></a>Visual Studio 'da eksik using 'leri ekleme

Bu kod üretimi için geçerlidir:

- C#

**Ne:** , Kopya ve yapıştırılan kod için gerekli içeri aktarmaları veya [kullanım yönergelerini](/dotnet/csharp/language-reference/keywords/using-directive) hemen eklemenizi sağlar.

**Ne zaman:** Projenizde veya diğer kaynaklardaki farklı yerlerden kod kopyalamak ve yeni koda yapıştırmak yaygın bir uygulamadır. Bu hızlı eylem, kopya ve yapıştırılan kod için eksik içeri aktarmalar yönergelerini bulur ve sonra bunları eklemenizi ister.

**Neden:** Hızlı eylem gerekli içeri aktarmaları otomatik olarak eklediğinden, kodunuzun ihtiyaç duyduğu `using` yönergelerini el ile kopyalamanız gerekmez.

## <a name="add-missing-usings-refactoring"></a>Eksik using 'leri yeniden düzenleme Ekle

1. Kodu bir dosyadan kopyalayın ve gerekli `using` yönergeleri dahil etmeden yeni bir dosyaya yapıştırın. Ortaya çıkan hata, eksik `using` yönergelerini ekleyen bir kod düzeltmesine eşlik eder.

    > [!NOTE]
    > **Araçlar > seçenekler > metin düzenleyicisi > C# yönergeleri kullanarak Gelişmiş > >** bu öneriyi etkinleştirmeniz gerekir.

2. CTRL + seçeneğini belirleyin. **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü açmak için.

    ![Using deyimleri oluşturma](media/generate-using-codefix.png)

3. Eksik başvuruyu eklemek için **\> \<your başvurusunu kullanmayı** seçin.

    ![Kullanımlar sonucu oluştur](media/generate-using-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
