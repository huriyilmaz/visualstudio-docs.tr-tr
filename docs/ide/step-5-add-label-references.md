---
title: '5\. Adım: etiket başvuruları ekleme'
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
ms.openlocfilehash: de89d7194425e1a8cba9e11f2734372d80b256b3
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579335"
---
# <a name="step-5-add-label-references"></a>5\. Adım: etiket başvuruları ekleme
Programın, Player 'ın seçtiği etiket denetimlerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık ilk olarak hangi etiket denetiminin seçili olduğunu ve *başvuru değişkenlerini*kullanarak ikinci seçili olduğunu izler.

## <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs.Microsoft.com](../ide/media/docs-programming-language-control.png) için programlama dili denetimi ![

     Bu başvuru değişkenleri formunuza nesneleri eklemek için (<xref:System.Windows.Forms.Timer> nesneleri, <xref:System.Collections.Generic.List%601> nesneleri ve <xref:System.Random> nesneleri gibi), daha önce kullandığınız deyimlere benzer şekilde görünür. Ancak, bu deyimler iki deyimden birinde kullanılan `new` anahtar sözcük olmadığından, formda iki ek etiket denetiminin görünmesine neden olmaz. `new` anahtar sözcüğü olmadan hiçbir nesne oluşturulmaz. `firstClicked` ve `secondClicked` başvuru değişkenleri olarak adlandırılmaktadır: yalnızca izleme (veya, başvuru) nesneleri.

     Bir değişken bir nesneyi izlememediğinde, özel bir ayrılmış değere ayarlanır: içinde C# `null` ve Visual Basic `Nothing`. Bu nedenle, program başlatıldığında `firstClicked` ve `secondClicked` `null` veya `Nothing`olarak ayarlanır, bu da değişkenlerin herhangi bir şeyi izlememediği anlamına gelir.

2. <xref:System.Windows.Forms.Control.Click> olay işleyicinizi yeni `firstClicked` başvuru değişkenini kullanacak şekilde değiştirin. `label_Click()` olay işleyicisi yönteminde (`clickedLabel.ForeColor = Color.Black;`) son ifadeyi kaldırın ve bunu izleyen `if` ifadesiyle değiştirin. (Yorumu ve tüm `if` deyiminizi eklediğinizden emin olun.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program, Player 'ın seçtiği ilk etiketi zaten takip ediyor, bu nedenle `firstClicked` `null` veya `Nothing` ' C# de Visual Basic eşit değil. `if` deyiminiz, `null` veya `Nothing`eşit olup olmadığını anlamak için `firstClicked` denetlediğinde, olmadığını bulur ve `if` deyimindeki deyimleri yürütmez. Bu nedenle, aşağıdaki görüntüde gösterildiği gibi, yalnızca seçilen ilk simge siyah ' ü etkinleştirir ve diğer simgeler görünmez hale gelir.

     tek bir simge](../ide/media/express_tut4step5.png) eşleşen oyun ![<br/>
***Eşleşen oyun*** *bir simge gösteriyor*

     Bu durumu, bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında düzeltireceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 6. **[Adım: Zamanlayıcı ekleme](../ide/step-6-add-a-timer.md)** .

- Önceki öğretici adımına dönmek için, bkz. [Adım 4: Her Etikete Click olay Işleyicisi ekleme](../ide/step-4-add-a-click-event-handler-to-each-label.md).
