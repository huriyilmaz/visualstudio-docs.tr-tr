---
title: '7. Adım: çiftleri görünür tutma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d7981ca81839cc8d0959cf5ae75c6d9a001d39a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646941"
---
# <a name="step-7-keep-pairs-visible"></a>7. Adım: Çiftleri Görünür Kılma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Zamanlayıcıyı etkinleştirerek (yöntemi kullanarak) simgeleri ortadan `Start()` kaldırmamak yerine, oyunun kendisini sıfırlaması gerekir; böylece, `firstClicked` `secondClicked` Seçilen iki etiket için renkleri sıfırlamadan, ve başvuru değişkenlerini kullanarak hiçbir etiketi izlememek üzere.

### <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1. Aşağıdaki ifadeyi, `if` `label_Click()` süreölçer 'i başlattığınız deyimin hemen üstündeki kodun sonuna yakın şekilde olay işleyicisi yöntemine ekleyin. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]

     Az önce eklediğiniz deyimin ilk satırı, `if` Player 'ın seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler. Simgeler aynıysa, program C# içindeki küme ayraçları veya Visual Basic içindeki deyimde yer alan üç deyim arasında üç deyimi yürütür `if` . İlk iki deyim, `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar, böylece artık etiketlerden herhangi birini takip etmezsiniz. (Bu iki deyimi zamanlayıcının Tick olay işleyicisinden ayırt edebilirsiniz.) Üçüncü deyim, `return` programa onları yürütmeden, yöntemi içindeki deyimlerin geri kalanını atlamasını söyleyen bir deyimidir.

     Visual C# ' de programlıyorsanız, bazı kodların tek bir eşittir işareti () kullandığını fark etmiş olabilirsiniz `=` , ancak diğer deyimler iki eşittir işareti ( `==` ) kullanır. Neden `=` bazı yerlerde kullanıldığına, ancak `==` diğer yerlerde kullanıldığına göz önünde bulundurun.

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

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. İki değer karşılaştırıldığından, Visual C# programı `==` eşitlik işlecini kullanır. İkinci ifade gerçekten değeri değiştirir ( *atama*olarak adlandırılır), `firstClicked` başvuru değişkenini sıfırlamak için değerine eşit olarak ayarlar `null` . `=`Bunun yerine atama işlecini kullanmasının nedeni budur. Visual C# `=` , değerleri ayarlamak ve `==` karşılaştırmak için kullanır. Visual Basic `=` , hem değişken atama hem de karşılaştırma için kullanır.

2. Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz, yeni `if` ifade yürütülür ve Return deyimleri, aşağıdaki resimde gösterildiği gibi, simgenin görünür kalması için, bu yöntemin zamanlayıcıyı başlatan kodu atlamasına neden olur.

     ![Bu öğreticide oluşturduğunuz oyun](../ide/media/express-finishedgame.png "Express_FinishedGame") Görünür simge çiftleri ile eşleşen oyun

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 8. [Adım: oyuncunun kazandığını doğrulamak Için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).
