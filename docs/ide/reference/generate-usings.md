---
title: Using deyimleri oluşturma
description: Kopyalayıp yapıştıran kod için gerekli içeri aktarmaları veya kullanma yönergelerini hemen eklemek için Hızlı Eylemler ve Yeniden Düzenlemeler menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: b3eaa7d035c95ba3ff2eeccf37968cb858ddcf02
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726873"
---
# <a name="add-missing-usings-in-visual-studio"></a>Visual Studio'de eksik kullanmalar ekleme

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Kopyalayıp yapıştıran kod için gerekli içeri [aktarmaları veya](/dotnet/csharp/language-reference/keywords/using-directive) kullanma yönergelerini hemen eklemenize olanak sağlar.

**Ne zaman:** Projenizin veya diğer kaynakların farklı yerlerinden kod kopyalayıp yeni koda yapıştırmak yaygın bir uygulamadır. Bu Hızlı Eylem, kopyalayıp yapıştıran kod için eksik içeri aktarma yönergelerini bulur ve ardından bunları eklemenizi istenir. Bu kod düzeltmesi, projeden projeye başvurular da ekleyebilir.

**Neden:** Hızlı Eylem gerekli içeri aktarmaları otomatik olarak ekleyene kadar, kodunuzun ihtiyacı olan `using` yönergeleri el ile kopyalamanız gerekmez.

## <a name="add-missing-usings-refactoring"></a>Eksik usings yeniden düzenlemesi ekleme

1. Bir dosyadan kod kopyalayın ve gerekli yönergeleri dahil etmeden yenisine `using` yapıştırın. Sonuçta ortaya çıkan hataya eksik yönergeleri ekleyen bir kod `using` düzeltmesi eşlik ediyor.

    > [!NOTE]
    > Bu öneriyi Araçlar > Seçenekleri > C# > Gelişmiş > Yönergeleri > **etkinleştirmeniz gerekir.**

2. Ctrl+'yi seçin. hızlı eylemler **ve yeniden düzenleme menüsünü** açın.

    ![Using deyimleri oluşturma](media/generate-using-codefix.png)

3. Eksik **başvuru \<your reference\> eklemek** için kullanarak öğesini seçin.

    ![Usings sonucu oluşturma](media/generate-using-result.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
