---
title: '3. Adım: Her etikete rastgele bir simge atama'
description: Simgelerin her oyun için aynı hücrelerde gösterilene kadar her etikete rastgele bir simge atamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/21/2020
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 10d72dac4fd4e5f636076dca88af67e3b7a9053f
ms.sourcegitcommit: 5178819f49bb92995bca5c90c90e5fc5a1e04681
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2021
ms.locfileid: "134938249"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>3. Adım: Her etikete rastgele bir simge atama

Simgeler her oyunda aynı hücrelerde gösterilirse, oyun pek de zorlu olmaz. Bunu önlemek için, bir yöntem kullanarak simgeleri formuzda Etiket denetimlerine rastgele `AssignIconsToSquares()` attayabilirsiniz.

## <a name="to-assign-a-random-icon-to-each-label"></a>Her etikete rasgele bir simge atamak için

1. Aşağıdaki kodu eklemeden önce yöntemin nasıl çalıştığını düşünün. Yeni bir anahtar sözcük var: `foreach` C# ve `For Each` Visual Basic. (Satırlardan biri bilerek derleme dışı bırakılmıştır; bunun nedeni bu yordamın sonunda açıklanmaktadır.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet2":::

      > [!IMPORTANT]
      > C# kod parçacığını veya kod parçacığını görüntülemek için bu sayfanın sağ üst kısmında yer alan programlama dili Visual Basic kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

2. Önceki `AssignIconsToSquares()` adımda gösterildiği gibi yöntemini ekleyin. Bunu 2. Adım: Rastgele nesne ve simge listesi ekleme adımlarında ekley istediğiniz [kodun hemen altına koyabilirsiniz.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)

     Daha önce belirtildiği gibi yönteminde yeni bir şey `AssignIconsToSquares()` vardır: `foreach` C# döngüsü ve `For Each` Visual Basic. Bir `For Each` döngüyü, aynı eylemi birden çok kez yapmak istediğiniz zaman kullanabilirsiniz. Bu durumda, aşağıdaki kodda açıklanan şekilde , dosyanız üzerinde her etiket <xref:System.Windows.Forms.TableLayoutPanel> için aynı deyimleri yürütmek istiyor. İlk satır, denetimin üzerinde yürütülen döngüde deyimleri varken her denetimi tek tek depolar adlı `control` bir değişken oluşturur.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet14":::

    > [!NOTE]
    > "iconLabel" (simge etiketi) ve "control" (denetim) kullanılmasının nedeni bu adların açıklayıcı olmasıdır. Bu adların yerine istediğiniz adları kullanabilirsiniz; ilgili adı döngüdeki her bir deyimde de değiştirdiğiniz sürece kod tamamen aynı şekilde çalışacaktır.

     yöntemi TableLayoutPanel'daki her etiket denetiminde yineler ve her biri `AssignIconsToSquares()` için aynı deyimleri yürütür. Bu deyimler, [2. Adım:](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)Rastgele nesne ve simge listesi ekleyin. Anımsatıcı olarak, bu simgelerin her biri Webdings yazı tipinde bir harftir ve bu nedenle bu yöntemde metin olarak ifade edildi. Rastgele Etiket denetimlerine atanmış bir simge çifti olması için her simgeden iki tane listeye dahil edildi.

     veya döngüsü içinde çalışan koda daha yakından `foreach` `For Each` bakın. Bu kod burada tekrar üretilmektedir.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet16":::

     İlk satır denetim **değişkenini** iconLabel adlı bir **etikete dönüştürür.** Bundan sonra gelen satır, `if` dönüştürmenin çalışa olduğundan emin olmak için denetimi yapılan bir deyimdir. Dönüştürme işe olursa deyiminde deyimleri `if` çalışır. (Önceki öğreticilerden hatırlayarak belirttiğiniz koşulu değerlendirmek için `if` deyimi kullanılmıştır.) deyiminin ilk satırı, simgeler listesinde yer alan öğelerden birini karşılık gelen rastgele bir sayı içeren `if` **randomNumber** adlı bir değişken oluşturur. Bunu yapmak için daha <xref:System.Random.Next> önce oluşturduğunuz <xref:System.Random> nesnesinin yöntemini kullanır. yöntemi `Next` rastgele s numarayı döndürür. Bu satır ayrıca rastgele <xref:System.Collections.Generic.List%601.Count> sayıyı **seçmek** istediğiniz aralığı belirlemek için simgeler listesinin özelliğini kullanır. Sonraki satır, simge listesi öğelerilerinden birini <xref:System.Windows.Forms.Label.Text> etiketin özelliğine atar. Derleme dışı bırakılan satır bu konunun sonunda açıklanmaktadır. Son olarak, deyiminin `if` son satırı forma eklenmiş olan simgeyi listeden kaldırır.

     Kodun belirli bir bölümünün ne işe yaradığından emin olamadığınızda, fare işaretçisini kod öğesinin üzerine getirip ortaya çıkan araç ipucunu gözden geçirebileceğinizi unutmayın. Ayrıca, Visual Studio hata ayıklayıcısını kullanarak, program çalışırken kodun her satırını adım adım geçebilirsiniz. Daha [fazla Nasıl yaparım? için Bkz.](https://msdn.microsoft.com/vstudio/ee672313.aspx) hata ayıklayıcıda hata Visual Studio ile adım adım? veya Hata [ayıklayıcı ile](../debugger/navigating-through-code-with-the-debugger.md) kodda gezinme.

3. Oyun panosuna simgeler doldurmak için program başlar `AssignIconsToSquares()` başlamaz yöntemini çağırmanız gerekir. C# kullanıyorsanız Form1 oluşturucus unda yöntemine yapılan çağrının hemen altına bir deyimi ekleyin. Bu nedenle form, gösterilmeden önce yeni yönteminizi çağırarak kendisini `InitializeComponent()` ayarlamasını sağlar.   Oluşturucular, sınıf veya yapı gibi yeni bir nesne oluşturduğunuzda çağrılır. Daha fazla bilgi için bkz. [](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) Oluşturucular [(C#](/dotnet/csharp/programming-guide/classes-and-structs/constructors) programlama kılavuzu) veya Visual Basic ve yıkıcıları kullanma.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet13":::

     Daha Visual Basic `AssignIconsToSquares()` için, kodun aşağıdaki gibi `Form1_Load` görünüyor şekilde yöntemine yöntemini ekleyin.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir. 
   
   Webdings simgeleri formda düzgün görüntülenmezse, formda etiketlerin **UseCompatibleTextRendering** özelliğini True olarak **ayarlayın.**

5. Programınızı kapatın ve yeniden çalıştırın. Aşağıdaki resimde gösterildiği gibi, her etikete farklı simgeler atandığına dikkat edin. 

     ![Rasgele simgeleri içeren eşleştirme oyunu](../ide/media/express_tut4step3.png)<br/>
*Rasgele simgeleri içeren eşleştirme oyunu*

     Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları oynatıcıdan gizlemek için, her etiketin **ForeColor** özelliğini BackColor özelliğiyle aynı renge **ayarlayın.**

6. Simgeleri gizlemek için programı durdurun ve döngü içindeki açıklama satırına yönelik açıklama işaretlerini `For Each` kaldırın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet15":::

7. Menü çubuğunda, programınızı **kaydetmek için** Hepsini Kaydet düğmesini seçin ve ardından çalıştırın. Simgelerin kaybolduğu görülür ve yalnızca mavi bir arka plan görüntülenir. Bununla birlikte simgeler rasgele atanırlar ve halen oradadırlar. Simgeler arka plan ile aynı renkte olduğundan, oyuncudan gizlenmiş olurlar. Sonuçta, oyuncu simgelerin tümünü doğrudan görebilseydi hiç de zorlayıcı bir oyun olmazdı!

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 4. Adım: Her etikete bir tıklama olayı işleyicisi ekleme.](../ide/step-4-add-a-click-event-handler-to-each-label.md)**

- Önceki öğretici adımına dönmek için [bkz. 2. Adım: Rastgele nesne ve simge listesi ekleme.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)
