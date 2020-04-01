---
title: '6. Adım: Süreölçer ekleme'
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0473ab07155e0f132e8e6207361e409b804257f2
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472773"
---
# <a name="step-6-add-a-timer"></a>6. Adım: Süreölçer ekleme
Sonra, eşleşen <xref:System.Windows.Forms.Timer> oyuna bir denetim ekleyin. Zamanlayıcı belirli sayıda milisaniye bekler ve ardından *işaretçi*olarak adlandırılan bir olayı ateşler. Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.

## <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için

1. **Windows Forms Designer'daki**araç kutusundan **Zamanlayıcı'yı** **(Bileşenler** kategorisinde) seçin ve ardından **Enter** tuşunu seçin veya forma zamanlayıcı denetimi eklemek için zamanlayıcıyı çift tıklatın. **Zamanlayıcının Timer1**adı verilen simgesi, aşağıdaki resimde gösterildiği gibi formun altındaki bir boşlukta görünmelidir.

     ![Zamanlayıcı](../ide/media/express_timer.png)<br/>
***Zamanlayıcı***

    > [!NOTE]
    > Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.

2. Zamanlayıcıyı seçmek için **Timer1** simgesini seçin. **Özellikler** penceresinde, olayları görüntülemekten görüntüleme özelliklerine geçin. Daha sonra, zamanlayıcının **Interval** özelliğini **750**olarak ayarlayın, ancak **Etkin** özelliğini **False**olarak ayarlayın. **Interval** özelliği zamanlayıcıya *keneler*arasında ne kadar beklemesi <xref:System.Windows.Forms.Timer.Tick> gerektiğini veya olayını ne zaman tetiklediğini söyler. 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. Zamanlayıcıyı <xref:System.Windows.Forms.Timer.Start> başlatmak için yöntemi ancak oyuncu ikinci etiketi seçtikten sonra ararsınız.

3. **Windows Forms Designer'daki** zamanlayıcı denetim simgesini seçin ve ardından boş bir Tick olay işleyicisi eklemek için **Enter** tuşunu seçin veya zamanlayıcıyı çift tıklatın. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)

     Tick olay işleyicisi üç şey yapar: İlk olarak, <xref:System.Windows.Forms.Timer.Stop> yöntem çağırarak zamanlayıcı çalışmadığından emin olun. Daha sonra iki referans `firstClicked` değişkeni kullanır ve `secondClicked`, oyuncunun tekrar görünmez seçtiği iki etiketin simgelerini yapmak için. `firstClicked` Son olarak, c# `secondClicked` ve `Nothing` Visual `null` Basic'teki ve referans değişkenlerini sıfırlar. Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Şimdi herhangi bir <xref:System.Windows.Forms.Label> kontrolleri takip etmiyor ve oyuncunun yeniden bir etiket seçmesi ne kadar hazır.

    > [!NOTE]
    > Zamanlayıcı nesnesinin `Start()` zamanlayıcıyı başlatan bir yöntemi `Stop()` ve onu durduran bir yöntemi vardır. **Özellikler** penceresinde zamanlayıcının **Etkin** özelliğini **True** olarak ayarladığınızda, program başlar başlamaz işlemeye başlar. Ancak, **false**olarak ayarlanmış bıraktığınızda, yöntemi çağrılana `Start()` kadar işlemeye başlamaz. Normalde, bir zamanlayıcı, keneler arasında kaç milisaniye beklemeniz gerektiğini belirlemek için **Interval** özelliğini kullanarak Tick olayını tekrar tekrar işaretler. Zamanlayıcının `Stop()` yönteminin Tick olayının içinde nasıl çağrıldığını fark etmiş olabilirsiniz. Bu, zamanlayıcıyı *tek bir çekim moduna* `Start()` koyar, yani yöntem çağrıldığında, belirtilen aralığı bekler, tek bir Tick olayını tetikler ve sonra durur.

4. Yeni zamanlayıcının iş başında olduğunu görmek için kod düzenleyicisine gidin ve `label_Click()` olay işleyicisi yönteminin üst ve alt bölümüne aşağıdaki kodu ekleyin. (En üste iki, `if` alta üç ifade ekliyorsunuz; yöntemin geri kalanı aynı kalır.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Yöntemin üst kısmındaki kod, **Etkinleştirilen** özelliğin değerini denetleyerek zamanlayıcının başlatılıp başlatılmadığını denetler. Bu şekilde, oyuncu birinci ve ikinci Etiket denetimlerini seçerse ve zamanlayıcı başlarsa, üçüncü bir etiket seçmek hiçbir işe yaramaz. Ayrıca oyun başka bir ilk tıklama için hazır olmadan önce hızlı bir şekilde üçüncü kez tıklayarak oyuncu engeller. 

     Yöntemin altındaki kod, oyuncunun `secondClicked` seçtiği ikinci Etiket denetimini izlemek için başvuru değişkenini ayarlar ve daha sonra görünür olması için etiketin simge rengini siyaha ayarlar. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olay işleyicisi iki simgeyi gizler ve formun başka bir simge çiftini seçmesi için formun hazır olması için `firstClicked` ve `secondClicked` referans değişkenlerini sıfırlar.

5. Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.

6. Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 7: Çiftleri görünür tutun.](../ide/step-7-keep-pairs-visible.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-5-add-label-references.md)
