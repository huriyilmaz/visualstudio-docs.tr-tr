---
title: 'Adım 4: Her etikete bir tıklama olay işleyicisi ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7049271dddb4e763bf5ecb3760358bdd63e38df5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579340"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Adım 4: Her etikete bir tıklama olay işleyicisi ekleme

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için, seçilen etiketin rengini değiştiren bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi eklersiniz.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete tıklama olayı işleyicisi eklemek için

1. **Formu Windows Forms Designer'da**açın. **Çözüm Gezgini'nde,** *Form1.cs* veya *Form1.vb'yi*seçin. Menü çubuğunda**Tasarımcıyı** **Görüntüle'yi** > seçin.

2. İlk etiket denetimini belirleyip seçin. Ardından, diğer etiketlerin her birini seçerek bunları seçerken **Ctrl** tuşunu basılı tutun. Her etiketin seçildiğinden emin olun.

3. **Özellikler** penceresindeki **Etkinlikler** sayfasını görüntülemek için **Özellikler** penceresindeki araç çubuğundaki **Etkinlikler** düğmesini seçin. Aşağıdaki ekran görüntüsünde gösterildiği gibi **Click** olayına gidin ve **label_Click** kutuya girin.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4. **Enter** tuşunu seçin. IDE, koda çağrılan `Click` `label_Click()` bir olay işleyicisi ekler ve bu kodu formdaki etiketlerin her birine bağlar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Kodu el ile girmek `label_Click()` yerine kod bloğunu kopyalayıp yapıştırıyorsanız, varolan `label_Click()` kodu değiştirdiğinden emin olun. Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > Etkinlik işleyicisinin üst `object sender` [kısmında, Öğretici 2: Zamanlanmış bir matematik testi](../ide/tutorial-2-create-a-timed-math-quiz.md) öğreticisi oluşturun' da kullanılanın aynısını tanıyabilirsiniz. Farklı etiket denetimi tıklama olaylarını tek bir olay işleyicisi yöntemine bağladığınızdan, kullanıcı hangi etiketi seçerse seçsin aynı yöntem edenir. Olay işleyicisi yönteminin hangi etiketin seçildiğini `sender` bilmesi gerekir, bu nedenle etiket denetimini tanımlamak için adı kullanır. Yöntemin ilk satırı, programa yalnızca genel bir nesne değil, özellikle bir etiket denetimi olduğunu `clickedLabel` ve etiketin özelliklerine ve yöntemlerine erişmek için adı kullandığını söyler.

     Bu yöntem ilk `clickedLabel` olarak bir nesneden etiket denetimine başarıyla dönüştürülüp dönüştürülmediğini (döküm) denetler. Başarısız olursa, `null` (C#) veya `Nothing` (Visual Basic) değerine sahiptir ve yöntemde kodun geri kalanını yürütmek istemezsiniz. Ardından, yöntem, etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. (Bu `return` ifade ne yapar: Bu yöntemi yürütmeyi durdurmak için program söyler.) Aksi takdirde, simge seçilmediğinden, program etiketin metin rengini siyaha değiştirir.

6. Menü çubuğunda, ilerlemenizi kaydetmek için**Tümlerini Kaydet'i** **File** > seçin ve ardından menü çubuğunda programınızı çalıştırmak için **Hata Ayıklama** > **Hata Ayıklama'yı** seçin. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz.](../ide/step-5-add-label-references.md)**

- Önceki öğretici adıma dönmek için [bkz: Adım 3: Her etikete rasgele bir simge atayın.](../ide/step-3-assign-a-random-icon-to-each-label.md)
