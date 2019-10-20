---
title: Yeniden düzenleme yeniden Düzenle
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2991227b3c8d742da360465e6c506e7123259e2c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655616"
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

       ![Vurgulanan kod-C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/rename-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **CTRL + r**, ardından **CTRL + r**tuşlarına basın. (Klavye kısayolunuzun seçtiğiniz profile göre farklı olabileceğini unutmayın.)
   - **Tığında**
      - **Düzenle > yeniden düzenle > yeniden adlandır**' ı seçin.
      - Koda sağ tıklayıp **Yeniden Adlandır**' ı seçin.

3. Yeni adı yazarak öğeyi yeniden adlandırın.

   - C#:

      ![Animasyonu yeniden adlandır-C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Yeniden adlandır-VB](media/rename-rename-vb.png)

   > [!TIP]
   > Ayrıca, bu yeni adı kullanmak için açıklamaları ve diğer dizeleri güncelleştirebilir ve Düzenleyicinizde, **Yeniden Adlandır** ' ın sağ üst köşesinde görünen onay kutularını kullanarak [değişiklikleri gözden](../../ide/preview-changes.md) aktarabilirsiniz.

4. Değişikliğin ne kadar memnunsanız **Uygula** düğmesini seçin veya **ENTER** tuşuna basın ve değişiklikler uygulanır.

## <a name="remarks"></a>Açıklamalar

- Visual Studio 2019 sürüm 16,3 ' den başlayarak, içindeki dosyanın adıyla eşleşen bir türü yeniden adlandırdığınızda, dosyayı aynı anda yeniden adlandırmanızı sağlayan bir onay kutusu görüntülenir. Bu seçenek, bir sınıfı, arabirimi veya numaralandırmayı yeniden adlandırdığınızda görüntülenir. Bu seçenek, birden çok tanım içeren kısmi türler için desteklenmez.

   ![Animasyonu dosyayla yeniden adlandırma-C#](media/rename-with-file-animated-cs.gif)

- Bir çakışmaya neden olabilecek zaten var olan bir ad kullanırsanız, **yeniden adlandırma** kutusu sizi uyarır.

   ![Yeniden adlandırma çakışması](media/rename-conflict-cs.png)

- Bir sembolü yeniden adlandırmaya yönelik başka bir yol da düzenleyicide adını değiştirkullanmaktır. Sonra, sembol adındaki imleç ile **Ctrl** + ' a basın **.** ya da görünen ampul simgesi menüsünü genişlettikten sonra **\<old ad > yeniden adlandır**' ı seçerek > \<new.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
