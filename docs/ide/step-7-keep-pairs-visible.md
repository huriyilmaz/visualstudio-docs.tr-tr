---
title: '7\. Adım: Çiftleri görünür durumda tutma'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 025e388185651e6b2effb0f53345f2e145e101b3
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289598"
---
# <a name="step-7-keep-pairs-visible"></a>7\. Adım: Çiftleri görünür durumda tutma
Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Zamanlayıcıyı etkinleştirerek (<xref:System.Windows.Forms.Timer.Start> yöntemini kullanarak) simgeleri ortadan kaldırmamak yerine, oyunun kendisini sıfırlaması gerekir; böylece, iki için renkleri sıfırlamadan, `firstClicked` ve `secondClicked` başvuru değişkenlerini kullanarak hiçbir etiketi takip etmeden önce Seçilen Etiketler.

## <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1. Aşağıdaki `if` ifadesini, süreölçeri başlattığınız deyimin hemen üstündeki kodun sonuna yakın olan `label_Click()` olay işleyicisi yöntemine ekleyin. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Yeni eklediğiniz `if` ifadesinin ilk satırı, Player 'ın seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler. Simgeler aynıysa program, içindeki C# küme ayraçları arasında üç deyimi veya Visual Basic `if` deyimi içindeki üç deyimi yürütür. İlk iki deyim `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlayın, böylece artık etiketlerden herhangi birini takip etmezsiniz. (Bu iki deyimi zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinden ayırt edebilirsiniz.) Üçüncü deyim bir `return` deyimidir, bu da programa çalıştırmadan deyimlerin geri kalanını atlamasını söyler.

     Görselde C#programlamada, bazı kodların tek bir eşittir işareti (`=`) kullandığını fark etmiş olabilirsiniz; diğer deyimler ise iki eşittir işareti (`==`) kullanır. @No__t-0 ' ın bazı konumlarda kullanıldığını, ancak `==` ' in diğer yerlerde kullanıldığını göz önünde bulundurun.

     Bu örnek, aradaki farkı gösteren güzel bir örnektir. @No__t-0 deyimindeki parantezler arasındaki koda dikkatli bir göz atın.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Ardından `if` ifadesinden sonra kod bloğundaki ilk ifadeye yakından bakın.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. İki değer karşılaştırıldığından, görsel C# program `==` eşitlik işlecini kullanır. İkinci ifade gerçekten değeri değiştirir ( *atama*olarak adlandırılır), `firstClicked` başvuru değişkeni, `null` ' ye eşit olarak ayarlanır. Bunun yerine `=` atama işlecini kullanmasının nedeni budur. Visual C# , değerleri ayarlamak için `=` kullanır ve karşılaştırmak için 2 @no__t. Visual Basic, hem değişken atama hem de karşılaştırma için `=` kullanır.

2. Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz, yeni `if` deyimleri yürütülür ve Return yöntemi yöntemin zamanlayıcıyı başlatan kodu atlamasına neden olur, böylece aşağıdaki resimde gösterildiği gibi simgeler görünür kalır.

     Bu öğreticide oluşturduğunuz ![Game @ no__t-1<br/>
Görünür simge çiftleri ile **eşleşen oyun**

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Adım 8: Oynatıcının @ no__t-0 olarak kazanıldığını doğrulamak için bir yöntem ekleyin.

- Önceki öğretici adımına dönmek için bkz. [Step 6: Bir süreölçer ekleyin @ no__t-0.
