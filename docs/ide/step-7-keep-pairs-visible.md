---
title: '7. Adım: Çiftleri görünür durumda tutma'
description: Bir if ifadesinin nasıl ekleneceğini öğrenin. bu nedenle, oynatıcı eşleşen bir simge çifti seçtiğinde simgeler görünür kalır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc61a59d1e04d96fb36e7a7e4cd1304e2057adb
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479452"
---
# <a name="step-7-keep-pairs-visible"></a>7. Adım: Çiftleri görünür durumda tutma
Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Zamanlayıcıyı etkinleştirerek (yöntemi kullanarak) simgeleri ortadan <xref:System.Windows.Forms.Timer.Start> kaldırmamak yerine, oyunun kendisini sıfırlaması gerekir; böylece, `firstClicked` `secondClicked` Seçilen iki etiket için renkleri sıfırlamadan, ve başvuru değişkenlerini kullanarak hiçbir etiketi izlememek üzere.

## <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1. Aşağıdaki ifadeyi, `if` `label_Click()` süreölçer 'i başlattığınız deyimin hemen üstündeki kodun sonuna yakın şekilde olay işleyicisi yöntemine ekleyin. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     > [!IMPORTANT]
     > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

     Az önce eklediğiniz deyimin ilk satırı, `if` Player 'ın seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler. Simgeler aynıysa, program C# içindeki küme ayraçları veya Visual Basic içindeki deyimde yer alan üç deyim arasında üç deyimi yürütür `if` . İlk iki deyim, `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar, böylece artık etiketlerden herhangi birini takip etmezsiniz. (Bu iki deyimi zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinden ayırt edebilirsiniz.) Üçüncü deyim, `return` programa onları yürütmeden, yöntemi içindeki deyimlerin geri kalanını atlamasını söyleyen bir deyimidir.

     C# dilinde programlama yaparsanız, bazı kodların tek bir eşittir işareti () kullandığını fark etmiş olabilirsiniz `=` , ancak diğer deyimler iki eşittir işareti ( `==` ) kullanır. Neden `=` bazı yerlerde kullanıldığına, ancak `==` diğer yerlerde kullanıldığına göz önünde bulundurun.

     Bu örnek, aradaki farkı gösteren güzel bir örnektir. Deyimdeki parantez arasındaki koda dikkatli bir göz atın `if` .

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Ardından, deyimden sonra kod bloğundaki ilk ifadeye yakından bakın `if` .

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. İki değer karşılaştırıldığından, C# programı `==` eşitlik işlecini kullanır. İkinci ifade gerçekten değeri değiştirir ( *atama* olarak adlandırılır), `firstClicked` başvuru değişkenini sıfırlamak için değerine eşit olarak ayarlar `null` . `=`Bunun yerine atama işlecini kullanmasının nedeni budur. C# `=` , değerleri ayarlamak ve `==` karşılaştırmak için kullanır. Visual Basic `=` , hem değişken atama hem de karşılaştırma için kullanır.

2. Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz, yeni `if` ifade yürütülür ve Return deyimleri, aşağıdaki görüntüde gösterildiği gibi, simgenin görünür kalması için, bu yöntemin zamanlayıcıyı başlatan kodu atlamasına neden olur.

     ![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)<br/>
***Eşleşen oyun** _ _with görünür simge çiftleri *

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 8. **[Adım: oyuncunun kazandığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**.

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).
