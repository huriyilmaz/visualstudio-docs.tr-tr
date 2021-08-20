---
title: Yeniden adlandırmayı yeniden düzenleme
description: Alanlar, yerel değişkenler, yöntemler, ad alanları, özellikler ve türler gibi kod sembollerinin tanımlayıcılarını yeniden adlandırmak için Yeniden Düzenleme Özelliğini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f71587d86bc1b4fc722abeee31a0e8e7ce8ae7cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123846"
---
# <a name="rename-a-code-symbol-refactoring"></a>Kod sembolünü yeniden düzenlemeyi yeniden adlandırma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Alanlar, yerel değişkenler, yöntemler, ad alanları, özellikler ve türler gibi kod sembolleri için tanımlayıcıları yeniden adlandırmaya olanak sağlar.

**Ne zaman:** Tüm örnekleri bulmak zorunda kalmadan bir şeyi güvenli bir şekilde yeniden adlandırmak ve yeni adı kopyalayıp yapıştırmak istiyor musunuz?

**Neden:** Yeni adı bir projenin tamamına kopyalayıp yapıştırarak hatalara neden olabilir. Bu yeniden düzenleme aracı yeniden düzenleme eylemlerini doğru bir şekilde gerçekleştirecek.

## <a name="how-to"></a>Nasıl yapılır

1. Yeniden adlandıracak öğenin içine metin imlecini vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/rename-highlight-vb.png)

2. Ardından, klavyenizi veya farenizi aşağıdaki gibi kullanın:

   - **Klavye**
      - **Ctrl+R tuşlarına** ve ardından **Ctrl+R tuşlarına basın.** (Seçtiğiniz profile bağlı olarak klavye kısayolu farklı olabilir.)
   - **Fare**
      - Yeniden **Adlandır'> Düzenle'yi > seçin.**
      - Koda sağ tıklayın ve Yeniden Adlandır'ı **seçin.**

3. Yeni adı yazarak öğeyi yeniden adlandırabilirsiniz.

   - C#:

      ![Animasyonu yeniden adlandırma - C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Yeniden Adlandırma - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Ayrıca, düzenleyicinizin sağ üst kısmında görüntülenen Yeniden Adlandır [](../../ide/preview-changes.md) kutusunda yer alan onay kutularını kullanarak,  yorumları ve diğer dizeleri bu yeni adı kullanmak için güncelleştirebilirsiniz ve kaydetmeden önce değişikliklerin önizlemesini görebilirsiniz.

4. Değişiklik sizi memnun edecekse Uygula düğmesini **seçin** veya **Enter** tuşuna basarak değişiklikler işlendi.

## <a name="remarks"></a>Açıklamalar

- Visual Studio 2019 sürüm 16.3'te başlayarak, içinde yer alan dosyanın adıyla eşleşen bir türü yeniden adlandırırsanız, dosyayı aynı anda yeniden adlandırmaya olanak sağlayan bir onay kutusu görüntülenir. Bu seçenek bir sınıfı, arabirimi veya numaralamayı yeniden adlandırarak görünür. Bu seçenek, birden çok tanımı olan kısmi türler için desteklanmaz.

   ![Animasyonu dosyayla yeniden adlandırma - C #](media/rename-with-file-animated-cs.gif)

- Çakışmaya neden olacak bir ad kullanırsanız Yeniden Adlandır **kutusu** sizi uyaracak.

   ![Yeniden Adlandırma Çakışması](media/rename-conflict-cs.png)

- Simgeyi yeniden adlandırmanın bir diğer yolu da düzenleyicide sembol adını değiştirmektir. Ardından imleci sembol adına yerleştirerek **Ctrl tuşuna** + **basın.** veya görüntülenen ampul simgesi menüsünü genişletin ve Olarak yeniden **adlandır'ı \<old name> seçin. \<new name>**

   ![Düzenleyicide yeniden adlandırma](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
