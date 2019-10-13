---
title: '3\. adım: Her etikete rastgele bir simge atama'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a670ec4b5b6689c68820b37b20a4e1a942dc3bd
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289615"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3\. adım: Her etikete rastgele bir simge atama
Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, `AssignIconsToSquares()` yöntemi kullanarak, simgeleri formunuzdaki etiket denetimlerine rastgele atayın.

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük vardır: Visual C# 'te `foreach` ve Visual Basic `For Each`. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs. Microsoft. com @ no__t-1 için ![Programlama dil denetimi

2. Önceki adımda gösterildiği gibi `AssignIconsToSquares()` yöntemini ekleyin. @No__t-0Adım 2 ' de eklediğiniz kodun hemen altına yerleştirebilirsiniz: Rastgele bir nesne ve simge listesi ekleyin @ no__t-0.

     Daha önce belirtildiği gibi, `AssignIconsToSquares()` yönteminde yeni bir şey vardır: Visual C# 'te `foreach` döngüsü ve Visual Basic `For Each`. @No__t-0 döngüsünü aynı eylemi birden çok kez yapmak istediğiniz zaman kullanabilirsiniz. Bu durumda, aşağıdaki kodda açıklandığı gibi <xref:System.Windows.Forms.TableLayoutPanel> ' daki her etiket için aynı deyimleri yürütmek istersiniz. İlk satır, her denetimi bir kerede depolayan `control` adlı bir değişken oluşturur ve bu denetim, bu denetimde yürütülen Döngülerdeki deyimler vardır.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     @No__t-0 yöntemi, TableLayoutPanel içindeki her etiket denetimi boyunca yinelenir ve her biri için aynı deyimleri yürütür. Bu deyimler [Adım 2 ' de eklediğiniz listeden rastgele bir simge çeker: Rastgele bir nesne ve simge listesi ekleyin @ no__t-0. (Bu nedenle, listedeki her bir simgenin ikisini de eklemiş olursunuz, bu nedenle rastgele etiket denetimlerine atanan bir çift simge vardır.)

     @No__t-0 veya `For Each` döngüsü içinde çalışan koda daha yakından bakın. Bu kod burada tekrar üretilmektedir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     İlk satır, **Denetim** değişkenini **iconLabel**adlı bir etikete dönüştürür. Bundan sonraki satır, dönüştürmenin çalıştığından emin olmak için denetleyen `if` deyimidir. Dönüştürme işe alıyorsa, `if` deyimindeki deyimler çalıştırılır. (Önceki öğreticilerden hatırlayabileceğiniz gibi, belirttiğiniz koşulu değerlendirmek için `if` açıklaması kullanılır.) @No__t-0 deyimindeki ilk satır, simgeler listesindeki öğelerden birine karşılık gelen rastgele bir sayı içeren **rasgelenumber** adlı bir değişken oluşturur. Bunu yapmak için, daha önce oluşturduğunuz <xref:System.Random> nesnesinin <xref:System.Random.Next> yöntemini kullanır. @No__t-0 yöntemi rastgele sayı döndürür. Bu satır, rastgele sayının seçim aralığını belirlemek için **simgeler** listesinin <xref:System.Collections.Generic.List%601.Count> özelliğini de kullanır. Sonraki satır, bir simge listesi öğelerinden birini etiketin <xref:System.Windows.Forms.Label.Text> özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, `if` deyimindeki son satır, forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz. [Nasıl yapılır: Visual Studio 'daki hata ayıklayıcıyla adımla mı? ](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya daha fazla bilgi için [hata ayıklayıcıyla birlikte kod üzerinden ilerleyin](../debugger/navigating-through-code-with-the-debugger.md) .

3. Oyun panosunu simgelerle doldurmanız için, program başladıktan hemen sonra `AssignIconsToSquares()` yöntemini çağırmanız gerekir. Görsel C#kullanıyorsanız, **Form1**_oluşturucusunda_`InitializeComponent()` yöntemine yapılan çağrının hemen altına bir ifade ekleyin, böylece formunuz görüntülenmeden önce kendisini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Daha fazla bilgi için bkz. [oluşturucular (C# programlama kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya Visual Basic [oluşturucular ve Yıkıcılar kullanma](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) .

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Visual Basic için, `AssignIconsToSquares()` yöntem çağrısını `Form1_Load` yöntemine ekleyerek kodun aşağıdaki gibi görünmesini sağlayın.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.

     Rastgele simgelerle ![ ile eşleşen oyun, rastgele simgelerle eşleşen oyun @ no__t-1

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları Player 'dan gizlemek için, her etiketin **ForeColor** özelliğini **BackColor** özelliği ile aynı renge ayarlayabilirsiniz.

    > [!TIP]
    > Etiketler gibi denetimleri gizlemenin bir diğer yolu da **Visible** özelliğini **false**olarak ayarlamanıza olanak sağlar.

6. Simgeleri gizlemek için programı durdurun ve `For Each` döngüsü içindeki açıklamalı kod satırının açıklama işaretlerini kaldırın.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Menü çubuğunda, **Tümünü Kaydet** düğmesini seçerek programınızı kaydedin ve çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Adım 4: Her etikete bir tıklama olayı işleyicisi ekleyin @ no__t-0.

- Önceki öğretici adımına dönmek için bkz. [Step 2: Rastgele bir nesne ve simge listesi ekleyin @ no__t-0.
