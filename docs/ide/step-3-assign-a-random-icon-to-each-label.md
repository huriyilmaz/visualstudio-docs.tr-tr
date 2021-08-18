---
title: '3. Adım: Her etikete rastgele bir simge atama'
description: Simgelerin her oyunda aynı hücrelerde gösterilmemesi için her etikete rastgele bir simge atamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/21/2020
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ecd824bcfe1fad320f42c8240530c0d480975c12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132073"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3. Adım: Her etikete rastgele bir simge atama

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, bir yöntemi kullanarak simgeleri formunuzdaki etiket denetimlerine rastgele atayın `AssignIconsToSquares()` .

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük vardır: `foreach` C# içinde ve `For Each` Visual Basic. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet2":::

      > [!IMPORTANT]
      > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

2. Yöntemi, `AssignIconsToSquares()` önceki adımda gösterildiği gibi ekleyin. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz kodun hemen altına yerleştirebilirsiniz.

     Daha önce bahsedildiği gibi, `AssignIconsToSquares()` yöntegende yeni bir şey vardır: `foreach` C# ve `For Each` Visual Basic. Bir `For Each` döngüyü, aynı eylemi birden çok kez yapmak istediğiniz zaman kullanabilirsiniz. Bu durumda, <xref:System.Windows.Forms.TableLayoutPanel> aşağıdaki kodda açıklandığı gibi, içindeki her etiket için aynı deyimleri yürütmek istersiniz. İlk satır, `control` her denetimi bir kez depolayan adlı bir değişken oluşturur ve bu denetim, üzerinde yürütülen deyimlerdeki deyimler vardır.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet14":::

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     `AssignIconsToSquares()`Yöntemi TableLayoutPanel içindeki her etiket denetimi boyunca yinelenir ve her biri için aynı deyimleri yürütür. Bu deyimler [Adım 2: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)bölümünde eklediğiniz listeden rastgele bir simge çeker. Bir anımsatıcı olarak, bu simgelerin her biri, bu yöntemde metin olarak ifade edilmesinin nedeni olan Webedilecek yazı tipinde bir harftir. Rastgele etiket denetimlerine atanmış bir simge çifti olacak şekilde, listedeki her bir simgenin ikisini de eklemiş olursunuz.

     Veya döngüsünün içinde çalışan koda daha yakından bakın `foreach` `For Each` . Bu kod burada tekrar üretilmektedir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet16":::

     İlk satır, **Denetim** değişkenini **iconLabel** adlı bir etikete dönüştürür. Bundan sonraki satır, `if` dönüştürmenin çalıştığından emin olmak için denetleyen bir ifadedir. Dönüştürme işe alıyorsa, `if` deyimindeki deyimler çalışır. (Önceki öğreticilerden hatırlayabileceğiniz gibi, `if` ifade belirttiğiniz koşulu değerlendirmek için kullanılır.) Deyimdeki ilk satır, `if` simgeler listesindeki öğelerden birine karşılık gelen rastgele bir sayı Içeren **rasgelenumber** adlı bir değişken oluşturur. Bunu yapmak için, <xref:System.Random.Next> <xref:System.Random> daha önce oluşturduğunuz nesnenin yöntemini kullanır. `Next`Yöntemi rastgele sayı döndürür. Bu satır, <xref:System.Collections.Generic.List%601.Count> rastgele sayının seçim aralığını belirlemek için **simgeler** listesinin özelliğini de kullanır. Sonraki satır, simge listesi öğelerinden birini <xref:System.Windows.Forms.Label.Text> etiketin özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, deyimindeki son satır, `if` forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. [Nasıl yaparım?: Visual Studio hata ayıklayıcıyla adımla](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya daha fazla bilgi için [hata ayıklayıcıyla kod içinde gezinin](../debugger/navigating-through-code-with-the-debugger.md) .

3. Oyun panosunu simgelerle doldurmanız için `AssignIconsToSquares()` Program başlatıldıktan hemen sonra yöntemi çağırmanız gerekir. C# kullanıyorsanız, Form1 oluşturucusunda yöntemine yapılan çağrının hemen altına bir ifade ekleyin `InitializeComponent()` , böylece formunuz görüntülenmeden önce  kendisini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. daha fazla bilgi için bkz. [oluşturucular (C# programlama kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya Visual Basic [oluşturucular ve yıkıcılar kullanın](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet13":::

     Visual Basic için yöntemine `AssignIconsToSquares()` yöntem çağrısını ekleyerek `Form1_Load` kodun aşağıdaki gibi görünmesini sağlayın.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir. 

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin. 

     ![Rasgele simgeleri içeren eşleştirme oyunu](../ide/media/express_tut4step3.png)<br/>
*Rasgele simgeleri içeren eşleştirme oyunu*

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları Player 'dan gizlemek için, her etiketin **ForeColor** özelliğini **BackColor** özelliği ile aynı renge ayarlayabilirsiniz.

6. Simgeleri gizlemek için programı durdurun ve döngü içindeki açıklamalı kod satırının açıklama işaretlerini kaldırın `For Each` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet15":::

7. Menü çubuğunda, **Tümünü Kaydet** düğmesini seçerek programınızı kaydedin ve çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. **[Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Önceki öğretici adımına dönmek için bkz. 2. [Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
