---
title: 'Adım 5: Etiket referansları ekleme'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579335"
---
# <a name="step-5-add-label-references"></a>Adım 5: Etiket referansları ekleme
Programın, oyuncunun seçtiği Etiket denetimlerini izlemesi gerekir. Şu anda program oyuncunun seçtiği tüm etiketleri göstermektedir. Ancak bunun değişmesini sağlayacağız. İlk etiket seçildikten sonra program etiketin simgesini göstermelidir. İkinci etiket seçildikten sonra iki simgeyi de kısa bir süre göstermeli ve ardından iki simgeyi de tekrar gizlemelidir. Programınız artık *referans değişkenleri*kullanılarak hangi Etiket denetiminin ilk sırada seçildiğini ve hangilerinin ikinci seçildiğini takip edecektir.

## <a name="to-add-label-references"></a>Etiket başvuruları eklemek için

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)

     Bu başvuru değişkenleri, formunuza nesneler (nesneler, <xref:System.Windows.Forms.Timer> <xref:System.Collections.Generic.List%601> nesneler ve <xref:System.Random> nesneler gibi) eklemek için daha önce kullandığınız ifadelere benzer. Ancak, bu ifadeler, iki ifadenin hiçbirinde anahtar kelime kullanılmadığından, `new` formda iki ek Etiket denetiminin görünmesine neden olmaz. `new` Anahtar kelime olmadan hiçbir nesne oluşturulmaz. Bu nedenle `firstClicked` ve `secondClicked` referans değişkenleri denir: Onlar sadece izlemek (veya, bakın) Etiket nesneleri.

     Bir değişken bir nesneyi takip etmiyorsa, özel bir ayrılmış `null` değere ayarlanır: C# ve `Nothing` Visual Basic'te. Yani, program başladığında, `firstClicked` her `secondClicked` ikisi `null` de `Nothing`ve ayarlanır ya da , hangi değişkenler bir şey takip olmadığı anlamına gelir.

2. Yeni `firstClicked` <xref:System.Windows.Forms.Control.Click> başvuru değişkenini kullanmak için olay işleyicinizi değiştirin. Olay işleyicisi `label_Click()` yöntemindeki son`clickedLabel.ForeColor = Color.Black;`deyimi kaldırın ( `if` ) ve aşağıdaki deyimle değiştirin. (Yorumu ve tüm `if` ifadeyi eklediğinizden emin olun.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.

4. Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin. Program zaten oyuncunun seçtiği ilk etiketi takip ediyor, `firstClicked` bu nedenle `null` C# veya `Nothing` Visual Basic'te eşit değildir. `if` Ekstreniz `firstClicked` eşit `null` `Nothing`olup olmadığını belirlemek için kontrol ettiğinde, bunun eşit olmadığını fark eder ve `if` deyimdeki ifadeleri yürütmez. Bu nedenle, yalnızca seçilen ilk simge siyaha döner ve aşağıdaki resimde gösterildiği gibi diğer simgeler görünmezdir.

     ![Tek bir simgeyi gösteren eşleştirme oyunu](../ide/media/express_tut4step5.png)<br/>
***Bir*** simge *gösteren* eşleştirme oyunu

     Bir **Zamanlayıcı** denetimi ekleyerek öğreticinin bir sonraki adımında bu durumu düzelteceksiniz.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 6: Zamanlayıcı ekleyin.](../ide/step-6-add-a-timer.md)**

- Önceki öğretici adıma dönmek için [bkz: Adım 4: Her etikete bir Tıklama olay işleyicisi ekleyin.](../ide/step-4-add-a-click-event-handler-to-each-label.md)
