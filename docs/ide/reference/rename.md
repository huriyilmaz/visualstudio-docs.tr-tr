---
title: Yeniden Adlandır yeniden düzenleyin
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565467"
---
# <a name="rename-a-code-symbol-refactoring"></a>Bir kod sembol yeniden düzenlemeyi yeniden adlandırma

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** alanlar, yerel değişkenler, yöntemleri, ad alanları, özellikler ve türler gibi kod simgeleri tanımlayıcıları yeniden adlandırın olanak tanır.

**Ne zaman:** güvenli bir şekilde bir şey tüm örneklerini bulun ve yeni adı kopyala/yapıştır gerekmeden yeniden adlandırmak istiyor.

**Neden:** kopyalayıp yeni bir ad, bir projenin tamamı yapıştırarak musunuz büyük olasılıkla hatalara neden. Bu yeniden düzenleme aracı doğru yeniden adlandırma eylemi gerçekleştirir.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Vurgulama veya yeniden adlandırılacak öğe metin imleci yerleştirin:

   - C#:

       ![Vurgulanan kodu:C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu - Visual Basic](media/rename-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl + R**, ardından **Ctrl + R**. (Bağlı olarak hangi profilinde seçtiğiniz klavye kısayolu farklı olabileceğini unutmayın.)
   - **Fare**
      - Seçin **Düzenle > yeniden düzenleyin > Yeniden Adlandır**.
      - Kod sağ tıklayıp **Yeniden Adlandır**.

3. Yeni bir ad yazarak öğeyi yeniden adlandırın.

   - C#:

      ![Animasyon yeniden adlandır-C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Rename - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Ayrıca açıklamalar ve diğer dizeleri bu yeni adı kullanacak şekilde güncelleştirebilirsiniz yanı [değişiklikleri Önizleme](../../ide/preview-changes.md) önce kaydetme, içinde onay kutularını kullanarak **Yeniden Adlandır** en üstünde açılan kutusunda düzenleyiciniz sağında.

4. Değişiklik ile tamamladığınızda seçin **Uygula** düğme veya basın **Enter** ve değişiklikler uygulanır.

## <a name="remarks"></a>Açıklamalar

- Visual Studio 2019 sürüm 16,3 ' den başlayarak, içindeki dosyanın adıyla eşleşen bir türü yeniden adlandırdığınızda, dosyayı aynı anda yeniden adlandırmanızı sağlayan bir onay kutusu görüntülenir. Bu seçenek, bir sınıfı, arabirimi veya numaralandırmayı yeniden adlandırdığınızda görüntülenir. Bu seçenek, birden çok tanım içeren kısmi türler için desteklenmez.

   ![Animasyonu dosyayla yeniden adlandırma-C#](media/rename-with-file-animated-cs.gif)

- Bir çakışma neden zaten var olan bir ad kullanırsanız **Yeniden Adlandır** kutusunun sizi uyaracaktır.

   ![Yeniden adlandırma çakışması](media/rename-conflict-cs.png)

- Bir sembolü yeniden adlandırmaya yönelik başka bir yol da düzenleyicide adını değiştirkullanmaktır. Sonra, sembol adındaki imleç ile **Ctrl**+' a basın **.** ya da görüntülenen ampul simgesi menüsünü genişletin ve **Yeni ad > \<\<eski adı > yeniden adlandır**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
