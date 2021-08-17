---
title: '4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme'
description: Her etikete tıklama olayı işleyicisi eklemeyi öğrenin.
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

   Programınızı bu şekilde çalışması için, seçilen <xref:System.Windows.Forms.Control.Click> etiketin rengini değiştirir bir olay işleyicisi eklersiniz.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir tıklama olayı işleyicisi eklemek için

1. Form Tasarımcısı'nda **Windows açın.** Bu **Çözüm Gezgini** *Form1.cs veya* *Form1.vb'yi seçin.* Menü çubuğunda Görünüm **Tasarımcısı'ı**  >  **seçin.**

2. İlk etiket denetimini belirleyip seçin. Ardından **Ctrl** tuşunu basılı tutarak diğer etiketlerin her birini seçin. Her etiketin seçildiğinden emin olun.

3. Özellikler **penceresindeki** Olaylar sayfasını görüntülemek için **Özellikler** penceresindeki araç **çubuğundaki** Olaylar **düğmesini** seçin. Ekranı aşağı kaydırarak **Tıklama** olayına **label_Click** ve aşağıdaki ekran görüntüsünde gösterildiği gibi kutuya bir giriş girin.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4. Enter **tuşuna** basın. IDE, koda adlı bir olay işleyicisi ekler ve `Click` `label_Click()` formda etiketlerin her biri için bu işleyiciyi kancalar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet4":::

    > [!IMPORTANT]
    > C# kod parçacığını veya kod parçacığını görüntülemek için bu sayfanın sağ üst kısmında yer alan programlama dili Visual Basic kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Kodu el ile girmek `label_Click()` yerine kod bloğu kopyalayıp yapıştırıyorsanız, mevcut kodu değiştirerek emin `label_Click()` olun. Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > Olay işleyicinin en üstünde, Öğretici 2: Zamanlı matematik testi oluşturma öğreticisinde `object sender` [kullanılanla aynı olduğunu anabilirsiniz.](../ide/tutorial-2-create-a-timed-math-quiz.md) Farklı etiket denetimi tıklama olaylarını tek bir olay işleyicisi yöntemine bağlamış olduğunuz için, kullanıcının hangi etiketi seçerse seçsin aynı yöntem çağrılır. Olay işleyicisi yönteminin hangi etiketin seçiliyor olduğunu belirlemesi gerekir, bu nedenle etiket `sender` denetimi tanımlamak için adı kullanır. Yönteminin ilk satırı, programa yalnızca genel bir nesne değil, özellikle bir etiket denetimi olduğunu ve etiketin özelliklerine ve yöntemlerine erişmek için adı `clickedLabel` kullandığını söyler.

     Bu yöntem ilk olarak bir `clickedLabel` nesneden etiket denetimine başarıyla dönüştürüldü (cast) olup olmadığını denetler. Başarısız olursa ( C#) veya (Visual Basic) değerine sahip olur ve kodun geri kalanını `null` `Nothing` yönteminde yürütmek istemiyorsanız. Ardından yöntemi, etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. (deyimi bunu `return` yapar: Programa yöntemini yürütmeyi durdurması söyler.) Aksi takdirde simge seçilmemiş ve bu nedenle program etiketin metin rengini siyah olarak değiştirir.

6. Menü çubuğunda Dosya Kaydet'i seçerek ilerlemenizi kaydedin ve ardından menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek  >     >   programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 5. Adım: Etiket başvuruları ekleme.](../ide/step-5-add-label-references.md)**

- Önceki öğretici adımına dönmek için [bkz. 3. Adım: Her etikete rastgele bir simge atama.](../ide/step-3-assign-a-random-icon-to-each-label.md)
