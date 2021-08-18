---
title: '3. Adım: Form özelliklerinizi ayarlama'
description: Form biçiminizi değiştirmek için Özellikler penceresi kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c7f9d8153a27807c394f2d6b3f383365e4fbb65d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132047"
---
# <a name="step-3-set-your-form-properties"></a>3. Adım: Form özelliklerinizi ayarlama

Ardından Özellikler penceresini **kullanarak** form biçiminizi değiştireceksiniz.

## <a name="how-to-set-your-form-properties"></a>Form özelliklerinizi ayarlama

1. Windows **Forms Designer'a Windows olun.** Tümleşik Visual Studio ortamında (IDE) **Form1.cs [Tasarım]** sekmesini (veya **form1.vb [Tasarım]** sekmesini) Visual Basic.

1. **Form1** formunun içinde herhangi bir yerde seçim yapmak için form1'i seçin. Şimdi **formun** özelliklerini gösteren Özellikler penceresine bakın. Formlar çeşitli özelliklere sahiptir. Örneğin, ön plan ve arka plan rengini, formun en üstünde görünen başlık metnini, formun boyutunu ve diğer özellikleri ayarlayın.

   > [!NOTE]
   > Özellikler **penceresi** görünmüyorsa, araç çubuğunda hata ayıklamayı  durdur düğmesini seçerek veya pencereyi kapatarak uygulamayı durdurun. Uygulama durdurulursa ve Özellikler penceresini hala  görmüyorsanız, menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

1. Form seçildikten sonra Özellikler **penceresinde Text** **özelliğini** bulun. Listenin nasıl sıralanmış olduğunu bağlı olarak, aşağı kaydırmak için ihtiyacınız olabilir. **Metin'i** seçin, **Resim Görüntüleyici yazın** ve enter tarak **seçin.**  Formunuz artık başlık çubuğunda **Resim** Görüntüleyici metnine sahip olmalı ve **Özellikler** penceresi aşağıdaki ekran görüntüsüne benzer şekilde görünür.

    ![Özellik penceresi](../ide/media/express_edittextproperty.png)<br>
   ***Özellikler** _ _window*

   > [!NOTE]
   > Özellikler Kategorilere Ayrılmış veya **Alfabetik görünüme** **göre sıralanır.** Özellikler penceresindeki düğmeleri kullanarak bu iki görünüm arasında **geçişebilirsiniz.** Bu öğreticide, alfabetik görünüm aracılığıyla özellikleri **bulmak daha kolaydır.**

1. Geri dön Form **Windows'a .** Formun sağ alt köşesindeki küçük beyaz kare olan ve aşağıdaki gibi görünen sağ alt tutamacı seçin.

    ![Tutamacı sürükleme](../ide/media/express_bottomrt_drag.png)<br>
   *Tutamacı sürükleme*

    Formu daha geniş ve biraz daha uzun olacak şekilde yeniden boyutlandırmak için tutamacı sürükleyin.

1. Özellikler **penceresine bakın** ve Size özelliğinin **değiştiklerini** görebilirsiniz. Formu **her** yeniden boyutlandırarak Boyut özelliği değişir. Formun tutamacı sürükleyerek yaklaşık **550, 350** (tam olması gerekmemektedir) bir form boyutuna yeniden boyutlandırmayı deneyin. Bu, bu projenin iyi çalışmasına neden olur. Alternatif olarak, değerleri doğrudan Boyut özelliğine **girebilirsiniz ve** ardından **Enter tuşuna basın.**

1. Uygulamayı yeniden çalıştırın. Uygulama çalıştırmak için aşağıdaki yöntemlerden herhangi birini kullanabileceğinizi unutmayın.

   - **F5 anahtarını** seçin.

   - Menü çubuğunda Hata Ayıklama Hata **AyıklamaYı**  >  **Başlat'ı seçin.**

   - Araç çubuğunda, aşağıdaki **gibi görünen** Hata Ayıklamayı Başlat düğmesini seçin.

      ![Hata Ayıklamayı Başlat araç çubuğu düğmesi](../ide/media/express_icondebug.png)<br>
     ***Hata Ayıklamayı Başlat** _ _toolbar düğmesi*

     Daha önce olduğu gibi, IDE uygulamanızı derlemek ve çalıştırır ve bir pencere görünür.

1. Bir sonraki adıma gitmeden önce, IDE çalışırken uygulamanızı değiştirmenize izin vermey olduğundan, uygulamayı durdurun. Uygulamayı durdurmak için aşağıdaki yöntemlerden herhangi birini kullanabileceğinizi unutmayın.

   - Araç çubuğunda Hata Ayıklamayı **Durdur düğmesini** seçin.

   - Menü çubuğunda Hata Ayıklama Hata **Ayıklamayı**  >  **Durdur'u seçin.**

   - Klavyenizi kullanın ve **Shift** + **F5 tuşuna basın.**

   - Resim **Görüntüleyicisi** penceresinin üst köşesindeki X **düğmesini** seçin.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için **[bkz. 4. Adım: Formlarınızı TableLayoutPanel denetimiyle oluşturma.](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**

* Önceki öğretici adımına dönmek için [bkz. 2. Adım: Resim görüntüleyicisi uygulamasını çalıştırma.](../ide/step-2-run-your-program.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
