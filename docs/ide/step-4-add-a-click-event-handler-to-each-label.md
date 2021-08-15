---
title: '4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme'
description: Her etikete bir tıklama olayı işleyicisi eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 865258edefa07ed824d76762503f29fedfc7335cbc1709288d1392b7bc54d751
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232126"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için, <xref:System.Windows.Forms.Control.Click> Seçilen etiketin rengini değiştiren bir olay işleyicisi ekleyin.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir tıklama olayı işleyicisi eklemek için

1. **Windows Form Tasarımcısı** formunu açın. **Çözüm Gezgini**, *Form1. cs* veya *Form1. vb* öğesini seçin. Menü çubuğunda **Görünüm**  >  **Tasarımcısı**' nı seçin.

2. İlk etiket denetimini belirleyip seçin. Daha sonra, seçmek için diğer etiketlerin her birini seçerken **CTRL** tuşunu basılı tutun. Her etiketin seçildiğinden emin olun.

3. Özellikler **penceresinde** **Olaylar** sayfasını görüntülemek için **Özellikler** penceresindeki araç çubuğundan **Olaylar** düğmesini seçin. **Tıklama** olayına aşağı kaydırın ve aşağıdaki ekran görüntüsünde gösterildiği gibi kutuya **label_Click** girin.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4. **ENTER** tuşunu seçin. IDE, `Click` koda çağrılan bir olay işleyicisi ekler `label_Click()` ve formdaki her etikete takar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet4":::

    > [!IMPORTANT]
    > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Kodu `label_Click()` el ile girmek yerine kod bloğunu kopyalayıp yapıştırırsanız, var olan kodun değiştirilmesini unutmayın `label_Click()` . Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > `object sender`Olay işleyicisinin en üstünde [öğretici 2: süreli bir matematik testi öğreticisi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md) öğreticisinde kullanılan aynı şekilde tanınabiliriz. Tek bir olay işleyicisi yöntemine farklı etiket denetimi tıklamadıklarından, aynı yöntem kullanıcının seçtiği etiketle aynı şekilde çağrılır. Olay işleyicisi yönteminin hangi etiketin seçili olduğunu bilmesi gerekir, bu nedenle `sender` etiket denetimini tanımlamak için adı kullanır. Yöntemin ilk satırı programa yalnızca genel bir nesne değil, özellikle bir etiket denetimi olduğunu ve `clickedLabel` etiketin özelliklerine ve yöntemlerine erişmek için adı kullandığını söyler.

     Bu yöntem ilk `clickedLabel` olarak bir nesneden bir etiket denetimine başarıyla dönüştürülüp dönüştürülmediğini denetler. başarısız olursa, `null` (C#) veya `Nothing` (Visual Basic) değerine sahiptir ve yöntemdeki kodun geri kalanını yürütmek istemezsiniz. Sonra, yöntemi etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. ( `return` Deyimin yöntemi: programın yöntemi yürütmeyi durdurmasını söyler.) Aksi halde, simge seçilmemiş, bu nedenle program etiketin metin rengini siyah olarak değiştiriyor.

6. Menü çubuğunda, devam etmek için **Dosya**  >  **Tümünü Kaydet** ' i seçin ve ardından menü çubuğunda **Hata Ayıkla**  >  **Başlat hata ayıklama Başlat** ' ı seçerek programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md)**.

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).
