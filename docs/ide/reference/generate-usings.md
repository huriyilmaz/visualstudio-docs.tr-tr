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
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544547"
---
# <a name="add-missing-usings-in-visual-studio"></a>Visual Studio 'da eksik using 'leri ekleme

Bu kod oluşturma için geçerlidir:

- C#

**Ne:** , Kopya ve yapıştırılan kod için gerekli içeri aktarmaları veya [kullanım yönergelerini](/dotnet/csharp/language-reference/keywords/using-directive) hemen eklemenizi sağlar.

**Ne zaman:** Projenizde veya diğer kaynaklardaki farklı yerlerden kod kopyalamak ve yeni koda yapıştırmak yaygın bir uygulamadır. Bu hızlı eylem, kopya ve yapıştırılan kod için eksik içeri aktarmalar yönergelerini bulur ve sonra bunları eklemenizi ister. Bu kod düzeltilme Ayrıca projeden projeye başvurular da eklenebilir.

**Neden:** Hızlı eylem gerekli içeri aktarmaları otomatik olarak eklediğinden, kodunuzun ihtiyaç duyduğu `using` yönergelerini el ile kopyalamanız gerekmez.

## <a name="add-missing-usings-refactoring"></a>Eksik using 'leri yeniden düzenleme Ekle

1. Kodu bir dosyadan kopyalayın ve gerekli `using` yönergeleri dahil etmeden yeni bir dosyaya yapıştırın. Ortaya çıkan hata, eksik `using` yönergelerini ekleyen bir kod düzeltmesine eşlik eder.

    > [!NOTE]
    > **Araçlar > seçenekler > metin düzenleyicisi > C# yönergeleri kullanarak Gelişmiş > >** bu öneriyi etkinleştirmeniz gerekir.

2. CTRL + seçeneğini belirleyin. **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü açmak için.

    ![Using deyimleri oluşturma](media/generate-using-codefix.png)

3. Eksik başvuruyu eklemek için **\>başvurunuz \<using** seçeneğini belirleyin.

    ![Kullanımlar sonucu oluştur](media/generate-using-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
