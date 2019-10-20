---
title: '5\. Adım: etiket başvuruları ekleme | Microsoft Docs'
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671735"
---
# <a name="step-5-add-label-references"></a>5\. Adım: Etiket Başvuruları Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programın, oyuncunun seçtiği etiket kontrollerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık ilk olarak hangi etiket denetiminin seçili olduğunu ve *başvuru değişkenlerini*kullanarak ikinci seçili olduğunu izler.

### <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Bu başvuru değişkenleri formunuza nesneleri eklemek için (`Timer` nesneleri, `List` nesneleri ve `Random` nesneleri gibi), daha önce kullandığınız deyimlere benzer şekilde görünür. Ancak, bu deyimler iki deyimden birinde kullanılan `new` anahtar sözcük olmadığından, formda iki ek etiket denetiminin görünmesine neden olmaz. @No__t_0 anahtar sözcüğü olmadan hiçbir nesne oluşturulmaz. @No__t_0 ve `secondClicked` başvuru değişkenleri olarak adlandırılmaktadır: `Label` nesneleri yalnızca izleme (veya, başvuru) olarak saklar.

     Bir değişken bir nesneyi izlememediğinde, özel bir ayrılmış değere ayarlanır: görsel C# `null` ve Visual Basic `Nothing`. Bu nedenle, program başlatıldığında `firstClicked` ve `secondClicked` `null` veya `Nothing` olarak ayarlanır, bu da değişkenlerin herhangi bir şeyi izlememediği anlamına gelir.

2. Click olay işleyicinizi yeni `firstClicked` başvuru değişkenini kullanacak şekilde değiştirin. @No__t_0 olay işleyicisi yönteminde (`clickedLabel.ForeColor = Color.Black;`) son ifadeyi kaldırın ve bunu izleyen `if` ifadesiyle değiştirin. (Yorumu ve tüm `if` deyiminizi eklediğinizden emin olun.)

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program, Player 'ın seçtiği ilk etiketi zaten tutuyor, bu nedenle `firstClicked` `null` eşit değil C# ve Visual Basic `Nothing`. @No__t_0 deyiminiz, `null` veya `Nothing` eşit olup olmadığını anlamak için `firstClicked` denetlediğinde, olmadığını bulur ve `if` deyimindeki deyimleri yürütmez. Bu nedenle, aşağıdaki resimde gösterildiği gibi, yalnızca seçilen ilk simgenin rengi siyah olur ve diğer simgeler görünmez.

     ![Eşleşen oyun bir simge gösteriyor](../ide/media/express-tut4step5.png "Express_Tut4Step5") Eşleşen oyun bir simge gösteriyor

     Bu durumu, bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında düzeltireceksiniz.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 6. [Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md).

- Önceki öğretici adımına dönmek için, bkz. [Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).
