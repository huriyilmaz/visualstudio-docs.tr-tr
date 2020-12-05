---
title: Using deyimleri oluşturma
description: Hızlı Eylemler ve yeniden düzenlemeler menüsünü kullanarak, gerekli içeri aktarmaları hemen ekleme veya kopya ve yapıştırılan kod için yönergeleri kullanma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 38996d1cda52dfe98b6ce9cf24e5adcca6a8b069
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617168"
---
# <a name="add-missing-usings-in-visual-studio"></a>Visual Studio 'da eksik using 'leri ekleme

Bu kod üretimi için geçerlidir:

- C#

- Visual Basic

**Ne:** , Kopya ve yapıştırılan kod için gerekli içeri aktarmaları veya [kullanım yönergelerini](/dotnet/csharp/language-reference/keywords/using-directive) hemen eklemenizi sağlar.

**Ne zaman:** Projenizde veya diğer kaynaklardaki farklı yerlerden kod kopyalamak ve yeni koda yapıştırmak yaygın bir uygulamadır. Bu hızlı eylem, kopya ve yapıştırılan kod için eksik içeri aktarmalar yönergelerini bulur ve sonra bunları eklemenizi ister. Bu kod düzeltilme Ayrıca projeden projeye başvurular da eklenebilir.

**Neden:** Hızlı eylem gerekli içeri aktarmaları otomatik olarak eklediğinden, `using` kodunuzun ihtiyaç duyduğu yönergeleri el ile kopyalamanız gerekmez.

## <a name="add-missing-usings-refactoring"></a>Eksik using 'leri yeniden düzenleme Ekle

1. Kodu bir dosyadan kopyalayın ve gerekli yönergeleri eklemeden yeni bir dosyaya yapıştırın `using` . Ortaya çıkan hata, eksik yönergeleri ekleyen bir kod düzeltmesine eşlik eder `using` .

    > [!NOTE]
    > Bu öneriyi, **araçlar > seçenekler > metin düzenleyicisi > yönergeleri kullanarak C# > gelişmiş >** etkinleştirmeniz gerekir.

2. CTRL + seçeneğini belirleyin. **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü açmak için.

    ![Using deyimleri oluşturma](media/generate-using-codefix.png)

3. Eksik **başvuruyu \<your reference\> eklemek için using** öğesini seçin.

    ![Kullanımlar sonucu oluştur](media/generate-using-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
