---
title: '7\. Adım: çiftleri görünür tutma'
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
ms.openlocfilehash: 60b058883e30587ed656690796732b15750b6277
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647441"
---
# <a name="step-7-keep-pairs-visible"></a>7\. Adım: çiftleri görünür tutma
Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Zamanlayıcıyı etkinleştirerek (<xref:System.Windows.Forms.Timer.Start> yöntemi kullanılarak) simgeleri ortadan kaldırmamak yerine, oyunun kendisini sıfırlamasına gerek kalmadan, `firstClicked` ve `secondClicked` başvuru değişkenlerini kullanarak hiçbir etiketi takip etmeden önce Seçilen Etiketler.

## <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1. Aşağıdaki `if` ifadesini, süreölçeri başlattığınız deyimin hemen üstündeki kodun sonuna yakın olan `label_Click()` olay işleyicisi yöntemine ekleyin. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Yeni eklediğiniz `if` deyimin ilk satırı, Player 'ın seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler. Simgeler aynıysa, program içindeki C# küme ayraçları veya Visual Basic içindeki `if` deyimi arasındaki üç deyimi yürütür. İlk iki deyim `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlayın ve bu sayede etiketlerin hiçbirini izlememek üzere. (Bu iki deyimi zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinden ayırt edebilirsiniz.) Üçüncü deyim bir `return` deyimidir, bu da programa çalıştırmadan deyimlerin geri kalanını atlamasını söyler.

     İçinde C#Programlama yapıyorsanız, bazı kodların tek bir eşittir işareti (`=`) kullandığını fark etmiş olabilirsiniz, ancak diğer deyimler iki eşittir işareti (`==`) kullanır. @No__t_0 neden bazı yerlerde kullanıldığını, ancak `==` başka yerlerde kullanıldığını göz önünde bulundurun.

     Bu örnek, aradaki farkı gösteren güzel bir örnektir. @No__t_0 deyimindeki parantezler arasındaki koda dikkatli bir göz atın.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Ardından `if` deyimden sonra kod bloğundaki ilk ifadeye yakından bakın.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. İki değer karşılaştırıldığından, C# program `==` eşitlik işlecini kullanır. İkinci ifade gerçekten değeri değiştirir ( *atama*olarak adlandırılır), `firstClicked` başvuru değişkenini sıfırlamak için `null` eşittir. Bunun yerine `=` atama işlecini kullanmasıdır. C#değerleri ayarlamak için `=` kullanır ve bunları karşılaştırmak için `==`. Visual Basic, hem değişken atama hem de karşılaştırma için `=` kullanır.

2. Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz, yeni `if` deyimleri yürütülür ve Return deyimleri, aşağıdaki görüntüde gösterildiği gibi, simgenin görünür kalması için, metodun zamanlayıcıyı başlatan kodu atlamasına neden olur.

     Bu öğreticide oluşturduğunuz ![Game ](../ide/media/express_finishedgame.png)<br/>
*Görünür simge çiftleri Ile* ***eşleşen oyun***

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 8. **[Adım: oyuncunun kazandığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)** .

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).
