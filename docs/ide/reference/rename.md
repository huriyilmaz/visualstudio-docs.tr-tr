---
title: Yeniden düzenleme yeniden Düzenle
description: Alanlar, yerel değişkenler, Yöntemler, ad alanları, Özellikler ve türler gibi kod sembolleri için tanımlayıcıları yeniden adlandırmak üzere yeniden Düzenle özelliğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2e3d4d5d0abc335cfb857e5a4de9c5189a1ca5cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958108"
---
# <a name="rename-a-code-symbol-refactoring"></a>Kod sembolünü yeniden düzenlemeyi yeniden adlandırma

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Alanlar, yerel değişkenler, Yöntemler, ad alanları, Özellikler ve türler gibi kod sembolleri için tanımlayıcıları yeniden adlandırmanızı sağlar.

**Ne zaman:** Tüm örnekleri bulmak zorunda kalmadan bir şeyi güvenle yeniden adlandırmak ve yeni adı kopyalayıp yapıştırmak istiyorsunuz.

**Neden:** Yeni adı bir projenin tamamına kopyalamak ve yapıştırmak muhtemelen hatalara neden olabilir. Bu yeniden düzenleme aracı yeniden adlandırma eylemini doğru bir şekilde gerçekleştirir.

## <a name="how-to"></a>Nasıl yapılır

1. Yeniden adlandırılacak öğenin içine metin imlecini vurgula veya Yerleştir:

   - C#:

       ![Vurgulanan kod-C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/rename-highlight-vb.png)

2. Ardından, klavyenizi veya farenizi aşağıdaki şekilde kullanın:

   - **Klavye**
      - **CTRL + r**, ardından **CTRL + r** tuşlarına basın. (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
   - **Fare**
      - **Düzenle > yeniden düzenle > yeniden adlandır**' ı seçin.
      - Koda sağ tıklayıp **Yeniden Adlandır**' ı seçin.

3. Yeni adı yazarak öğeyi yeniden adlandırın.

   - C#:

      ![Animasyonu yeniden adlandırma-C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Yeniden adlandır-VB](media/rename-rename-vb.png)

   > [!TIP]
   > Ayrıca, bu yeni adı kullanmak için açıklamaları ve diğer dizeleri güncelleştirebilir ve Düzenleyicinizde, **Yeniden Adlandır** ' ın sağ üst köşesinde görünen onay kutularını kullanarak [değişiklikleri gözden](../../ide/preview-changes.md) aktarabilirsiniz.

4. Değişikliğin ne kadar memnunsanız **Uygula** düğmesini seçin veya **ENTER** tuşuna basın ve değişiklikler uygulanır.

## <a name="remarks"></a>Açıklamalar

- Visual Studio 2019 sürüm 16,3 ' den başlayarak, içindeki dosyanın adıyla eşleşen bir türü yeniden adlandırdığınızda, dosyayı aynı anda yeniden adlandırmanızı sağlayan bir onay kutusu görüntülenir. Bu seçenek, bir sınıfı, arabirimi veya numaralandırmayı yeniden adlandırdığınızda görüntülenir. Bu seçenek, birden çok tanım içeren kısmi türler için desteklenmez.

   ![Animasyonu dosyayla yeniden adlandırma-C #](media/rename-with-file-animated-cs.gif)

- Bir çakışmaya neden olabilecek zaten var olan bir ad kullanırsanız, **yeniden adlandırma** kutusu sizi uyarır.

   ![Yeniden adlandırma çakışması](media/rename-conflict-cs.png)

- Bir sembolü yeniden adlandırmaya yönelik başka bir yol da düzenleyicide adını değiştirkullanmaktır. Ardından, imleç sembol adında, **CTRL** tuşuna basın + **.** ya da görüntülenen ampul simgesi menüsünü genişletin ve **Yeniden Adlandır \<old name> \<new name>**' ı seçin.

   ![Düzenleyicide yeniden adlandırma](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
