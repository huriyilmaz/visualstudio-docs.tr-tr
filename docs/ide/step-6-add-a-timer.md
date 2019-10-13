---
title: '6\. Adım: Süreölçer ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2f58e969f96d05828a4b3a5e640ede364abca10
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289642"
---
# <a name="step-6-add-a-timer"></a>6\. Adım: Süreölçer ekleme
Ardından, eşleşen oyuna <xref:System.Windows.Forms.Timer> denetimi eklersiniz. Bir Zamanlayıcı belirtilen sayıda milisaniye bekler ve sonra *değer*olarak adlandırılan bir olayı tetikler. Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.

## <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için

1. **Windows Form Tasarımcısı**içindeki Araç kutusundan **Zamanlayıcı** ' yı seçin ( **Bileşenler** kategorisinde) ve ardından **ENTER** tuşunu seçin veya bir zamanlayıcı denetimi eklemek için zamanlayıcıyı çift tıklayın. Aşağıdaki resimde gösterildiği gibi, **Süreölçer1**adlı zamanlayıcının simgesinin, formun altındaki bir alanda görünmesi gerekir.

     ![Timer](../ide/media/express_timer.png)<br/>
**Timer**

    > [!NOTE]
    > Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.

2. Zamanlayıcıyı seçmek için **Süreölçer1** simgesini seçin. **Özellikler** penceresinde olayları görüntüleme, özellikleri görüntüleme ' ye geçin. Sonra, zamanlayıcının **Interval** özelliğini **750**olarak ayarlayın, ancak **Enabled** özelliğini **false**olarak ayarlayın. **Interval** özelliği, zamanlayıcının *Tick*'ler arasında ne kadar bekleneceğini veya <xref:System.Windows.Forms.Timer.Tick> olayını tetikleyeceğini söyler. 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. Zamanlayıcıyı yalnızca Player ikinci etiketi seçtikten sonra başlatmak için <xref:System.Windows.Forms.Timer.Start> yöntemini çağıracaksınız.

3. **Windows Form Tasarımcısı** 'de süreölçer denetimi simgesini seçin ve ardından **ENTER** tuşuna basın veya boş bir Tick olayı işleyicisi eklemek için zamanlayıcıyı çift tıklayın. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs. Microsoft. com @ no__t-1 için ![Programlama dil denetimi

     Tick olay işleyicisi üç şey yapar: İlk olarak, <xref:System.Windows.Forms.Timer.Stop> yöntemini çağırarak zamanlayıcının çalışmadığından emin olur. Ardından, Player 'ın görünmez bir şekilde seçtiği iki etiketin simgelerini yapmak için `firstClicked` ve `secondClicked` olarak iki başvuru değişkeni kullanır. Son olarak, `firstClicked` ve `secondClicked` başvuru değişkenlerini Visual C# 'te `null` ' ye ve Visual Basic `Nothing` ' e sıfırlar. Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Artık @no__t 0 denetimlerin izlemediğini ve Player 'ın bir etiketi yeniden seçmesini sağlamak için hazır olduğunu göreceksiniz.

    > [!NOTE]
    > Zamanlayıcı nesnesi, süreölçeri Başlatan `Start()` yöntemine ve bunu durduran bir `Stop()` yöntemine sahiptir. Zamanlayıcı 'nın **etkin** özelliğini **Özellikler** penceresinde **doğru** olarak ayarladığınızda, program başladıktan hemen sonra başlatılır. Ancak **false**olarak ayarladıktan sonra, `Start()` yöntemi çağrılana kadar başlatılmaz. Normal olarak, bir Zamanlayıcı Tick olayını tekrar tekrar tekrar tetiklerler ve zaman işaretleri arasında kaç milisaniye bekleneceğini anlamak için **Interval** özelliğini kullanmaktır. Zamanlayıcının `Stop()` yönteminin Tick olayının içinde nasıl çağrıldığını fark etmiş olabilirsiniz. Bu, `Start()` yöntemi çağrıldığında, belirtilen Aralık için beklediği, tek bir Tick olayını tetikleyen ve ardından durdurduğu anlamına gelen süreölçeri *tek bir görüntü moduna*geçirir.

4. Yeni zamanlayıcıyı eylemde görmek için, kod düzenleyicisine gidin ve `label_Click()` olay işleyicisi yönteminin üst ve alt kısmına aşağıdaki kodu ekleyin. (En üste bir `if` deyimi ve en alta üç deyim ekliyoruz; yöntemin geri kalanı aynı kalır.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Yöntemin en üstündeki kod, **etkin** özelliğin değerini denetleyerek zamanlayıcının başlatılıp başlatılmayacağını denetler. Bu şekilde, oyuncu birinci ve ikinci etiket denetimlerini seçerse ve Zamanlayıcı başlarsa, üçüncü bir etiket seçilmesi hiçbir şey yapmaz.

     Yöntemin en altındaki kod, oynatıcının seçtiği ikinci etiket denetimini izlemek için `secondClicked` başvuru değişkenini ayarlar ve ardından bu etiketin simge rengini görünür hale getirmek için siyaha ayarlar. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olayı işleyicisi iki simgeyi gizler ve `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar, böylece form Player 'ın başka bir simge çifti seçmesini sağlamak için kullanılır.

5. Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.

6. Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Adım 7: Çiftleri görünür tutun @ no__t-0.

- Önceki öğretici adımına dönmek için bkz. [Adım 5: Etiket başvuruları ekleyin @ no__t-0.
