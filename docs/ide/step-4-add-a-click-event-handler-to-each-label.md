---
title: '4\. Adım: Her Etikete Click olay işleyicisi ekleme'
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579340"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4\. Adım: Her Etikete Click olay işleyicisi ekleme

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için, seçilen etiketin rengini değiştiren bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi eklersiniz.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir tıklama olayı işleyicisi eklemek için

1. **Windows Form Tasarımcısı**formunu açın. **Çözüm Gezgini**' de *Form1.cs* veya *Form1. vb*öğesini seçin. Menü çubuğunda **görünüm** > **Tasarımcı**' yı seçin.

2. İlk etiket denetimini belirleyip seçin. Daha sonra, seçmek için diğer etiketlerin her birini seçerken **CTRL** tuşunu basılı tutun. Her etiketin seçildiğinden emin olun.

3. Özellikler **penceresinde** **Olaylar** sayfasını görüntülemek için **Özellikler** penceresindeki araç çubuğundan **Olaylar** düğmesini seçin. **Tıklama** olayına aşağı kaydırın ve aşağıdaki ekran görüntüsünde gösterildiği gibi kutuya **label_Click** girin.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_labelclick.png)

4. **ENTER** tuşunu seçin. IDE, koda `label_Click()` adlı `Click` bir olay işleyicisi ekler ve formdaki her etikete takar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs.Microsoft.com](../ide/media/docs-programming-language-control.png) için programlama dili denetimi ![

    > [!NOTE]
    > Kodu el ile girmek yerine `label_Click()` kod bloğunu kopyalayıp yapıştırırsanız, mevcut `label_Click()` kodunu değiştirdiğinizden emin olun. Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > Olay işleyicisinin üst kısmında `object sender` [öğretici 2: süreli bir matematik test öğreticisi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md) öğreticisinde kullanılan aynı şekilde tanınabiliriz. Tek bir olay işleyicisi yöntemine farklı etiket denetimi tıklamadıklarından, aynı yöntem kullanıcının seçtiği etiketle aynı şekilde çağrılır. Olay işleyicisi yönteminin hangi etiketin seçili olduğunu bilmesi gerekir, bu nedenle etiket denetimini tanımlamak için `sender` adını kullanır. Yöntemin ilk satırı programa yalnızca genel bir nesne değil, özellikle bir etiket denetimi olduğunu ve etiketin özelliklerine ve yöntemlerine erişmek için `clickedLabel` adını kullandığını söyler.

     Bu yöntem ilk olarak, `clickedLabel` bir nesneden bir etiket denetimine başarıyla dönüştürülüp dönüştürülmediğini denetler. Başarısız olursa, `null` (C#) veya `Nothing` (Visual Basic) değerine sahiptir ve yöntemdeki kodun geri kalanını yürütmek istemezsiniz. Sonra, yöntemi etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. (`return` deyimleri şu şekilde yapar: programın yöntemi yürütmeyi durdurmasını söyler.) Aksi halde, simge seçilmemiş, bu nedenle program etiketin metin rengini siyah olarak değiştiriyor.

6. Çalışmanızı kaydetmek için, menü çubuğunda **dosya** > **Tümünü Kaydet** ' i seçin ve ardından menü çubuğunda **Hata Ayıkla** > hata **ayıklamayı Başlat** ' ı seçerek programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md)** .

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).
