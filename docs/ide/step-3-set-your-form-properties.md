---
title: 'Adım 3: Form özelliklerinizi ayarlama'
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579859"
---
# <a name="step-3-set-your-form-properties"></a>Adım 3: Form özelliklerinizi ayarlama

Ardından, formunuzun görünüşününü değiştirmek için **Özellikler** penceresini kullanırsınız.

## <a name="how-to-set-your-form-properties"></a>Form özelliklerinizi ayarlama

1. **Windows Forms Designer'a**baktığınızdan emin olun. Visual Studio tümleşik geliştirme ortamında (IDE), **Form1.cs [Tasarım]** sekmesini (veya Visual **Basic'teki Form1.vb [Tasarım]** sekmesini seçin).

1. **Form1** formunun herhangi bir yerine seçin. Şimdi formun özelliklerini göstermesi gereken **Özellikler** penceresine bakın. Formlar çeşitli özelliklere sahiptir. Örneğin, ön plan ve arka plan rengini, formun üst kısmında görünen başlık metnini, formun boyutunu ve diğer özellikleri ayarlayabilirsiniz.

   > [!NOTE]
   > **Özellikler** penceresi görünmüyorsa, araç çubuğundaki hata **ayıklamayı durdur** düğmesini seçerek uygulamanızı durdurun veya pencereyi kapatın. Uygulama durdurulursa ve menü çubuğunda **Özellikler** penceresini hala göremiyorsanız,**Özellikler Penceresini** **Görüntüle'yi** > seçin.

1. Form seçildikten sonra **Özellikler** penceresinde **Metin** özelliğini bulun. Listenin nasıl sıralandırılına bağlı olarak, aşağı kaydırmanız gerekebilir. **Metin'i**seçin, **Resim görüntüleyicisi**yazın ve sonra **Enter'u**seçin.  Formunuz artık başlık çubuğunda **Resim Görüntüleyici** metnine sahip olmalıdır ve **Özellikler** penceresi aşağıdaki ekran görüntüsüne benzer olmalıdır.

    ![Özellik penceresi](../ide/media/express_edittextproperty.png)<br>
   ***Özellikler*** *penceresi*

   > [!NOTE]
   > Özellikler **Kategorize** veya **Alfabetik** görünümtarafından sıralanabilir. **Özellikler** penceresindeki düğmeleri kullanarak bu iki görünüm arasında geçiş yapabilirsiniz. Bu öğreticide, **alfabetik** görünüm aracılığıyla özellikleri bulmak daha kolaydır.

1. **Windows Forms Designer'a**geri dön. Formun sağ alt takimindeki küçük beyaz kare olan ve aşağıdaki gibi görünen formun sağ alt sürükleme tutamacını seçin.

    ![Sürükleme kolu](../ide/media/express_bottomrt_drag.png)<br>
   *Sürükleme kolu*

    Form daha geniş ve biraz daha uzun olacak şekilde formu yeniden boyutlandırmak için tutamacı sürükleyin.

1. **Özellikler** penceresine bakın ve **Boyut** özelliğinin değiştiğini fark edin. Formu her yeniden boyutlandırdığınızda **Boyut** özelliği değişir. Formun tutamacını yaklaşık **550, 350** (tam olarak gerek yok) şeklinde yeniden boyutlandırmak için sürüklemeyi deneyin ve bu proje için iyi çalışır. Alternatif olarak, değerleri doğrudan **Boyut** özelliğine girebilir ve sonra **Enter** tuşunu seçebilirsiniz.

1. Uygulamanızı yeniden çalıştırın. Uygulamanızı çalıştırmak için aşağıdaki yöntemlerden herhangi birini kullanabileceğinizi unutmayın.

   - **F5** tuşunu seçin.

   - Menü çubuğunda **Hata** > **Ayıklama Başlat Hata Ayıklama'yı**seçin.

   - Araç çubuğunda, aşağıdaki gibi görünen **Hata Ayıklama Başlat** düğmesini seçin.

      ![Hata Ayıklama araç çubuğu düğmesini başlat](../ide/media/express_icondebug.png)<br>
     ***Hata Ayıklama*** *araç çubuğu düğmesini* başlat

     Daha önce olduğu gibi, IDE uygulamanızı oluşturur ve çalıştırZ ve bir pencere görüntülenir.

1. Bir sonraki adıma geçmeden önce uygulamanızı durdurun, çünkü IDE çalışırken uygulamanızı değiştirmenize izin vermez. Uygulamanızı durdurmak için aşağıdaki yöntemlerden herhangi birini kullanabileceğinizi unutmayın.

   - Araç çubuğunda Hata **Ayıklamayı Durdur** düğmesini seçin.

   - Menü çubuğunda **Hata** > **Ayıklama'yı Durdur'u**seçin.

   - Klavyenizi kullanın ve **Shift**+**F5 tuşuna**basın.

   - **Resim görüntüleyen** penceresinin üst köşesindeki **X** düğmesini seçin.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[bkz: Adım 4: TabloDüzeniPanel denetimi ile formunuzu düzenle.](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**

* Önceki öğretici adıma dönmek için [bkz.](../ide/step-2-run-your-program.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
