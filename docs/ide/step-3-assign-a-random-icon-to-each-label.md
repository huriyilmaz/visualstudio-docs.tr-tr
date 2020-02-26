---
title: '3\. Adım: her etikete rastgele bir simge atama'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 366f6d7a07d2f30b5b8110fb7dae7a2311fcce23
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579401"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3\. Adım: her etikete rastgele bir simge atama

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, bir `AssignIconsToSquares()` yöntemi kullanarak, simgeleri formunuzdaki etiket denetimlerine rastgele atayın.

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük vardır: `foreach` C# ve Visual Basic `For Each`. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs.Microsoft.com](../ide/media/docs-programming-language-control.png) için programlama dili denetimi ![

2. Önceki adımda gösterildiği gibi `AssignIconsToSquares()` yöntemini ekleyin. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz kodun hemen altına yerleştirebilirsiniz.

     Daha önce belirtildiği gibi, `AssignIconsToSquares()` yönteminde yeni bir şey vardır: içinde C# `foreach` döngüsü ve Visual Basic `For Each`. `For Each` döngüsünü aynı eylemi birden çok kez yapmak istediğiniz zaman kullanabilirsiniz. Bu durumda, aşağıdaki kodda açıklandığı gibi <xref:System.Windows.Forms.TableLayoutPanel>her etiket için aynı deyimleri yürütmek istersiniz. İlk satır, her denetimi bir kerede depolayan `control` adlı bir değişken oluşturur ve bu denetim, bu denetimde yürütülen Döngülerdeki deyimler vardır.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     `AssignIconsToSquares()` yöntemi TableLayoutPanel içindeki her etiket denetimi boyunca yinelenir ve her biri için aynı deyimleri yürütür. Bu deyimler [Adım 2: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz listeden rastgele bir simge çeker. (Bu nedenle, listedeki her bir simgenin ikisini de eklemiş olursunuz, bu nedenle rastgele etiket denetimlerine atanan bir çift simge vardır.)

     `foreach` veya `For Each` döngüsü içinde çalışan koda daha yakından bakın. Bu kod burada tekrar üretilmektedir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     İlk satır, **Denetim** değişkenini **iconLabel**adlı bir etikete dönüştürür. Bundan sonraki satır, dönüştürmenin çalıştığından emin olmak için kontrol eden bir `if` deyimidir. Dönüştürme işe alıyorsa, `if` deyimindeki deyimler çalıştırılır. (Önceki öğreticilerden hatırlayabileceğiniz gibi, belirttiğiniz herhangi bir koşulu değerlendirmek için `if` deyimleri kullanılır.) `if` deyimindeki ilk satır, simgeler listesindeki öğelerden birine karşılık gelen rastgele bir sayı içeren **rasgelenumber** adlı bir değişken oluşturur. Bunu yapmak için, daha önce oluşturduğunuz <xref:System.Random> nesnesinin <xref:System.Random.Next> yöntemini kullanır. `Next` yöntemi rastgele sayı döndürür. Bu satır, rastgele sayının seçim aralığını belirlemek için **simgeler** listesinin <xref:System.Collections.Generic.List%601.Count> özelliğini de kullanır. Sonraki satır, bir simge listesi öğelerinden birini etiketinin <xref:System.Windows.Forms.Label.Text> özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, `if` deyimindeki son satır, forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz. [nasıl yaparım?: Visual Studio 'daki hata ayıklayıcıyla adımla mı?](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya daha fazla bilgi için [hata ayıklayıcıyla birlikte kod içine gidin](../debugger/navigating-through-code-with-the-debugger.md) .

3. Oyun panosunu simgelerle doldurmanız için, program başladıktan hemen sonra `AssignIconsToSquares()` yöntemini çağırmanız gerekir. Kullanıyorsanız C#, **Form1**_kurucusundaki_`InitializeComponent()` yöntemine yapılan çağrının hemen altına bir ifade ekleyin, böylece formunuz gösterilmeden önce kendisini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Daha fazla bilgi için bkz. [oluşturucular (C# programlama kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya Visual Basic [oluşturucular ve Yıkıcılar kullanma](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) .

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Visual Basic için, `AssignIconsToSquares()` yöntemi çağrısını `Form1_Load` yöntemine ekleyerek kodun aşağıdaki gibi görünmesini sağlayın.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.

     Rastgele simgelerle eşleşen oyuna ![](../ide/media/express_tut4step3.png)<br/>
*Rastgele simgelerle eşleşen oyun*

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları Player 'dan gizlemek için, her etiketin **ForeColor** özelliğini **BackColor** özelliği ile aynı renge ayarlayabilirsiniz.

    > [!TIP]
    > Etiketler gibi denetimleri gizlemenin bir diğer yolu da **Visible** özelliğini **false**olarak ayarlamanıza olanak sağlar.

6. Simgeleri gizlemek için programı durdurun ve `For Each` döngüsünün içinde açıklamalı kod satırının açıklama işaretlerini kaldırın.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Menü çubuğunda, **Tümünü Kaydet** düğmesini seçerek programınızı kaydedin ve çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)** .

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
