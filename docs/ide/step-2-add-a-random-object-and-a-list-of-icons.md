---
title: '2. Adım: Rastgele nesne ve simge listesi ekleme'
description: Oyun için eşleşen semboller kümesi oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a2c0e9f72e0a1dc31be3d867ca1078ddb5227754
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628509"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>2. Adım: Rastgele nesne ve simge listesi ekleme

Bu adımda, oyun için bir grup eşleşen simge oluşturuyorsunuz. Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir. Bunu yapmak için, iki nesne `new` oluşturmak için iki deyimi kullanırsiniz. Birincisi, matematik testi oyunlarında kullanılan nesne gibi <xref:System.Random> bir nesnedir. Bu koddaki kullanım amacıysa, TableLayoutPanel denetiminde rasgele hücre seçmektir. Sizin için yeni olan ikinci nesne, rastgele seçilen sembolleri depolamak <xref:System.Collections.Generic.List%601> için kullanılan bir nesnedir.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Rastgele bir nesne ve simge listesi eklemek için

1. Bu **Çözüm Gezgini** C# kullanıyorsanız *Form1.cs* veya Visual Basic kullanıyorsanız *Form1.vb'yi* seçin ve ardından menü çubuğunda Kodu **Görüntüle'yi**  >  **seçin.** Alternatif olarak, **F7** anahtarını seçebilir veya form1'de **form1'e** çift **Çözüm Gezgini.**

     Böylece Form1'in arkasındaki kod modülü görüntülenir.

2. Varolan kod içine aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet1":::

      > [!IMPORTANT]
      > C# kod parçacığını veya kod parçacığını görüntülemek için bu sayfanın sağ üst kısmında yer alan programlama dili Visual Basic kullanın.<br><br>![Docs.Microsoft.com için programlama dili denetimi](../ide/media/docs-programming-language-control.png)

      C# kullanıyorsanız, kodu açılış küme ayracından sonra ve sınıf bildiriminin hemen altına ( ) koyarak emin `public partial class Form1 : Form` olun. Visual Basic kullanıyorsanız, kodu sınıf bildiriminin () hemen altına `Public Class Form1` girin.

3. List nesnesini eklerken açılan **IntelliSense penceresine** dikkat edin. Aşağıda bir C# örneği ve benzer bir metin yer alelade bir liste Visual Basic.

     ![Tıklama olayını gösteren Özellikler penceresi](../ide/media/express_listintellisense.png)<br/>***IntelliSense** penceresi*

    > [!NOTE]
    > IntelliSense penceresi yalnızca kodu el ile girerken görünür. Kodu kopyalayıp yapıştırırsanız görünmez.

     Kodu (ve açıklamaları) küçük bölümler halinde incelerseniz anlaması daha kolay olur. Programlarınız birçok farklı öğe türlerini izlemek için liste nesnelerini kullanabilir. Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir. Hatta diğer liste nesnelerini tutan bir liste nesnesi bile olabilir. Bir listedeki öğelere öğe adı ve her liste yalnızca bir öğe türü içerir. Öyleyse, bir sayı listesi yalnızca sayıları tutabilir; bu listeye metin ekleyemezsiniz. Benzer şekilde, doğru/yanlış değerlerini içeren bir listeye sayı ekleyemezsiniz.

     deyimini `List` kullanarak bir nesne `new` oluşturursanız, içinde depolamak istediğiniz veri türü belirtmeniz gerekir. Bu nedenle **IntelliSense** penceresinin üst kısmında yer alan araç ipucu, listede yer alan öğe türlerini gösterir. Ayrıca (C#' içinde) ve (Visual Basic) şu anlama gelir: Veri türü öğelerini `List<string>` `List(Of String)` tutan bir `List` `string` nesnedir. Dize, programınız metin depolamak için kullandığı dizedir. **IntelliSense** penceresinin sağ tarafından sağ tarafından bu araç ipucu bunu söylüyor.

4. İlk olarak Visual Basic dizi oluşturmanın gerektiğini ancak C# içinde listenin tek bir deyimle oluşturulama neden gerektiğini göz önünde bulundurabilirsiniz. Bunun nedeni, C# dilinde listeyi *değerleri kabul etmek için* hazırlayacak koleksiyon başlatıcıları olmasıdır. Visual Basic'te bir koleksiyon başlatıcısı kullanabilirsiniz. Ancak, önceki Visual Basic sürümü ile uyumluluk açısından önceki kodu kullanmanızı öneririz.

     Deyimiyle bir koleksiyon başlatıcısı kullanırken, yeni List nesnesi oluşturulduktan sonra program bunu küme ayraçlarının içinde `new` sağlanan verilerle doldurur. Bu durumda simgeler adlı dizelerin listesini alır ve bu liste on altı dizeyi içeren şekilde başlatılır. Bu dizelerin her biri tek bir harftir ve bunların tümü etiketlerde yer alacak simgelere karşılık gelir. Dolayısıyla, oyunda bir çift ünlem işareti, bir çift büyük N harfi, bir çift virgül vs. olacaktır. (Bu karakterler Webdings yazı tipine ayarlanırsa, bunlar bir veri yolu, bisiklet, bir dağ gibi semboller olarak görünür.) Liste nesneniz, TableLayoutPanel panelindeki her hücre için bir tane olmak için on altı dize içerir.

    > [!NOTE]
    > Bu Visual Basic aynı sonucu elde edersiniz, ancak önce dizeler geçici bir diziye eklenir ve bu da bir liste nesnesine dönüştürülür. Örneğin, dizilerin sabit boyutlu oluşturulması dışında, dizi bir listeye benzer. Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için [**bkz. 3. Adım: Her etikete rastgele bir simge atama.**](../ide/step-3-assign-a-random-icon-to-each-label.md)

- Önceki öğretici adımına dönmek için [bkz. 1. Adım: Proje oluşturma ve formnize tablo ekleme.](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)
