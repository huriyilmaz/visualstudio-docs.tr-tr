---
title: '6. Adım: Süreölçer ekleme'
description: Eşleştirme oyununa <xref:System.Windows.Forms.Timer> denetim ekleme hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 964f49c6a149ccf0f5af46456005ff0e1f82826b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078056"
---
# <a name="step-6-add-a-timer"></a>6. Adım: Süreölçer ekleme
Ardından, eşleştirme <xref:System.Windows.Forms.Timer> oyununa bir denetim eklersiniz. Süreölçer belirtilen sayıda milisaniye bekler ve ardından değer işareti olarak adlandırılan bir olayı *sağlar.* Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.

## <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için

1. **Windows Forms Tasarımcısı'nda** araç kutusundan Zamanlayıcı **'yı** (Bileşenler kategorisinde) seçin ve **enter** tuşuna basın veya forma zamanlayıcı denetimi eklemek için zamanlayıcıya çift tıklayın.  Zamanlayıcının **Timer1** adlı simgesi, aşağıdaki görüntüde gösterildiği gibi formun altındaki bir alanda görünecektir.

     ![Zamanlayıcı](../ide/media/express_timer.png)<br/>
***Zamanlayıcı***

    > [!NOTE]
    > Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.

2. Zamanlayıcıyı **seçmek için Zamanlayıcı1** simgesini seçin. Özellikler **penceresinde,** olayları görüntülemeden özellikleri görüntülemeye geçiş. Ardından zamanlayıcının **Interval** özelliğini **750** olarak ayarlayın, ancak **Enabled** özelliğini False olarak **bırakın.** **Interval özelliği** zamanlayıcıya saat işaretlerini ne kadar *süreyle* bekleyeceğini veya ne zaman olayı tetikley olduğunu <xref:System.Windows.Forms.Timer.Tick> söyler. 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. Zamanlayıcıyı başlatmak <xref:System.Windows.Forms.Timer.Start> için yöntemini çağırarak ancak oynatıcı ikinci etiketi seçtikten sonra başlat.

3. Form Tasarımcısı'nda **zamanlayıcı Windows simgesini** seçin ve **enter** tuşuna basın veya zamanlayıcıya çift tıklar ve boş bir Tick olayı işleyicisi ekleyin. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet7":::

      > [!IMPORTANT]
      > C# kod parçacığını veya kod parçacığını görüntülemek için bu sayfanın sağ üst kısmında yer alan programlama dili Visual Basic kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

     Tick olayı işleyicisi üç şey yapar: İlk olarak, yöntemini çağırarak zamanlayıcının çalışmay olduğundan emin <xref:System.Windows.Forms.Timer.Stop> olur. Ardından, oyuncunun seçtiği iki etiketin simgelerini yeniden görünmez yapmak için ve olmak `firstClicked` için iki başvuru değişkeni `secondClicked` kullanır. Son olarak, ve başvuru `firstClicked` `secondClicked` değişkenlerini C# içinde ve `null` `Nothing` Visual Basic. Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Artık herhangi bir denetimi izlemez ve oynatıcının bir etiketi yeniden <xref:System.Windows.Forms.Label> seçmesi için hazırdır.

    > [!NOTE]
    > Zamanlayıcı nesnesinin `Start()` zamanlayıcıyı başlatan bir yöntemi ve onu `Stop()` durduran bir yöntemi vardır. Özellikler penceresinde zamanlayıcının **Etkin** özelliğini **True**  olarak ayarlıyorsa, program başlar başlamaz tıklanır. Ancak False olarak bırakarak **yöntemi** çağrılana kadar `Start()` tıklar. Normalde zamanlayıcı, tıklar arasında kaç milisaniye bekleyeceğini belirlemek için **Interval** özelliğini kullanarak Tick olayını tekrar tekrar verir. Zamanlayıcının yönteminin Tick olayı içinde `Stop()` nasıl çağrıldını fark etmişsinizdir. Bu, zamanlayıcıyı tek bir atış moduna *koyar.* Başka bir ifadeyle yöntem çağrıldında belirtilen aralığı bekler, tek bir Tick olayı tetikler ve `Start()` ardından durur.

4. Yeni zamanlayıcıyı iş başında görmek için kod düzenleyicisine gidin ve olay işleyicisi yönteminin üst ve alt `label_Click()` kısmında aşağıdaki kodu ekleyin. (En üstüne iki deyim ve en alta üç deyim ekliyoruz; yöntemin `if` geri kalanı aynı kalır.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet8":::

     Yöntemin en üstünde yer alan kod, Enabled özelliğinin değerini kontrol ederek zamanlayıcının başlat olup **olmadığını** denetler. Böylece, oyuncu birinci ve ikinci Etiket denetimlerini seçerse zamanlayıcı başlatılırsa üçüncü bir etiket seçmek hiçbir şey yapmaz. Ayrıca, oyun başka bir ilk tıklama için hazır olmadan önce oyuncunun üçüncü kez hızlı bir şekilde tıklamasını da önler. 

     Yöntemin alt kısmında yer alan kod, başvuru değişkenini oynatıcının seçtiği ikinci Etiket denetimine göre ayarlar ve ardından etiketin simge rengini siyah olarak ayararak görünür `secondClicked` hale gelir. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olayı işleyicisi iki simgeyi gizler ve ve başvuru değişkenlerini sıfırlar, böylece form, oyuncunun başka bir simge `firstClicked` `secondClicked` çifti seçmesi için hazır olur.

5. Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.

6. Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. **[7. Adım: Çiftleri görünür durumda tutma.](../ide/step-7-keep-pairs-visible.md)**

- Önceki öğretici adımına dönmek için [bkz. 5. Adım: Etiket başvuruları ekleme.](../ide/step-5-add-label-references.md)
