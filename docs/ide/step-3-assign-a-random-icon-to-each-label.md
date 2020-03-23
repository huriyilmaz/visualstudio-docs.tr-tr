---
title: 'Adım 3: Her etikete rastgele bir simge atama'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579401"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Adım 3: Her etikete rastgele bir simge atama

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, bir `AssignIconsToSquares()` yöntem kullanarak simgeleri formunuzdaki Etiket denetimlerine rasgele atayın.

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar kelime `foreach` var: C# ve `For Each` Visual Basic'te. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)

2. Önceki `AssignIconsToSquares()` adımda gösterildiği gibi yöntemi ekleyin. Adım 2'ye eklediğiniz kodun hemen altına [koyabilirsiniz: Rastgele bir nesne ve simgelerin bir listesini ekleyin.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)

     Daha önce de belirtildiği gibi, yönteminizde `AssignIconsToSquares()` yeni `foreach` bir şey `For Each` var: C# ve Visual Basic'te bir döngü. Aynı eylemi `For Each` birden çok kez yapmak istediğinizde bir döngü kullanabilirsiniz. Bu durumda, aşağıdaki kodla açıklandığı gibi, her <xref:System.Windows.Forms.TableLayoutPanel>etiketiniz için aynı ifadeleri yürütmek istiyorsunuz. İlk satır, her denetimi `control` birer birer depolayan bir değişken oluştururken, bu denetim döngüde yürütülen ifadelere sahiptir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     Yöntem, `AssignIconsToSquares()` TableLayoutPanel'deki her etiket denetiminde yineler ve her biri için aynı deyimleri yürütür. Bu ifadeler Adım 2'ye eklediğiniz listeden rasgele bir simge [çeker: Rastgele nesne ve simgelerin bir listesini ekleyin.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md) (Bu nedenle, listedeki her simgeden iki sini dahil etmişsinizdir, bu nedenle rasgele Etiket denetimlerine atanmış bir dizi simge olacaktır.)

     `foreach` Veya `For Each` döngü içinde çalışan koda daha yakından bakın. Bu kod burada tekrar üretilmektedir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     İlk **satır, denetim** değişkenini **iconLabel**adlı bir etikete dönüştürür. Bundan sonraki satır, `if` dönüştürmenin çalıştığından emin olmak için denetleyen bir deyimdir. Dönüştürme işe yararsa, ekstredeki `if` ifadeler çalışır. (Önceki öğreticilerden hatırlayacağınız gibi, `if` deyim belirttiğiniz durumu değerlendirmek için kullanılır.) İfadedeki `if` ilk satır, simgeler listesindeki öğelerden birine karşılık gelen rasgele bir sayı içeren **randomNumber** adlı bir değişken oluşturur. Bunu yapmak için, <xref:System.Random.Next> daha önce <xref:System.Random> oluşturduğunuz nesnenin yöntemini kullanır. Yöntem `Next` rasgele sayıyı döndürür. Bu satır, <xref:System.Collections.Generic.List%601.Count> rasgele sayı seçmek için hangi aralığı belirlemek için **simgeler** listesinin özelliğini de kullanır. Sonraki satır, simge listesi öğelerinden birini <xref:System.Windows.Forms.Label.Text> etiketin özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, deyimdeki `if` son satır, forma eklenen simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Bkz. [Nasıl Yapabilirim: Visual Studio'da hata ayıklayıcıyla adım atın](https://msdn.microsoft.com/vstudio/ee672313.aspx) veya daha fazla bilgi için hata [ayıklayıcıyla kod da gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

3. Oyun tahtasını simgelerle doldurmak için, program `AssignIconsToSquares()` başlar başlamaz yöntemi aramanız gerekir. C# kullanıyorsanız, `InitializeComponent()` **Form1**_oluşturucusundaki_yönteme çağrının hemen altına bir ifade ekleyin, böylece formunuz gösterilmeden önce kendisini ayarlamak için yeni yönteminizi çağırır. Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Daha fazla bilgi için Visual Basic'te [Oluşturucular (C# programlama kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya [kurucuları ve yıkıcıları kullanın.](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\))

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Visual Basic için, `AssignIconsToSquares()` yöntem çağrısını yönteme `Form1_Load` ekleyin, böylece kod aşağıdaki gibi görünür.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin.

     ![Rasgele simgeleri içeren eşleştirme oyunu](../ide/media/express_tut4step3.png)<br/>
*Rasgele simgeleri içeren eşleştirme oyunu*

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları oyuncudan gizlemek için, her etiketin **ForeColor** özelliğini **BackColor** özelliğiyle aynı renge ayarlayabilirsiniz.

    > [!TIP]
    > Denetimleri etiketler gibi gizlemenin başka bir yolu da **Görünür** özelliğini **False**olarak ayarlamaktır.

6. Simgeleri gizlemek için programı durdurun ve `For Each` döngü içindeki yorum kodu satırının yorum işaretlerini kaldırın.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Menü çubuğunda, programınızı kaydetmek için **Tümlerini Kaydet** düğmesini seçin ve ardından çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 4: Her etikete bir tıklama olay işleyicisi ekleyin.](../ide/step-4-add-a-click-event-handler-to-each-label.md)**

- Önceki öğretici adıma dönmek için [bkz: Adım 2: Rastgele nesne ve simgelerin listesini ekleyin.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)
