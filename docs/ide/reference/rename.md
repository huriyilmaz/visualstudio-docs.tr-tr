---
title: Yeniden düzenleme
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565467"
---
# <a name="rename-a-code-symbol-refactoring"></a>Kod simgesi refactoring'i yeniden adlandırma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Alanlar, yerel değişkenler, yöntemler, ad alanları, özellikler ve türler gibi kod sembolleri için tanımlayıcıları yeniden adlandırmanıza olanak tanır.

**Ne zaman:** Tüm örnekleri bulmak zorunda kalmadan bir şeyi güvenli bir şekilde yeniden adlandırmak ve yeni adı kopyalamak/yapıştırmak istiyorsunuz.

**Neden:** Yeni adı tüm projeboyunca kopyalama ve yapıştırma büyük olasılıkla hatalara neden olur. Bu yeniden düzenleme aracı, yeniden adlandırma eylemini doğru bir şekilde gerçekleştirir.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini yeniden adlandırılacak öğenin içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/rename-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl+R**tuşuna basın, sonra **Ctrl+R**tuşuna basın. (Klavye kısayol'unuzun seçtiğiniz profile bağlı olarak farklı olabileceğini unutmayın.)
   - **Fare**
      - **Yeniden Adlandır> düzenleme >yi**seçin.
      - Kodu sağ tıklatın ve **Yeniden Adlandır'ı**seçin.

3. Öğeyi yalnızca yeni adı yazarak yeniden adlandırın.

   - C#:

      ![Animasyonu yeniden adlandır - C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Yeniden Adlandırma - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Ayrıca, düzenleyicinizin sağ üst kısmında görünen **Yeniden Adla** kutusundaki onay kutularını kullanarak, bu yeni adı kullanmak için yorumları ve diğer dizeleri güncelleştirebilir ve kaydetmeden önce [değişiklikleri önizleyebilirsiniz.](../../ide/preview-changes.md)

4. Değişiklikten memnun olduğunuzda, **Uygula** düğmesini seçin veya **Enter** tuşuna bastığında değişiklikler tamamlanın.

## <a name="remarks"></a>Açıklamalar

- Visual Studio 2019 sürüm 16.3'ten başlayarak, içinde olduğu dosyanın adıyla eşleşen bir türü yeniden adlandırdığınızda, dosyayı aynı anda yeniden adlandırmanızı sağlayan bir onay kutusu görüntülenir. Bu seçenek, bir sınıfı, arabirimi veya numaralandırmayı yeniden adlandırdığınızda görüntülenir. Bu seçenek, birden çok tanımı olan kısmi türler için desteklenmez.

   ![Dosya ile animasyonu yeniden adlandır - C #](media/rename-with-file-animated-cs.gif)

- Çakışmaya neden olacak zaten var olan bir ad kullanırsanız, **Yeniden Adlandırma** kutusu sizi uyarır.

   ![Çakışmayı Yeniden Adlandır](media/rename-conflict-cs.png)

- Bir sembolü yeniden adlandırmanın başka bir yolu da editördeki adını değiştirmektir. Daha sonra, sembol adındaimle **ctrl**+tuşuna**basın.** veya sadece görünür ampul simgesi menüsünü genişletmek ve ** \< \<yeni ad>için eski adı> yeniden adlandırmak **seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
