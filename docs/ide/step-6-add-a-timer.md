---
title: '6. Adım: Süreölçer ekleme'
description: <xref:System.Windows.Forms.Timer>Eşleşen oyuna nasıl denetim ekleneceğini öğrenin.
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
ms.openlocfilehash: 2367536dd520876d753bce3c3ffa46e4c9853208e9ddf53385c1c84374f160bf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121289185"
---
# <a name="step-6-add-a-timer"></a>6. Adım: Süreölçer ekleme
Ardından, <xref:System.Windows.Forms.Timer> eşleşen oyuna bir denetim eklersiniz. Bir Zamanlayıcı belirtilen sayıda milisaniye bekler ve sonra *değer* olarak adlandırılan bir olayı tetikler. Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.

## <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için

1. **Windows Form Tasarımcısı** içindeki araç kutusundan **zamanlayıcı** ' yı seçin ( **bileşenler** kategorisinde) ve ardından **enter** tuşunu seçin veya bir zamanlayıcı denetimi eklemek için zamanlayıcıyı çift tıklayın. Aşağıdaki görüntüde gösterildiği gibi, **Süreölçer1** adlı zamanlayıcının simgesinin, formun altındaki bir alanda görünmesi gerekir.

     ![Zamanlayıcı](../ide/media/express_timer.png)<br/>
***Zamanlayıcı***

    > [!NOTE]
    > Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.

2. Zamanlayıcıyı seçmek için **Süreölçer1** simgesini seçin. **Özellikler** penceresinde olayları görüntüleme, özellikleri görüntüleme ' ye geçin. Sonra, zamanlayıcının **Interval** özelliğini **750** olarak ayarlayın, ancak **Enabled** özelliğini **false** olarak ayarlayın. **Interval** özelliği, zamanlayıcının, zaman *işaretleri* arasında ne kadar bekleyeceğini ya da olayını ne zaman tetikleyeceğini söyler <xref:System.Windows.Forms.Timer.Tick> . 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. <xref:System.Windows.Forms.Timer.Start>Zamanlayıcıyı yalnızca Player ikinci etiketi seçtikten sonra başlatmak için yöntemini çağıracaksınız.

3. **Windows Form Tasarımcısı** 'de süreölçer denetimi simgesini seçin ve ardından **enter** tuşuna basın veya boş bir Tick olayı işleyicisi eklemek için zamanlayıcıyı çift tıklayın. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet7":::

      > [!IMPORTANT]
      > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

     Tick olay işleyicisi üç şeyi yapar: Ilk olarak, yöntemi çağırarak zamanlayıcının çalışmadığından emin olur <xref:System.Windows.Forms.Timer.Stop> . Daha sonra, `firstClicked` `secondClicked` Player 'ın görünmez bir şekilde seçtiği iki etiketin simgelerini oluşturmak için iki başvuru değişkeni kullanır. Son olarak, `firstClicked` ve `secondClicked` başvuru değişkenlerini `null` C# ve Visual Basic olarak sıfırlar `Nothing` . Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Artık herhangi <xref:System.Windows.Forms.Label> bir denetimi izlemediğinden, Player bir etiketi yeniden seçebilmesi için hazırdır.

    > [!NOTE]
    > Zamanlayıcı nesnesi `Start()` , süreölçeri Başlatan bir yönteme ve `Stop()` bunu durduran bir yönteme sahiptir. Zamanlayıcı 'nın **etkin** özelliğini **Özellikler** penceresinde **doğru** olarak ayarladığınızda, program başladıktan hemen sonra başlatılır. Ancak **false** olarak ayarlandığında, `Start()` yöntemi çağrılana kadar başlatılmaz. Normal olarak, bir Zamanlayıcı Tick olayını tekrar tekrar tekrar tetiklerler ve zaman işaretleri arasında kaç milisaniye bekleneceğini anlamak için **Interval** özelliğini kullanmaktır. Zamanlayıcı `Stop()` yönteminin Tick olayının içinde nasıl çağrıldığını fark etmiş olabilirsiniz. Bu, süreölçeri *tek bir görüntü moduna* geçirir, yani `Start()` Yöntem çağrıldığında, belirtilen aralığı bekler, tek bir Tick olayını tetikler ve sonra duraklar.

4. Yeni zamanlayıcıyı eylemde görmek için, kod düzenleyicisine gidin ve olay işleyicisi yönteminin üst ve alt kısmına aşağıdaki kodu ekleyin `label_Click()` . ( `if` En üste iki deyim ve en alta üç deyim ekliyoruz; yöntemin geri kalanı aynı kalır.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet8":::

     Yöntemin en üstündeki kod, **etkin** özelliğin değerini denetleyerek zamanlayıcının başlatılıp başlatılmayacağını denetler. Bu şekilde, oyuncu birinci ve ikinci etiket denetimlerini seçerse ve Zamanlayıcı başlarsa, üçüncü bir etiket seçilmesi hiçbir şey yapmaz. Ayrıca, oyun başka bir ilk tıklamaya hazırlanmadan önce Player 'ın üçüncü kez hızla tıklamasını önler. 

     Yöntemin en altındaki kod, `secondClicked` Player 'ın seçtiği Ikinci etiket denetimini izlemek için başvuru değişkenini ayarlar ve ardından bu etiketin simge rengini görünür hale getirmek için siyaha ayarlar. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olayı işleyicisi iki simgeyi gizler ve `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar. böylece form Player 'ın başka bir simge çifti seçmesini sağlamak için kullanılır.

5. Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.

6. Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[7. Adım: çiftleri görünür tut](../ide/step-7-keep-pairs-visible.md)**.

- Önceki öğretici adımına dönmek için bkz. [5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md).
