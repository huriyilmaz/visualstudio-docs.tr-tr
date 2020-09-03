---
title: '5. Adım: etiket başvuruları ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671735"
---
# <a name="step-5-add-label-references"></a>5. Adım: Etiket Başvuruları Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programın, oyuncunun seçtiği etiket kontrollerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık ilk olarak hangi etiket denetiminin seçili olduğunu ve *başvuru değişkenlerini*kullanarak ikinci seçili olduğunu izler.

### <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Bu başvuru değişkenleri formunuza nesneleri eklemek için ( `Timer` nesneler, `List` nesneler ve nesneler gibi), daha önce kullandığınız deyimlere benzer şekilde görünür `Random` . Ancak, `new` iki deyimden birinde anahtar sözcük kullanılmadığından, bu deyimler formda iki ek etiket denetiminin görünmesine neden olmaz. `new`Anahtar sözcüğü olmadan hiçbir nesne oluşturulmaz. `firstClicked`Bunun nedeni ve `secondClicked` başvuru değişkenleri olarak adlandırılmaları gerekir: yalnızca izleme (veya, başvuru) nesnelerini takip eder `Label` .

     Bir değişken bir nesneyi izlememediğinde, özel bir ayrılmış değere ayarlanır: `null` Visual C# ve `Nothing` Visual Basic. Bu nedenle, program başlatıldığında `firstClicked` ve ya da olarak ayarlanır; bu da `secondClicked` `null` `Nothing` değişkenlerin herhangi bir şeyi izlememediği anlamına gelir.

2. Click olay işleyicinizi yeni başvuru değişkenini kullanacak şekilde değiştirin `firstClicked` . `label_Click()`Olay işleyicisi yönteminde () son ifadeyi kaldırın `clickedLabel.ForeColor = Color.Black;` ve bunu `if` takip eden deyimle değiştirin. (Yorumu ve tüm deyimin dahil ettiğinizden emin olun `if` .)

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program, Player 'ın seçtiği ilk etiketi zaten tutuyor, bu yüzden `firstClicked` `null` Visual C# veya Visual Basic ile eşit değildir `Nothing` . `if`Deyiminiz `firstClicked` veya ' a eşit olup olmadığını belirlemeyi denetlediğinde, olmadığını `null` `Nothing` bulur ve `if` deyimdeki deyimleri yürütmez. Bu nedenle, aşağıdaki resimde gösterildiği gibi, yalnızca seçilen ilk simgenin rengi siyah olur ve diğer simgeler görünmez.

     ![Eşleşen oyun bir simge gösteriyor](../ide/media/express-tut4step5.png "Express_Tut4Step5") Eşleşen oyun bir simge gösteriyor

     Bu durumu, bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında düzeltireceksiniz.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 6. [Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).

- Önceki öğretici adımına dönmek için, bkz. [Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).
