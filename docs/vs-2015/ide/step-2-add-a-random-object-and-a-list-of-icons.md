---
title: '2. Adım: rastgele bir nesne ve simge listesi ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7370bf956fd79f5568737af5d9a96b9c64a5316b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667308"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2. Adım: Rasgele Nesne ve Simge Listesi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için iki `new` nesne oluşturmak üzere iki deyim kullanırsınız. Birincisi, `Random` matematik sınavından kullandığınız gibi bir nesnedir. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. Sizin için yeni olabilecek ikinci nesne, `List` rastgele seçilmiş sembolleri depolamak için kullanılan bir nesnedir.

### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rasgele nesne ve bir simge listesi eklemek için

1. **Çözüm Gezgini**, Visual C# kullanıyorsanız **Form1.cs** ' yi veya Visual Basic kullanıyorsanız **Form1. vb** öğesini seçin ve ardından menü çubuğunda **görüntüle**, **kod**' u seçin. Alternatif olarak, **F7** tuşunu seçebilir veya **Çözüm Gezgini**içinde **Form1** ' e çift tıklayatıklayabilirsiniz.

     Böylece Form1'in arkasındaki kod modülü görüntülenir.

2. Varolan kod içine aşağıdaki kodu ekleyin.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]

     Visual C# kullanıyorsanız, kodu açılış küme ayracından sonra ve Sınıf bildiriminden hemen sonra () yerleştirdiğinizden emin olun `public partial class Form1 : Form` . Visual Basic kullanıyorsanız, kodu Sınıf bildiriminden () hemen sonra koyun `Public Class Form1` .

3. `List`Nesnesi eklenirken, açılan **IntelliSense** penceresine dikkat edin. Aşağıdaki bir Visual C# örneği olmakla birlikte, Visual Basic'te liste eklediğinizde de benzer bir metin görüntülenir.

     ![Click olayını gösteren Özellikler penceresi](../ide/media/express-listintellisense.png "Express_ListIntellisense") IntelliSense penceresi

    > [!NOTE]
    > IntelliSense penceresi yalnızca kodu el ile girdiğinizde görünür. Kodu kopyalayıp yapıştırırsanız görünmez.

     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınız, `List` birçok farklı öğe türünü izlemek için nesneleri kullanabilir. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. `List`Diğer nesneleri tutan bir nesneye bile sahip olabilirsiniz `List` . Bir listedeki öğelere *öğeler*denir ve her liste yalnızca bir öğe türü tutar. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.

     `List`Bir ifade kullanarak bir nesne oluşturduğunuzda `new` , içinde depolamak istediğiniz veri türünü belirtmeniz gerekir. **IntelliSense** penceresinin en üstündeki araç ipucu, listedeki öğe türlerini gösterir. Ayrıca, bu nedir `List<string>` (Visual C# ' de) ve `List(Of String)` (Visual Basic), bu, `List` veri türü öğelerini tutan bir nesnedir `string` . Bir dize, programınızın metin depolamak için kullandığı şeydir. Bu, **IntelliSense** penceresinin sağındaki araç ipucu sizi size söylemiş olur.

4. Visual Basic'te önce geçici bir dizin oluşturulması gerekmesine karşın, Visual C# ortamında listenin tek bir deyimle oluşturulabilmesinin nedenini bir düşünün. Bunun nedeni, Visual C# dilinin *koleksiyon başlatıcılarına*sahip olmasından kaynaklanır. Bu, listeyi değerleri kabul edecek şekilde hazırlar. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.

     Bir koleksiyon başlatıcısı kullandığınızda `new` , yeni `List` nesne oluşturulduktan sonra, program bunu küme ayraçları içinde verdiğiniz verilerle doldurur. Bu durumda, **simgeler**adlı dizelerin bir listesini alırsınız ve bu liste altı harfli dizeler içerecek şekilde başlatılır. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler, Web 'e ait yazı tipine ayarlandığında, bir veri yolu, Bisiklet, Spider vb. gibi simgeler olarak görünürler.) `List` Nesneniz, TableLayoutPanel panelindeki her hücre için bir tane olmak üzere on altı dizeye sahip olacaktır.

    > [!NOTE]
    > Visual Basic, aynı sonucu elde edersiniz, ancak ilk dizeler geçici bir diziye konur ve bu daha sonra bir `List` nesneye dönüştürülür. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [3. Adım: her etikete rastgele bir simge atama](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Önceki öğretici adımına dönmek için bkz. [1. Adım: proje oluşturma ve formunuza tablo ekleme](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
