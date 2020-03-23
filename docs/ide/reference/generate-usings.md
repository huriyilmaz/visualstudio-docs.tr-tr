---
title: Using deyimleri oluşturma
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
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094312"
---
# <a name="add-missing-usings-in-visual-studio"></a>Visual Studio'da eksik kullanmalar ekleme

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Kopyala ve yapıştırılmış kod için gerekli içeri aktarımları veya [yönergeleri hemen](/dotnet/csharp/language-reference/keywords/using-directive) eklemenizi sağlar.

**Ne zaman:** Projenizdeki veya diğer kaynaklardaki farklı yerlerden kod kopyalayıp yeni koda yapıştırmak yaygın bir uygulamadır. Bu Hızlı Eylem, kopyala ve yapıştırılmış kod için eksik içeri alma yönergelerini bulur ve sonra bunları eklemenizi ister. Bu kod düzeltmesi, projeden projeye başvurular da ekleyebilir.

**Neden:** Hızlı Eylem gerekli içeri aktarımları otomatik olarak eklediklerinden, `using` kodunuzu ihtiyaç duyduğu yönergeleri el ile kopyalamanız gerekmez.

## <a name="add-missing-usings-refactoring"></a>Eksik kullanır refactoring ekleme

1. Kodu bir dosyadan kopyalayın ve gerekli `using` yönergeleri dahil etmeden yenibir dosyaya yapıştırın. Ortaya çıkan hata, eksik `using` yönergeleri ekleyen bir kod düzeltmesi ile birlikte verilir.

    > [!NOTE]
    > Bu öneriyi Araçlar **> Seçenekleri > Metin Düzenleyicisi > C# > Gelişmiş > Kullanma Yönergeleri'nde**etkinleştirmeniz gerekir.

2. Ctrl+'yı seçin. **Hızlı Eylemler ve Refactorings** menüsünü açmak için.

    ![Using deyimleri oluşturma](media/generate-using-codefix.png)

3. **Başvurunuzu \<\>kullanarak** seçin ; eksik başvuruyu ekleyin.

    ![Kullanarak sonuç oluşturma](media/generate-using-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
