---
title: Oluşturucu hızlı eylemi oluşturma
description: Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanarak bir sınıfta yeni bir oluşturucu için kodu hemen oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: a74b9d65db028646a6aca28b2c3bbb738e51ae18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151710"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Visual Studio'de oluşturucu oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıfta yeni bir oluşturucu için kodu hemen oluşturmana olanak sağlar.

**Ne zaman:** Yeni bir oluşturucu tanıtmış ve bunu otomatik olarak düzgün bir şekilde bildirmiş veya var olan bir oluşturucuda değişiklik yapmak istiyorsanız.

**Neden:** Oluşturucusu kullanmadan önce bildirebilirsiniz, ancak bu özellik bunu, uygun parametrelerle otomatik olarak oluşturur. Ayrıca, mevcut bir oluşturucuda değişiklik yapmak için, bu özelliği otomatik olarak güncelleştirmek için kullanmadıkça tüm çağrılarını güncelleştirmek gerekir.

**Nasıl:** Oluşturucu oluşturmanın birkaç yolu vardır:

- [Oluşturucu oluşturma ve üyeleri seçme](#pick)
- [Özelliklerle oluşturucu oluşturma](#with)
- [Seçili alanlardan oluşturucu oluşturma](#selection)
- [Yeni kullanımdan oluşturucu oluşturma](#usage)
- [Mevcut oluşturucuya parametre ekleme](#addparameter)
- [Oluşturucu parametresinden alan/özellik oluşturma ve başlatma](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a> Oluşturucu oluşturma ve üyeleri seçme (yalnızca C# )

1. İmlecinizi bir sınıftaki boş bir satıra yerleştirin:

   ![Boş satırda imleç](media/constructor1-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Metin :::image type="icon" source="media/screwdriver.png"::: imleci sınıftaki boş satırda zaten varsa sol kenar boşluğunda görünen simgeye tıklayın.

   ![Oluşturucu oluştur seçeneğinin ekran görüntüsü.](media/constructor1-preview-cs.png)

1. Açılan **menüden** Oluşturucu oluştur'a tıklayın.

   Üye **seç** iletişim kutusu açılır.

1. Oluşturucu parametreleri olarak eklemek istediğiniz üyeleri seçme. Yukarı ve aşağı okları kullanarak bunları sıraebilirsiniz. **Tamam'ı seçin.**

   ![Üye seç iletişim kutusu](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Oluşturucu parametreleriniz için **otomatik olarak null** denetimleri oluşturmak için Null denetimleri ekle onay kutusunu işaretleyin.

   Oluşturucu belirtilen parametrelerle oluşturulur.

   ![Oluşturucu'da belirtilen parametrelerle oluşturulmuş olduğunu gösteren ekran görüntüsü.](media/constructor1-result-cs.png)

## <a name="generate-constructor-with-properties-c-only"></a><a id = "with"></a> Özelliklerle oluşturucu oluşturma (yalnızca C# )

1. İmlecinizi örneğin üzerine yerleştirin.

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.

3. içinde **Oluşturucu `<QualifiedName>` oluştur'a (özelliklerle) tıklayın.**

   ![Anahtarda oluşturucu oluştur (özelliklerle) seçeneğinin ekran görüntüsü.](media/generate-constructor-with-properties.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a> Seçili alanlardan oluşturucu oluşturma (yalnızca C# )

1. Oluşturulan oluşturucuda olmasını istediğiniz üyeleri vurgulayın:

   ![Üyeleri vurgulama](media/constructor2-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Metin :::image type="icon" source="media/screwdriver.png"::: imleci seçimin olduğu satırda zaten varsa sol kenar boşluğunda görünen simgeye tıklayın.

      ![Oluşturucu Kişi dizesi dizesi oluştur seçeneğinin ekran görüntüsü.](media/constructor2-preview-cs.png)

1. Açılan **menüden Oluşturucu oluştur 'TypeName(...)'** öğesini seçin.

   Oluşturucu seçilen parametrelerle oluşturulur.

   ![Oluşturucu'da seçili parametrelerle oluşturulmuş olduğunu gösteren ekran görüntüsü.](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a>Yeni kullanımdan oluşturucu oluşturma (C# ve Visual Basic)

1. İmlecinizi kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz. Kırmızı geçiş, henüz mevcut olmayan bir oluşturucuya yapılan çağrıyı gösterir.

   - C#:

       ![Vurgulanan kod C #](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/constructor-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve görüntülenen :::image type="icon" source="media/error-bulb.png"::: simgeye tıklayın.
      - Metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar :::image type="icon" source="media/error-bulb.png"::: boşluğunda görünen simgeye tıklayın.

      ![Kişi olarak oluşturucu oluştur seçeneğinin ekran görüntüsü.](media/constructor-preview-cs.png)

3. Açılan **menüden *'TypeName*' içinde** oluşturucu oluştur'ı seçin.

   > [!TIP]
   > Seçiminizi **yapmadan** önce yapılacak tüm değişiklikleri görmek için önizleme penceresinin [altındaki](../../ide/preview-changes.md) Değişiklikleri önizle bağlantısını kullanın.

   Oluşturucu, kullanımından alınan parametrelerle oluşturulur.

   - C#:

       ![Yöntem sonucu oluşturma C #](media/constructor-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu oluşturma VB](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a> Mevcut oluşturucuya parametre ekleme (yalnızca C# )

1. Mevcut oluşturucu çağrısına bir parametre ekleyin.

2. İmlecinizi henüz mevcut olmayan bir oluşturucusu kullandığınızı gösteren kırmızı bir geçişin bulunduğu satıra yerleştirebilirsiniz.

    ![Kırmızı bir geçişin bulunduğu satırı gösteren ekran görüntüsü.](media/constructor4-highlight-cs.png)

3. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Kırmızı çizginin üzerine gelin ve görüntülenen :::image type="icon" source="media/error-bulb.png"::: simgeye tıklayın.
      - Metin imleci kırmızı çizgiyle çizgi üzerinde zaten varsa sol kenar :::image type="icon" source="media/error-bulb.png"::: boşluğunda görünen simgeye tıklayın.

      ![Kişi dizesi dizesine parametre ekle seçeneğinin ekran görüntüsü.](media/constructor4-preview-cs.png)

4. Açılan **menüden Parametre ekle'yi 'TypeName(...)'** olarak seçin.

   parametresi oluşturucuya eklenir ve türü kullanımından gelir.

   ![Parametresinin oluşturucuya eklenmiştir ve türü kullanımdan alınarak ekran görüntüsü.](media/constructor4-result-cs.png)

Ayrıca var olan bir yönteme parametre eklemek de gerekir. Daha fazla bilgi için [bkz. Yöntemine parametre ekleme.](add-parameter.md)

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a> Oluşturucu parametresinden bir alan veya özellik oluşturma ve başlatma (yalnızca C# )

1. Var olan bir oluşturucu bulun ve bir parametre ekleyin:

   ![Mevcut oluşturucusu gösteren ekran görüntüsü.](media/constructor5-highlight-cs.png)

1. İmlecinizi yeni eklenen parametrenin içine yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
   - **Fare**
      - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.
      - Metin :::image type="icon" source="media/screwdriver.png"::: imleci eklenen parametreyle satırda zaten varsa sol kenar boşluğunda görünen simgeye tıklayın.

   ![Age özelliğini oluşturma ve başlatma seçeneğinin ekran görüntüsü.](media/constructor5-preview-cs.png)

1. Özellik **oluştur ve başlat'ı** **veya açılan menüden** Alan oluştur ve başlat'ı seçin.

   Alan veya özellik, türlerinize uygun olarak bildirilir ve otomatik olarak adlandırılmıştır. Oluşturucu gövdesinde alanı veya özelliği başlatmak için bir kod satırı da eklenir.

   ![Alan veya özelliğin, türlerinize uygun olarak bildir ve otomatik olarak adlandırılmış olduğunu gösteren ekran görüntüsü.](media/constructor5-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri önizleme](../../ide/preview-changes.md)
