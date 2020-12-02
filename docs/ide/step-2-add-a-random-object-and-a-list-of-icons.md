---
title: '2. Adım: rastgele bir nesne ve simge listesi ekleme'
description: Oyun için bir dizi eşleşen sembol oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1018b390f6ebbf67fab88554aa85fe6a8ecec88d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480700"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2. Adım: rastgele bir nesne ve simge listesi ekleme

Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için iki `new` nesne oluşturmak üzere iki deyim kullanırsınız. Birincisi, <xref:System.Random> matematik sınavından kullandığınız gibi bir nesnedir. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. Sizin için yeni olabilecek ikinci nesne, <xref:System.Collections.Generic.List%601> rastgele seçilmiş sembolleri depolamak için kullanılan bir nesnedir.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rastgele bir nesne ve simge listesi eklemek için

1. **Çözüm Gezgini**, C# kullanıyorsanız *Form1.cs* ' yi veya Visual Basic kullanıyorsanız *Form1. vb* öğesini seçin ve ardından menü çubuğunda kodu **görüntüle**' yi seçin  >  **Code**. Alternatif olarak, **F7** tuşunu seçebilir veya **Çözüm Gezgini** içinde **Form1** ' e çift tıklayatıklayabilirsiniz.

     Böylece Form1'in arkasındaki kod modülü görüntülenir.

2. Varolan kod içine aşağıdaki kodu ekleyin.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > C# kod parçacığını veya Visual Basic kod parçacığını görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

      C# kullanıyorsanız, kodu açılış küme ayracından sonra ve Sınıf bildiriminden hemen sonra () yerleştirdiğinizden emin olun `public partial class Form1 : Form` . Visual Basic kullanıyorsanız, kodu Sınıf bildiriminden () hemen sonra koyun `Public Class Form1` .

3. Liste nesnesi eklenirken, açılan **IntelliSense** penceresine dikkat edin. Aşağıda bir C# örneği verilmiştir ancak Visual Basic bir liste eklediğinizde benzer bir metin görüntülenir.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_listintellisense.png)<br/>**_IntelliSense_* penceresi*

    > [!NOTE]
    > IntelliSense penceresi yalnızca el ile kod girdiğinizde görünür. Kodu kopyalayıp yapıştırırsanız görünmez.

     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınız, birçok farklı öğe türünü izlemek için liste nesnelerini kullanabilir. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. Diğer Liste nesnelerini tutan bir liste nesneniz bile olabilir. Bir listedeki öğelere öğeler denir ve her liste yalnızca bir öğe türü tutar. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.

     `List`Bir ifade kullanarak bir nesne oluşturduğunuzda `new` , içinde depolamak istediğiniz veri türünü belirtmeniz gerekir. **IntelliSense** penceresinin en üstündeki araç ipucu, listedeki öğe türlerini gösterir. Ayrıca, bu, `List<string>` (C# ' de) ve `List(Of String)` (Visual Basic olarak), `List` veri türü öğelerini tutan bir nesnedir `string` . Bir dize, programınızın metin depolamak için kullandığı şeydir. Bu, **IntelliSense** penceresinin sağındaki araç ipucu sizi size söylemiş olur.

4. Visual Basic neden geçici bir dizi oluşturulmalıdır, ancak C# ' ta, listenin tek bir deyimle oluşturulması gerekir. Bunun nedeni, C# dilinin *koleksiyon başlatıcıları* olduğundan, listeyi değerleri kabul edecek şekilde hazırlar. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.

     Bir koleksiyon başlatıcısı kullandığınızda `new` , yeni liste nesnesi oluşturulduktan sonra, program bunu küme ayraçları içinde verdiğiniz verilerle doldurur. Bu durumda, simgeler adlı dizelerin bir listesini alırsınız ve bu liste altı harfli dizeler içerecek şekilde başlatılır. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler, Web 'e ait yazı tipine ayarlandığında, bir veri yolu, Bisiklet, Spider vb. gibi simgeler olarak görünürler.) Liste nesneniz, TableLayoutPanel panelindeki her hücre için bir tane olmak üzere on altı dizeye sahip olacaktır.

    > [!NOTE]
    > Visual Basic, aynı sonucu alırsınız, ancak önce dizeler geçici bir diziye konur, bu daha sonra bir liste nesnesine dönüştürülür. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [**3. Adım: her etikete rastgele bir simge atama**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Önceki öğretici adımına dönmek için bkz. [1. Adım: proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
