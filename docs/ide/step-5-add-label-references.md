---
title: '5. Adım: Etiket başvuruları ekleme'
description: Formunuza etiket başvuruları eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95a4286feb778e17b345f964b1b7ccca5343e461
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480570"
---
# <a name="step-5-add-label-references"></a>5. Adım: Etiket başvuruları ekleme
Programın, Player 'ın seçtiği etiket denetimlerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık ilk olarak hangi etiket denetiminin seçili olduğunu ve *başvuru değişkenlerini* kullanarak ikinci seçili olduğunu izler.

## <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

     Bu başvuru değişkenleri formunuza nesneleri eklemek için ( <xref:System.Windows.Forms.Timer> nesneler, <xref:System.Collections.Generic.List%601> nesneler ve nesneler gibi), daha önce kullandığınız deyimlere benzer şekilde görünür <xref:System.Random> . Ancak, `new` iki deyimden birinde anahtar sözcük kullanılmadığından, bu deyimler formda iki ek etiket denetiminin görünmesine neden olmaz. `new`Anahtar sözcüğü olmadan hiçbir nesne oluşturulmaz. `firstClicked`Bunun nedeni ve `secondClicked` başvuru değişkenleri olarak adlandırılmaları gerekir: yalnızca izleme (veya, başvuru) nesnelerini takip eder.

     Bir değişken bir nesneyi izlememediğinde, özel bir ayrılmış değere ayarlanır: `null` C# ve `Nothing` Visual Basic. Bu nedenle, program başlatıldığında `firstClicked` ve ya da olarak ayarlanır; bu da `secondClicked` `null` `Nothing` değişkenlerin herhangi bir şeyi izlememediği anlamına gelir.

2. <xref:System.Windows.Forms.Control.Click>Olay işleyicinizi yeni başvuru değişkenini kullanacak şekilde değiştirin `firstClicked` . `label_Click()`Olay işleyicisi yönteminde () son ifadeyi kaldırın `clickedLabel.ForeColor = Color.Black;` ve bunu `if` takip eden deyimle değiştirin. (Yorumu ve tüm deyimin dahil ettiğinizden emin olun `if` .)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program, Player 'ın seçtiği ilk etiketi zaten tutuyor, bu nedenle `firstClicked` `null` C# veya Visual Basic olarak eşit değildir `Nothing` . `if`Deyiminiz `firstClicked` veya ' a eşit olup olmadığını belirlemeyi denetlediğinde, olmadığını `null` `Nothing` bulur ve `if` deyimdeki deyimleri yürütmez. Bu nedenle, aşağıdaki görüntüde gösterildiği gibi, yalnızca seçilen ilk simge siyah ' ü etkinleştirir ve diğer simgeler görünmez hale gelir.

     ![Tek bir simgeyi gösteren eşleştirme oyunu](../ide/media/express_tut4step5.png)<br/>
***Eşleşen oyun** _ _showing bir simge *

     Bu durumu, bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında düzeltireceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 6. **[Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md)**.

- Önceki öğretici adımına dönmek için, bkz. [Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).
