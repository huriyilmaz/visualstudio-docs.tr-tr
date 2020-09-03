---
title: '6. Adım: Zamanlayıcı ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a2d47a66cdedfc191212a178221712de6aefa61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671694"
---
# <a name="step-6-add-a-timer"></a>6. Adım: Zamanlayıcı Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ardından, eşleşen oyuna bir **Zamanlayıcı** denetimi eklersiniz. Bir Zamanlayıcı belirtilen sayıda milisaniye bekler ve sonra *değer*olarak adlandırılan bir olayı tetikler. Bu olay, bir eylemi başlatmak veya eylemi düzenli aralıklarla yinelemek için kullanışlıdır. Bu durumda, oyuncuların iki simge seçmesini sağlamak ve simgeler eşleşmez ise, kısa bir süre sonra bu iki simgeyi yeniden gizlemek için bir zamanlayıcı kullanacaksınız.

### <a name="to-add-a-timer"></a>Zamanlayıcı eklemek için

1. Windows Form Tasarımcısı içindeki Araç kutusundan **Zamanlayıcı** ' yı seçin ( **Bileşenler** KATEGORISINDE) ve ardından Enter tuşunu seçin veya bir zamanlayıcı denetimi eklemek için zamanlayıcıyı çift tıklayın. Aşağıdaki resimde gösterildiği gibi, **Süreölçer1**adlı zamanlayıcının simgesinin, formun altındaki bir alanda görünmesi gerekir.

     ![Zamanlayıcı](../ide/media/express-timer.png "Express_Timer") Görevine

    > [!NOTE]
    > Araç kutusu boş ise, araç kutusunu açmadan önce formun arkasındaki kodu değil de, form tasarımcısını seçtiğinizden emin olun.

2. Zamanlayıcıyı seçmek için **Süreölçer1** simgesini seçin. **Özellikler** penceresinde olayları görüntüleme, özellikleri görüntüleme ' ye geçin. Sonra, zamanlayıcının **Interval** özelliğini **750**olarak ayarlayın, ancak **Enabled** özelliğini **false**olarak ayarlayın. **Interval** özelliği, zamanlayıcının *Tick 'ler arasında ne*kadar bekleneceğini veya bunun Tick olayını ne zaman tetikleyeceğini söyler. 750 değeri zamanlayıcıya, Tick olayını tetiklemeden önce saniyenin dörtte üçü kadar (750 milisaniye) beklemesini bildirir. `Start()`Zamanlayıcıyı yalnızca Player ikinci etiketi seçtikten sonra başlatmak için yöntemini çağıracaksınız.

3. Windows Form Tasarımcısı 'de süreölçer denetimi simgesini seçin ve ardından ENTER tuşuna basın veya boş bir **Tick** olayı işleyicisi eklemek için zamanlayıcıyı çift tıklayın. Kodu aşağıdaki kodla değiştirin ya da aşağıdaki kodu olay işleyicisine el ile girin.

     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]

     Tick olay işleyicisi üç şeyi yapar: Ilk olarak, yöntemi çağırarak zamanlayıcının çalışmadığından emin olur `Stop()` . Daha sonra, `firstClicked` `secondClicked` Player 'ın görünmez bir şekilde seçtiği iki etiketin simgelerini oluşturmak için iki başvuru değişkeni kullanır. Son olarak, `firstClicked` ve `secondClicked` başvuru değişkenlerini `null` Visual C# ve Visual Basic olarak sıfırlar `Nothing` . Programın kendini sıfırlama şekli olması nedeniyle bu adım önemlidir. Artık herhangi `Label` bir denetimi izlemediğinden, Player bir etiketi yeniden seçebilmesi için hazırdır.

    > [!NOTE]
    > Bir `Timer` nesne `Start()` , süreölçeri Başlatan bir yönteme ve `Stop()` bunu durduran bir yönteme sahiptir. Zamanlayıcı 'nın **etkin** özelliğini **Özellikler** penceresinde **doğru** olarak ayarladığınızda, program başladıktan hemen sonra başlatılır. Ancak **false**olarak ayarlandığında, `Start()` yöntemi çağrılana kadar başlatılmaz. Normal olarak, bir Zamanlayıcı Tick olayını tekrar tekrar tekrar tetiklerler ve zaman işaretleri arasında kaç milisaniye bekleneceğini anlamak için **Interval** özelliğini kullanmaktır. Zamanlayıcı `Stop()` yönteminin Tick olayının içinde nasıl çağrıldığını fark etmiş olabilirsiniz. Bu, süreölçeri *tek bir görüntü moduna*geçirir, yani `Start()` Yöntem çağrıldığında, belirtilen aralığı bekler, tek bir Tick olayını tetikler ve sonra duraklar.

4. Yeni zamanlayıcıyı eylemde görmek için, kod düzenleyicisine gidin ve olay işleyicisi yönteminin üst ve alt kısmına aşağıdaki kodu ekleyin `label_Click()` . ( `if` En üste bir deyim ve en alta üç deyim ekliyoruz; yöntemin geri kalanı aynı kalır.)

     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]

     Yöntemin en üstündeki kod, **etkin** özelliğin değerini denetleyerek zamanlayıcının başlatılıp başlatılmayacağını denetler. Bu şekilde, oyuncu ilk ve ikinci `Label` denetimleri seçerse ve Zamanlayıcı başlarsa, üçüncü bir etiket seçilmesi hiçbir şey yapmaz.

     Yöntemin en altındaki kod, `secondClicked` Player 'ın seçtiği ikinci denetimi izlemek için başvuru değişkenini ayarlar `Label` ve ardından bu etiketin simge rengini görünür hale getirmek için siyaha ayarlar. Daha sonra, 750 milisaniye bekler ve tek bir Tick olayı tetiklemesi için zamanlayıcıyı tek sefer modunda başlatır. Zamanlayıcının Tick olayı işleyicisi iki simgeyi gizler ve `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar. böylece form Player 'ın başka bir simge çifti seçmesini sağlamak için kullanılır.

5. Programınızı kaydedin ve çalıştırın. Bir simge seçin; bu simge görünür duruma gelir.

6. Başka bir simge seçin. Kısa bir süre görünür ve sonra iki simge birden kaybolur. Bunu birçok kez tekrar edin. Form artık, seçtiğiniz birinci ve ikinci simgeleri takip ediyor ve simgelerin kaybolmasını sağlamadan önce duraklamak için zamanlayıcıyı kullanıyor.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [7. Adım: çiftleri görünür tut](../ide/step-7-keep-pairs-visible.md).

- Önceki öğretici adımına dönmek için bkz. [5. Adım: etiket başvuruları ekleme](../ide/step-5-add-label-references.md).
