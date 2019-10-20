---
title: '3\. Adım: her etikete rastgele bir simge atama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4382a450051b7626a5eb5e29bf2ce4e78f6eceda
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671833"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3\. Adım: Her Etikete Rasgele Simge Atama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, bir `AssignIconsToSquares()` yöntemi kullanarak, simgeleri formunuzdaki etiket denetimlerine rastgele atayın.

### <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük vardır: görsel C# `foreach` ve Visual Basic `For Each`. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Önceki adımda gösterildiği gibi `AssignIconsToSquares()` yöntemini ekleyin. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz kodun hemen altına yerleştirebilirsiniz.

     Daha önce belirtildiği gibi, `AssignIconsToSquares()` yönteminde yeni bir şey vardır: görselde C# bir `foreach` döngüsü ve Visual Basic `For Each`. @No__t_0 döngüsünü aynı eylemi birden çok kez yapmak istediğiniz zaman kullanabilirsiniz. Bu durumda, aşağıdaki kod ile açıklandığı gibi, TableLayoutPanel denetiminizdeki her öğe için aynı deyimleri yürütmek istiyorsunuz. İlk satır, her denetimi bir kerede depolayan `control` adlı bir değişken oluşturur ve bu denetim, bu denetimde yürütülen Döngülerdeki deyimler vardır.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     @No__t_0 yöntemi TableLayoutPanel içindeki her etiket denetimi boyunca yinelenir ve her biri için aynı deyimleri yürütür. Bu deyimler [Adım 2: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz listeden rastgele bir simge çeker. (Listeye her simgeden iki tane eklemenizin nedeni budur; böylece rasgele etiket denetimlerine atanmış bir çift simge olur.)

     @No__t_0 veya `For Each` döngüsü içinde çalışan koda daha yakından bakın. Bu kod burada tekrar üretilmektedir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     İlk satır `control` değişkenini `iconLabel` adlı bir etikete dönüştürür. Bundan sonraki satır, dönüştürmenin çalıştığından emin olmak için kontrol eden bir `if` deyimidir. Dönüştürme işe alıyorsa, `if` deyimindeki deyimler çalıştırılır. (Önceki öğreticilerden hatırlayabileceğiniz gibi, belirttiğiniz herhangi bir koşulu değerlendirmek için `if` deyimleri kullanılır.) @No__t_1 deyimindeki ilk satır, simgeler listesindeki öğelerden birine karşılık gelen rastgele bir sayı içeren `randomNumber` adlı bir değişken oluşturur. Bunu yapmak için, daha önce oluşturduğunuz `Random` nesnesinin `Next` yöntemini kullanır. @No__t_0 yöntemi rastgele sayı döndürür. Bu satır ayrıca rastgele sayının seçim aralığını belirlemek için `icons` listesinin `Count` özelliğini kullanır. Sonraki satır, bir simge listesi öğelerinden birini etiketinin `Text` özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, `if` deyimindeki son satır, forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz. [nasıl yapılır: Visual Studio 'Da hata ayıklayıcıyla adımla](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya daha fazla bilgi Için [hata ayıklayıcı Ile kod arasında geziniyor](../debugger/navigating-through-code-with-the-debugger.md) .

3. Oyun panosunu simgelerle doldurmanız için, program başladıktan hemen sonra `AssignIconsToSquares()` yöntemini çağırmanız gerekir. Visual C#kullanıyorsanız, `Form1`*oluşturucusunda*`InitializeComponent()` yöntemine yapılan çağrının hemen altına bir ifade ekleyin, böylece formunuz görüntülenmeden önce kendisini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Daha fazla bilgi için bkz. [oluşturucular (C# programlama kılavuzu)](https://msdn.microsoft.com/library/ace5hbzh.aspx) veya Visual Basic [oluşturucular ve Yıkıcılar kullanma](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) .

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Visual Basic için, `AssignIconsToSquares()` yöntemi çağrısını `Form1_Load` yöntemine ekleyerek kodun aşağıdaki gibi görünmesini sağlayın.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.

     ![Rastgele simgelerle eşleşen oyun](../ide/media/express-tut4step3.png "Express_Tut4Step3") Rastgele simgelerle eşleşen oyun

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları Player 'dan gizlemek için, her etiketin `Forecolor` özelliğini `BackColor` özelliğiyle aynı renge ayarlayabilirsiniz.

    > [!TIP]
    > Etiketler gibi denetimleri gizlemek için başka bir yöntem de **Visible** özelliğini `False` olarak ayarlamanıza olanak sağlar.

6. Simgeleri gizlemek için programı durdurun ve `For Each` döngüsünün içinde açıklamalı kod satırının açıklama işaretlerini kaldırın.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Menü çubuğunda, **Tümünü Kaydet** düğmesini seçerek programınızı kaydedin ve çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
