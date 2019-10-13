---
title: '4\. Adım: Her etikete bir tıklama olayı işleyicisi ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b60f9bb1fffb9fb36311ad3fda504c1ff2260ce
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289691"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4\. Adım: Her etikete bir tıklama olayı işleyicisi ekleme

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için, seçilen etiketin rengini değiştiren bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi eklersiniz.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir tıklama olayı işleyicisi eklemek için

1. **Windows Form Tasarımcısı**formunu açın. **Çözüm Gezgini**' de *Form1.cs* veya *Form1. vb*öğesini seçin. Menü çubuğunda  >  tasarımcısını **görüntüle**' yi seçin.

2. İlk etiket denetimini belirleyip seçin. Daha sonra, seçmek için diğer etiketlerin her birini seçerken **CTRL** tuşunu basılı tutun. Her etiketin seçildiğinden emin olun.

3. Özellikler **penceresinde** **Olaylar** sayfasını görüntülemek için **Özellikler** penceresindeki araç çubuğundan **Olaylar** düğmesini seçin. **Click** olayına aşağı kaydırın ve aşağıdaki resimde gösterildiği gibi kutuya **label_Click** girin.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4. **ENTER** tuşunu seçin. IDE, koda `label_Click()` adlı `Click` olay işleyicisi ekler ve formdaki her etikete takar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs. Microsoft. com @ no__t-1 için ![Programlama dil denetimi

    > [!NOTE]
    > Kodu el ile girmek yerine `label_Click()` kod bloğunu kopyalayıp yapıştırırsanız, var olan `label_Click()` kodunu değiştirdiğinizden emin olun. Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > Olay işleyicisinin en üstündeki `object sender` ' i, [Öğretici 2 ' de kullanılan aynı şekilde ayırt edebilirsiniz: Zaman aşımına uğramış bir matematik sınavını oluşturun @ no__t-0 öğreticisi. Tek bir olay işleyicisi yöntemine farklı etiket denetimi tıklamadıklarından, aynı yöntem kullanıcının seçtiği etiketle aynı şekilde çağrılır. Olay işleyicisi yönteminin hangi etiketin seçili olduğunu bilmesi gerekir, bu nedenle etiket denetimini tanımlamak için `sender` adını kullanır. Yöntemin ilk satırı programa yalnızca genel bir nesne değil, özellikle bir etiket denetimi olduğunu ve etiketin özelliklerine ve yöntemlerine erişmek için `clickedLabel` adını kullandığını söyler.

     Bu yöntem ilk olarak, `clickedLabel` ' ın bir nesneden bir etiket denetimine başarıyla dönüştürülüp dönüştürülmediğini denetler. Başarısız olursa, `null` (C#) veya `Nothing` (Visual Basic) değerine sahiptir ve yöntemdeki kodun geri kalanını yürütmek istemezsiniz. Sonra, yöntemi etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. (@No__t-0 ifadesinin yaptığı bu,: Programın yöntemi yürütmeyi durdurmasını söyler.) Aksi takdirde simge seçilmemiş demektir ve dolayısıyla program etiketin metin rengini siyah olarak değiştirir.

6. Menü çubuğunda **dosya**@no__t seçin-1**Tümünü Kaydet** ' i seçin ve ardından menü çubuğunda **Hata Ayıkla** > **hata ayıklamayı Başlat** ' ı seçerek programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Adım 5: Etiket başvuruları ekleyin @ no__t-0.

- Önceki öğretici adımına dönmek için bkz. [Step 3: Her etikete bir rastgele simge atayın @ no__t-0.
