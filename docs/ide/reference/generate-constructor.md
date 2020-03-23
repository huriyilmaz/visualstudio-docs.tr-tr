---
title: Bir oluşturucu hızlı eylem oluşturma
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c8259841af4511bd782bca1be222353634638f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301813"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Visual Studio'da bir oluşturucu oluşturun

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir sınıftaki yeni bir oluşturucu için kodu hemen oluşturmanıza olanak tanır.

**Ne zaman:** Yeni bir oluşturucu tanıtın ve bunu otomatik olarak düzgün bir şekilde bildirmek istiyorsunuz veya varolan bir oluşturucuyuz değiştirin.

**Neden:** Kullanmadan önce oluşturucuyu bildirebilirsiniz, ancak bu özellik, uygun parametrelerle otomatik olarak oluşturur. Ayrıca, varolan bir oluşturucuyu değiştirmek, bu özelliği otomatik olarak güncelleştirmek için kullanmadığınız sürece tüm çağrı sitelerini güncelleştirmeyi gerektirir.

**Nasıl:** Bir oluşturucu oluşturmanın birkaç yolu vardır:

- [Oluşturucu oluşturma ve üye seçme](#pick)
- [Seçili alanlardan oluşturucu oluşturma](#selection)
- [Yeni kullanımdan yapıcı oluşturma](#usage)
- [Varolan oluşturucuya parametre ekleme](#addparameter)
- [Bir oluşturucu parametreden alan/özellik oluşturma ve başlatma](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a>Oluşturucu oluşturma ve üye seçin (yalnızca C# )

1. İmlecinizi sınıftaki herhangi bir boş satıra yerleştirin:

   ![Boş satırda imleç](media/constructor1-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - &nbsp; ![Tornavida](media/screwdriver.png) metin imleci sınıftaki boş satırda zaten duruyorsa, sol kenar boşluğunda görünen simge.

   ![Oluşturucu önizleme oluşturma](media/constructor1-preview-cs.png)

1. Açılan menüden **oluşturucu oluşturucu** oluştur'u oluştur'u seçin.

   **Üyeleri Seç** iletişim kutusu açılır.

1. Oluşturucu parametreler olarak eklemek istediğiniz üyeleri seçin. Yukarı ve aşağı okları kullanarak sipariş edebilirsiniz. **Tamam'ı**seçin.

   ![Üyeler iletişim kutusunu seçme](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Oluşturucu parametreleriniz için otomatik olarak null denetimleri oluşturmak için **Null checks onay** kutusunu ekle onay kutusunu işaretleyebilirsiniz.

   Konstrüktör belirtilen parametrelerle oluşturulur.

   ![Oluşturucu sonuç oluşturma](media/constructor1-result-cs.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a>Seçili alanlardan yapıcı oluşturma (yalnızca C# )

1. Oluşturulan oluşturucunuzda olmasını istediğiniz üyeleri vurgulayın:

   ![Üyeleri vurgulayın](media/constructor2-highlight-cs.png)

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - &nbsp; ![Tornavida](media/screwdriver.png) metin imleci seçimle zaten çizgideyse, sol kenar boşluğunda görünen simge.

      ![Constructor önizlemesi oluştur](media/constructor2-preview-cs.png)

1. Açılan menüden **oluşturucu 'TypeName(...)'** oluşturun'u seçin.

   Kurucu seçili parametrelerle oluşturulur.

   ![Yapıcı sonucu oluşturma](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a>Yeni kullanımdan yapıcı oluşturma (C# ve Visual Basic)

1. İmlecinizi kırmızı bir dalganın olduğu çizgiye yerleştirin. Kırmızı dalgalı henüz var olmayan bir yapıcıya yapılan çağrıyı gösterir.

   - C#:

       ![Vurgulanan kod C #](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod VB](media/constructor-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

      ![Oluşturucu önizleme oluşturma](media/constructor-preview-cs.png)

3. Açılan menüden **'*TypeName*' içinde oluşturucu oluştur'u** seçin.

   > [!TIP]
   > Seçiminizi yapmadan önce yapılacak [tüm değişiklikleri görmek için](../../ide/preview-changes.md) önizleme penceresinin altındaki Önizleme **değişiklikleri** bağlantısını kullanın.

   Yapıcı, kullanımından kaynaklanan parametrelerle oluşturulur.

   - C#:

       ![Yöntem sonucu c oluşturma #](media/constructor-result-cs.png)

   - Visual Basic:

       ![Yöntem sonucu vb oluşturma](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a>Varolan oluşturucuya parametre ekleme (yalnızca C#

1. Varolan bir kurucu çağrısına bir parametre ekleyin.

2. İmlecinizi, henüz var olmayan bir yapıcı kullandığınızı belirten kırmızı bir dalgalı çizgiye yerleştirin.

    ![Oluşturucu vurgu oluşturma](media/constructor4-highlight-cs.png)

3. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - Kırmızı dalgalı üzerinde hover ve tıklayın ![hata ampul](media/error-bulb.png) görünen simge.
      - &nbsp; ![hata ampul](media/error-bulb.png) metin imleci kırmızı dalgalı çizgide yse sol kenar boşluğunda görünen simge.

      ![Oluşturucu önizleme oluşturma](media/constructor4-preview-cs.png)

4. Açılan menüden **'TypeName(...)' parametresi ekle'yi** seçin.

   Parametre, kullanımından çıkarılan türü yle birlikte oluşturucuya eklenir.

   ![Oluşturucu sonuç oluşturma](media/constructor4-result-cs.png)

Varolan bir yönteme bir parametre de ekleyebilirsiniz. Daha fazla bilgi için [bkz.](add-parameter.md)

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a>Bir oluşturucu parametreden (yalnızca C#) bir alan veya özellik oluşturma ve başlatma

1. Varolan bir oluşturucu bulun ve bir parametre ekleyin:

   ![Oluşturucu vurgu oluşturma](media/constructor5-highlight-cs.png)

1. İmlecinizi yeni eklenen parametrenin içine yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
   - **Fare**
      - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.
      - &nbsp; ![Tornavida](media/screwdriver.png) metin imleci eklenen parametreyle zaten çizgideyse sol kenar boşluğunda görünen simge.

   ![Oluşturucu önizleme oluşturma](media/constructor5-preview-cs.png)

1. **Özellik Oluştur'u seçin ve başlatma** yı veya açılan menüden alanı oluştur ve **başlatma** yı seçin.

   Alan veya özellik beyan edilir ve türlerinize uyacak şekilde otomatik olarak adlandırılır. Oluşturucu gövdedeki alanı veya özelliği başlatmaya bir kod satırı da eklenir.

   ![Oluşturucu sonuç oluşturma](media/constructor5-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri önizleme](../../ide/preview-changes.md)
