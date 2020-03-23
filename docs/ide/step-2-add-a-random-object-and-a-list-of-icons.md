---
title: 'Adım 2: Rastgele nesne ve simgelerin listesi ekleme'
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
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579422"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Adım 2: Rastgele nesne ve simgelerin listesi ekleme

Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için, `new` iki nesne oluşturmak için iki deyim kullanırsınız. İlki, <xref:System.Random> matematik testi oyununda kullandığınız gibi bir nesnedir. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. Sizin için yeni olabilecek ikinci nesne, <xref:System.Collections.Generic.List%601> rasgele seçilen sembolleri depolamak için kullanılan bir nesnedir.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rasgele bir nesne ve simgelerin listesini eklemek için

1. **Solution Explorer'da,** Visual Basic kullanıyorsanız C#veya *Form1.vb* kullanıyorsanız *Form1.cs* seçin ve ardından menü çubuğunda**Kodu** **Görüntüle'yi** > seçin. Alternatif olarak, **Çözüm Gezgini'nde** **F7 tuşunu** seçebilir veya **Form1'i** çift tıklatabilirsiniz.

     Böylece Form1'in arkasındaki kod modülü görüntülenir.

2. Varolan kod içine aşağıdaki kodu ekleyin.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > C# kodu snippet'ini veya Visual Basic kod snippet'ini görüntülemek için bu sayfanın sağ üst kısmındaki programlama dili denetimini kullanın.<br><br>![Docs.Microsoft.com için programlama dil kontrolü](../ide/media/docs-programming-language-control.png)

      C# kullanıyorsanız, kodu açılış kıvırcık ayracından sonra ve sınıf bildiriminden`public partial class Form1 : Form`hemen sonra ( ) koyduğunuzdan emin olun. Visual Basic kullanıyorsanız, kodu sınıf bildiriminden hemen`Public Class Form1`sonra () koyun.

3. Liste nesnesini eklerken açılan **IntelliSense** penceresine dikkat edin. Aşağıda bir C# örneği verilmiştir, ancak Visual Basic'e bir liste eklediğinizde benzer metin görüntülenir.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_listintellisense.png)<br/>***IntelliSense** penceresi*

    > [!NOTE]
    > IntelliSense penceresi yalnızca kodu el ile girdiğinizde görüntülenir. Kodu kopyalayıp yapıştırırsanız görünmez.

     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınız, birçok farklı öğe türünü izlemek için liste nesnelerini kullanabilir. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. Diğer liste nesnelerini tutan bir liste nesnesi de olabilir. Listedeki öğeler öğe olarak adlandırılır ve her liste yalnızca bir öğe türünü tutar. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.

     Bir ekstre kullanarak bir `List` nesne oluşturduğunuzda, içinde depolamak istediğiniz veri türünü belirtmeniz gerekir. `new` Bu nedenle **IntelliSense** penceresinin üst kısmındaki araç ucu listedeki öğe türlerini gösterir. Ayrıca, `List<string>` (C#) ve `List(Of String)` (Visual Basic'te) anlamı budur: `List` `string` Veri türü öğelerini barındıran bir nesnedir. Bir dize, programınızın metni depolamak için kullandığı dizedir ve **IntelliSense** penceresinin sağındaki araç ucu size bunu söyler.

4. Visual Basic'te neden önce geçici bir dizi oluşturulması gerektiğini, ancak C#'da listenin tek bir deyimle oluşturulabileceğini düşünün. Bunun nedeni, C# dilinin listeyi değerleri kabul etmek üzere hazırlayan *koleksiyon başlatmalayıcıları*olmasıdır. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.

     Bir `new` deyimle bir koleksiyon başlatılması kullandığınızda, yeni Liste nesnesi oluşturulduktan sonra, program onu kıvırcık ayraçların içinde sağladığınız verilerle doldurur. Bu durumda, simgeleri adlı dizeleri bir listesini almak ve bu liste on altı dizeleri içeren böylece baş harfe getirilecektir. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler Webdings yazı tipine ayarlandığında, otobüs, bisiklet, örümcek vb. gibi semboller olarak görünürler.) Liste nesnenizde Tablo Düzeni Panel panelindeki her hücre için bir tane olmak üzere toplam on altı dize bulunur.

    > [!NOTE]
    > Visual Basic'te, aynı sonucu alırsınız, ancak önce dizeleri geçici bir diziye konur ve daha sonra liste nesnesine dönüştürülür. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için [**bkz: Adım 3: Her etikete rasgele bir simge atayın.**](../ide/step-3-assign-a-random-icon-to-each-label.md)

- Önceki öğretici adıma dönmek için [Bkz. Adım 1: Proje oluşturun ve formunuza bir tablo ekleyin.](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)
