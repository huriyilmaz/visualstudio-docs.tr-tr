---
title: '5\. Adım: Etiket başvuruları ekleme'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fdcecbdac0a866bd5c6a15a78d8c0ba2a33051a
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289672"
---
# <a name="step-5-add-label-references"></a>5\. Adım: Etiket başvuruları ekleme
Programın, Player 'ın seçtiği etiket denetimlerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık ilk olarak hangi etiket denetiminin seçili olduğunu ve *başvuru değişkenlerini*kullanarak ikinci seçili olduğunu izler.

## <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > C# Kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>Docs. Microsoft. com @ no__t-1 için ![Programlama dil denetimi

     Bu başvuru değişkenleri, formunuza nesneleri eklemek için (<xref:System.Windows.Forms.Timer> nesneleri, <xref:System.Collections.Generic.List%601> nesneleri ve <xref:System.Random> nesneleri gibi) daha önce kullandığınız deyimlere benzer. Ancak, bu deyimler iki deyimden birinde `new` anahtar sözcüğü kullanılmadığından, formda iki ek etiket denetiminin görünmesine neden olmaz. @No__t-0 anahtar sözcüğü olmadan hiçbir nesne oluşturulmaz. @No__t-0 ve `secondClicked` neden başvuru değişkenleri olarak adlandırılır: Yalnızca izleme (veya, başvuru) nesnelerini takip eder.

     Bir değişken bir nesneyi takip tutmazsa, özel bir ayrılmış değere ayarlanır: Visual C# 'te `null` ve Visual Basic `Nothing`. Bu nedenle, program başladığında her ikisi de `firstClicked` ve `secondClicked` `null` veya `Nothing` olarak ayarlanır, bu da değişkenlerin herhangi bir şeyi izlememediği anlamına gelir.

2. @No__t-0 olay işleyicinizi yeni `firstClicked` başvuru değişkenini kullanacak şekilde değiştirin. @No__t-0 olay işleyicisi yönteminde (`clickedLabel.ForeColor = Color.Black;`) son ifadeyi kaldırın ve bunu izleyen `if` ifadesiyle değiştirin. (Yorumu ve tüm `if` ifadesini eklediğinizden emin olun.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program, Player 'ın seçtiği ilk etiketi zaten takip ediyor, bu nedenle `firstClicked`, Visual C# 'te `null` ' e eşit değildir veya Visual Basic `Nothing`. @No__t-0 deyimi `null` veya `Nothing` ' e eşit olup olmadığını anlamak için `firstClicked` ' i denetlediğinde, olmadığını bulur ve `if` deyimindeki deyimleri yürütmez. Bu nedenle, aşağıdaki resimde gösterildiği gibi, yalnızca seçilen ilk simgenin rengi siyah olur ve diğer simgeler görünmez.

     tek bir simgeyi gösteren ![ ile eşleşen oyun @ no__t-1<br/>
**Eşleşen oyun** bir simge gösteriyor

     Bu durumu, bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında düzeltireceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [Step 6: Bir süreölçer ekleyin @ no__t-0.

- Önceki öğretici adımına dönmek için bkz. [Adım 4: Her etikete bir tıklama olayı işleyicisi ekleyin @ no__t-0.
