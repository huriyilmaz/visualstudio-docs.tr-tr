---
title: '4. Adım: Her Etikete Click olay Işleyicisi ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b78a1757586dfaf6087711eaf1ed6001155a3b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671797"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4. Adım: Her Etikete Click Olay İşleyicisi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşleştirme oyunu aşağıdaki gibi çalışır:

1. Oyuncu gizli simge içeren karelerden birini seçtiğinde, program simge rengini siyaha dönüştürerek bu simgeyi oyuncuya gösterir.

2. Oyuncu daha sonra başka bir gizli simge seçer.

3. Simgeler eşleşirse görünür olarak kalırlar. Aksi takdirde iki simge de tekrar gizlenir.

   Programınızın bu şekilde çalışmasını sağlamak için, seçilen etiketin rengini değiştiren bir Tıklama olayı işleyicisi eklersiniz.

### <a name="to-add-a-click-event-handler-to-each-label"></a>Her etikete bir Tıklama olayı işleyicisi eklemek için

1. Formu Windows Form Tasarımcısı'nda açın. Çözüm Gezgini'nde Form1.cs veya Form1.vb öğesini seçin. Menü çubuğunda **Görünüm**, **Tasarımcı**' yı seçin.

2. İlk etiket denetimini belirleyip seçin. Ardından CTRL tuşunu basılı tutarken diğer etiketleri tek tek belirleyip seçin. Her etiketin seçildiğinden emin olun.

3. Özellikler **penceresinde** **Olaylar** sayfasını görüntülemek için **Özellikler** penceresindeki araç çubuğundan **Olaylar** düğmesini seçin. **Tıklama** olayına aşağı kaydırın ve aşağıdaki resimde gösterildiği gibi kutuya **label_Click** girin.

     ![Click olayını gösteren Özellikler penceresi](../ide/media/express-labelclick.png "Express_labelClick") Click olayını gösteren Özellikler penceresi

4. ENTER tuşunu seçin. IDE, koda çağrılan bir tıklama olayı işleyicisi ekler `label_Click()` ve formdaki her etikete takar.

5. Kodun geri kalanını aşağıdaki gibi doldurun:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]

    > [!NOTE]
    > Kodu `label_Click()` el ile girmek yerine kod bloğunu kopyalayıp yapıştırırsanız, var olan kodun değiştirilmesini unutmayın `label_Click()` . Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

    > [!NOTE]
    > `object sender`Olay işleyicisinin en üstünde [öğretici 2: süreli bir matematik testi öğreticisi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md) öğreticisinde kullanılan aynı şekilde tanınabiliriz. Tek bir olay işleyicisi yöntemine farklı etiket denetimi Tıklama olayı tutturduğunuzdan, kullanıcının seçtiği etiket hangisi olursa olsun aynı yöntem çağrılır. Olay işleyicisi yönteminin hangi etiketin seçili olduğunu bilmesi gerekir, bu nedenle etiket denetimini tanımlamak için **Gönderen** adını kullanır. Yöntemin ilk satırı programa yalnızca genel bir nesne değil, özel olarak bir etiket denetimi olduğunu ve etiketin özelliklerine ve yöntemlerine erişmek için **Click adlı Click** adını kullandığını söyler.

     Bu yöntem ilk önce, **Click** nesnesinin bir nesneden bir etiket denetimine başarıyla dönüştürülüp dönüştürülmediğini denetler. Başarısız olursa, `null` (C#) veya `Nothing` (Visual Basic) değerine sahiptir ve yöntemdeki kodun geri kalanını yürütmek istemezsiniz. Sonra, yöntemi etiketin **ForeColor** özelliğini kullanarak seçilen etiketin metin rengini denetler. Etiketin metin rengi siyah ise, simge zaten seçilmiş ve yöntem bitmiş demektir. ( `return` Deyimin yöntemi: programın yöntemi yürütmeyi durdurmasını söyler.) Aksi halde, simge seçilmemiş, bu nedenle program etiketin metin rengini siyah olarak değiştiriyor.

6. Menü çubuğunda **Dosya**, **Tümünü Kaydet** ' i seçerek ilerlemenizi kaydedin, sonra da menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat** ' ı seçerek programınızı çalıştırın. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçtiğinizde, simgelerden birinin görünür hale gelmesi gerekir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md).

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).
