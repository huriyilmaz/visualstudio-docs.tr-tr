---
title: 'UML Bileşen diyagramları: yönergeler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297155"
---
# <a name="uml-component-diagrams-guidelines"></a>UML Bileşen Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, bir yazılım sistemi yapısını göstermek için bir *bileşen diyagramı* çizebilirsiniz. Video gösterimi için bkz. [bileşen diyagramlarını kullanarak fiziksel yapıyı tasarlama](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir UML bileşen diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

 Bir bileşen kendi ortamında değiştirilebilen modüler bir birimdir. İç yapıları gizlidir, ancak işlevlerine erişilebilen bir veya daha fazla iyi tanımlanmış *sağlanmış arabirim* vardır. Bir bileşen *gerekli arabirimlere*de sahip olabilir. Gerekli arabirim, diğer bileşenlerden hangi işlevleri veya hizmetleri beklediğini tanımlar. Birçok bileşenin sağlanan ve gerekli arabirimleri bağlanarak daha büyük bir bileşen oluşturulabilir. Tam bir yazılım sistemi bir bileşen olarak anlaşılabilir.

 Bileşen diyagramı çizmenin birçok faydası vardır:

- Tasarımınızı ana blokları dikkate alarak göz önünde bulundurmak, geliştirme takımının varolan tasarımı anlamasına ve yeni bir tane oluşturmasına yardım eder.

- Sisteminizi iyi tanımlanmış sağlanan ve gerekli arabirimlerden oluşan bir bileşenler koleksiyonu gibi düşünerek, bileşenler arasındaki ayrımı daha iyi anlayabilirsiniz. Böylece, tasarımın anlaşılması ve gereksinimler değiştiğinde değiştirilmesi daha kolay hale gelir.

  Bileşen diyagramını, tasarımın kullandığı veya kullanacağı dile ya da platforma bakılmaksızın tasarımınızı göstermek için kullanabilirsiniz.

## <a name="OtherDiagrams"></a>Diğer diyagramlarla ilişki
 Bileşen diyagramını başka diyagramlarla birlikte kullanabilirsiniz.

|Başka diyagram|Tasarımınızın bu yönlerini tartışmanıza ve iletişim kurmanıza yardımcı olur|
|-------------------|--------------------------------------------------------------------|
|UML Sıralı Diyagramı|-Sistemin bileşenleri arasındaki etkileşimler<br />-Etkileşimler ve bir bileşen içindeki parçalar arasında.<br /><br /> Daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).|
|UML Sınıf Diyagramı|-Bir bileşenin arabirimleri. Sınıf diyagramı arabirimin yöntemlerini ayrıntılı olarak incelemenizi sağlar.<br />-Bileşenlerin arabirimleri genelinde parametrelerde gönderilen veriler.<br /><br /> Daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).|
|Etkinlik Diyagramları|-Gelen iletilere yanıt olarak bir bileşen tarafından gerçekleştirilen iç işleme.<br /><br /> Daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).|
|Katman Diyagramları|-Bileşenleriniz için mantıksal mimari katmanları.<br /><br /> Daha fazla bilgi için bkz. [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a>Bileşen diyagramları çizmek için temel adımlar
 Bileşen diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz. [UML Bileşen diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md).

 Tasarım sürecinde Bileşen diyagramlarının nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Modelleme diyagramlarından herhangi birini oluşturmaya yönelik ayrıntılı adımlar [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)bölümünde açıklanmıştır.

#### <a name="to-create-a-component-diagram"></a>Bileşen diyagramı oluşturmak için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

2. **Şablonlar**altında **UML bileşen diyagramı**' na tıklayın.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de çözümünüzde mevcut bir modelleme projesi seçin veya **Yeni bir modelleme projesi oluşturun**ve ardından **Tamam**' a tıklayın.

     UML **bileşen diyagramı** araç kutusu ile yeni bir bileşen diyagramı görüntülenir. Araç kutusu gereken öğeleri ve ilişkileri içerir.

### <a name="drawing-components"></a>Bileşenleri Çizme
 ![Arabirimleri olan bileşenler](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Sisteminizdeki veya uygulamanızdaki her ana işlevsel birim için bir *bileşen* (1) oluşturun.

 Örnekler arasında uygulama, donanım cihazı, Web hizmeti, .NET derleme, program sınıfı veya sınıflar grubu ya da programın herhangi bir ayrılabilen kesimi bulunur.

##### <a name="to-create-components"></a>Bileşenler oluşturmak için

1. Araç kutusunda **bileşen** ' e tıklayın ve ardından diyagramın boş bir kısmına tıklayın.

     \- veya -

     Varolan bileşeni kopyalayıp yapıştırın.

    1. Diyagramda veya **UML Model Gezgini**'nde varolan bir bileşeni bulun.

    2. Bileşene sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

    3. Kopyalanan bileşenin görünmesini istediğiniz yerde diyagramı açın.

    4. Diyagramın boş bir kısmına sağ tıklayıp **Yapıştır**' a tıklayın.

         Bileşenin kopyası yeni bir adla görünür.

2. Değiştirmek için bileşenin adına tıklayın.

3. Yalnızca bileşenin başlığını görmek istiyorsanız köşeli çift ayraca (5) tıklayın.

### <a name="showing-the-ports-of-a-component"></a>Bileşenin Bağlantı Noktalarını Gösterme
 Bir *bağlantı noktası* (2, 3) bir bileşeni ya da bir bileşenin içine veya dışına geçen bir grup iletiyi veya işlem çağrılarını temsil eder. Grup, bağlantı noktasının türünü tanımlayan arabirim tarafından açıklanır. Bağlantı noktası, arabirim sağlar veya arabirim gerektirir.

 *Sağlanan arabirime* sahip bir bağlantı noktası (2), bileşen tarafından uygulanan ve diğer bileşenler tarafından kullanılabilen işlemler sağlar.

 Örnekler, herhangi bir programlama dilinde kullanıcı arabirimi, Web hizmeti, .NET arabirimi veya işlevler topluluğunu içerir.

 *Gerekli arabirimi* (3) olan bir bağlantı noktası, diğer bileşenler veya dış sistemler tarafından sağlanarak bir işlem veya hizmet grubu için bileşenin gereksinimini temsil eder.

 Örneğin, Web tarayıcısı Web hizmetleri gerektirir veya uygulama eklentisi uygulamadan hizmetler gerektirir.

 Bir bileşen herhangi bir sayıda bağlantı noktasına sahip olabilir.

##### <a name="to-add-ports-to-a-component"></a>Bileşene bağlantı noktaları eklemek için

1. Araç kutusunda, **sunulan arabirim** veya **gerekli arabirim ' e**tıklayın.

2. Eklemek istediğiniz bileşene tıklayın.

    Bir bağlantı noktası bileşenin sınırında görünür.

    Yeni arabirim bir bağlantı noktası türü olarak oluşturulur. Bu arabirim **UML Model Gezgini**' nde görüntülenir.

3. Bağlantı noktasını bileşen sınırı etrafında istediğiniz yere yerleştirmek için sürükleyin.

4. Bağlantı noktasının etiketini konumunu ayarlamak için sürükleyin.

5. Etiketi değiştirmek için ona tıklayın. Etiket arabirimin adını gösterir. Etiketi değiştirirseniz, arabirimin adı da değişir.

   Arabirimin özniteliklerini ve işlemlerini listelemek istiyorsanız, bunu UML Model Gezgini'nde arabirime ekleyerek yapabilirsiniz. Alternatif olarak, arabirimi UML Model Gezgini'nden sınıf diyagramına sürükleyebilir ve işlemleri ve öznitelikleri buraya ekleyebilirsiniz.

### <a name="linking-between-components"></a>Bileşenler arasında bağlama
 Bir bileşen gereksiniminin başka bileşen tarafından sağlanan işlemler veya hizmetler tarafından karşılanabileceğini göstermek için bir bağımlılık (4) kullanın.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Sağlanan arabirimin gerekli arabirimi karşılayabileceğini göstermek için

1. Araç kutusunda **bağımlılık**' a tıklayın.

2. Bir bileşende gerekli arabirime sahip bağlantı noktasına tıklayın ve ardından başka bir bileşende sağlanan arabirime sahip bağlantı noktasına tıklayın.

   Gruptaki her bileşenin diğer bileşenlere bağlı olduğu bağımlılık döngülerini tasarlamaktan kaçınmayı denemelisiniz.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Varolan arabirim için bileşene bağlantı noktası eklemek üzere

- **UML Model Gezgini** 'nde arabirimi bulun ve ardından bileşeni üzerine sürükleyin.

     veya

- Başvuruyu diyagramdan arabirime kopyalayıp yapıştırın.

    1. Bir sınıf diyagramında veya bileşen diyagramında, arabirime sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

    2. Bileşen diyagramında bileşene sağ tıklayın ve ardından **başvuruyu Yapıştır**' a tıklayın.

         Sağlanan arabirim bileşende görünür. Yakında bir Eylem etiketi görünür.

        > [!NOTE]
        > Yapıştırma **başvuru**yerine **Yapıştır** kullanırsanız, yeni bir ada sahip yeni bir arabirim oluşturulur.

    3. Gerekli bir arabirim oluşturmak isterseniz, eylem etiketine tıklayın ve **gerekli arabirime Dönüştür ' e**tıklayın.

## <a name="Parts"></a>Bir bileşenin Iç parçalarını gösterme
 ![İç parçaları gösteren bileşen diyagramı](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Nasıl birbiriyle etkileşim kuran daha küçük bileşenlerden oluştuğunu göstermek için bileşene (1) parçalar (3) yerleştirebilirsiniz.

 Şekildeki diyagram, Şimdi Akşam Yemeği Web Hizmeti türünün her örneğinin bir Müşteri Hizmeti Sunucusu ve bir Mutfak Hizmeti Sunucusu içerdiğini belirtir.

 Bir parça, sıradan bir sınıfa ait öznitelik gibi onun ana bileşeninin bir özelliğidir. Bir parçanın genellikle bileşen olan kendi türü vardır. Parçanın etiketi, sıradan bir öznitelikle aynı biçime sahiptir:

 `+ partName : TypeName`

 Ana bileşenin içinde, her parça türü (4, 5) için tanımlanmış sağlanan ve gerekli arabirimleri gösterir. Bir parça için gereken işlemler veya hizmetler bir diğeri tarafından sağlanabilir. Parçaların birbiriyle nasıl bağlandığını göstermek için, **bölüm derleme** bağlayıcılarını kullanabilirsiniz (6).

 Ana bileşenin arabiriminin gerçekte parçalarından biri tarafından sağlandığını veya gerekli kılındığını da gösterebilirsiniz. Bir bağlantı noktasını, bir **Yetkilendirme** ilişkisi (9) kullanarak bir iç parçanın bağlantı noktasına bağlayabilirsiniz. İki bağlantı noktası aynı türden olmalıdır (sağlanan veya gerekli) ve onların arabirim türleri uyumlu olmalıdır.

 Yeni bir tür ile veya varolan türden yeni bir parça oluşturabilirsiniz.

#### <a name="to-add-parts-to-a-component"></a>Bileşene parçalar eklemek için

1. Ana bileşenin bir parçası olarak düşündüğünüz her ana işlevsel birim için parça oluşturun.

    1. Araç kutusunda **bileşen** ' e tıklayın ve ardından ana bileşenin içine tıklayın (1).

         Yeni parça (3) ana bileşenin içinde görünür.

         **UML Model Gezgini**'nde yeni bir bileşen oluşturulur. Bu, yeni parçanın türüdür.

         \- veya -

         Varolan bileşeni UML Model Gezgini'nden ana bileşen üzerine sürükleyin.

         Yeni parça (3) ana bileşenin içinde görünür. Türü UML Model Gezgini'nden sürüklediğiniz bileşendir.

         \- veya -

         Diyagramda veya UML Model Gezgini ' nde bir bileşene sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

         Üst bileşene sağ tıklayın ve ardından **başvuruyu Yapıştır**' a tıklayın.

         Yeni parça (3) ana bileşenin içinde görünür. Türü kopyaladığınız bileşendir.

    2. Değiştirmek için yeni parçanın adına tıklayın. Türünü değiştiremezsiniz.

    3. Yeni parçaya sağlanan ve gerekli arabirimleri (4, 5) ekleyebilirsiniz. **Belirtilen arabirime** veya **gerekli arabirim** aracına tıklayın ve ardından bölümüne tıklayın.

         \- veya -

         **UML Model Gezgini** ' nden varolan bir arabirimi bölümüne sürükleyin.

         Arabirimler parçanın türüne eklenir ve kendi parçası üzerinde görünür. Gerekirse ana bileşen kendi boyutunu ayarlar.

2. Parçaları birbirine bağlayın.

    - Farklı parçaların (6) bağlantı noktalarını bağlamak için **bağımlılık** aracını kullanın.

3. Parçaları ana bileşenin bağlantı noktalarına bağlayın:

    1. Ana bileşen üzerinde bir veya daha çok bağlantı noktası (7) oluşturun. Araç kutusunda **gerekli arabirim** veya **sağlanmış arabirim** ' e tıklayın ve ardından üst bileşene tıklayın.

    2. Bağlantı noktalarını (9) bir veya daha çok parçaya atayın. **Temsili** aracına, ardından üst bileşendeki bir bağlantı noktasına ve ardından bir bölümde bir bağlantı noktasına tıklayın. Bağlantı noktalarını sağlanan veya gerekli arabirimlerle aynı şekilde bağlayabilirsiniz.

### <a name="showing-the-parts-of-a-part"></a>Bir Parçanın Parçalarını Gösterme
 Bir bileşeni parçalara ayırdıktan sonra, parça türlerinin her birini kendi iç parçalarına ayırabilirsiniz.

 Ayrışımın her katmanının, ayrı bileşen diyagramında tutulması en kolay yoldur. İlk önce parçanın türünü bulmanız gerekir. Örneğin, çizimde bölümlerden biri `DNCustomerServer`olarak adlandırılır ve türü `CustomerServer`adlı bir bileşendir. Bu türü UML Model Gezgini'nde bulabilir ve onu başka bir diyagrama yerleştirebilirsiniz. Daha sonra onun kendi iç parçalarını oluşturabilirsiniz.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>Diyagrama parçanın türünü yerleştirmek için

1. Parça türünün tam adını belirleyin.

     Bölüme sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     Tür adı Özellikler penceresi **tür** alanında görüntülenir.

2. **UML Model Gezgini**' nde parçanın türünü bulun.

     **Görüntüle**' ye tıklayın, **diğer pencereler**' ın üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

     Projeyi ve gerekirse türün ait olduğu herhangi bir paketi genişletin.

     Tür bir **bileşen**olarak listelenecektir.

     İsterseniz adını burada değiştirebilirsiniz.

3. Başka bir bileşen diyagramı açın veya oluşturun.

4. UML Model Gezgini'ndeki türden diyagram üzerine sürükleyin.

     Türün görünümü diyagramda bileşen olarak görüntülenir.

     Parça için tanımladığınızla aynı arabirimlere sahiptir.

     Artık parçaları içine ekleyebilirsiniz.

## <a name="Designing"></a>Bileşeni tasarlama

### <a name="describing-how-the-parts-collaborate"></a>Parçaların Birlikte Nasıl Çalıştığını Açıklama
 Parçaların ana bileşene ulaşan iletiye yanıt olarak birlikte nasıl çalıştığını göstermek için sıralı diyagram çizebilirsiniz.

 Bu diyagramları hem varolan bileşeni açıklamak hem de yeni bileşen tasarlamak için kullanabilirsiniz.

 Hala bileşeni tasarlıyorsanız, hangi parçalara sahip olacağına karar vermeden önce sıralı diyagramlar çizebilirsiniz. Sıralı diyagramları farklı parçalar, gerekli arabirimler ve ileti dizileri ile denemek için kullanabilirsiniz. En sık ve en önemli gelen iletiler için sıralı diyagramlar çizin. Daha sonra üzerinde karar verdiğiniz yaşam çizgilerine karşılık gelen bileşeninizde parçalar oluşturabilirsiniz.

 Sistem işinin farklı bileşenler arasında nasıl yayıldığını değerlendirmek için sıralı diyagramlar kullanın.

- Bir parçaya çok fazla yüklenilirse, işin eşit bir şekilde dağıtıldığı durumlara göre uygulamanın güncelleştirilmesi daha zor olacaktır.

- İş birçok etkileşimle yetersiz bir şekilde dağıtılmışsa, sistem kötü bir şekilde çalışabilir ve anlaşılması zor olabilir.

  ![İşbirliği parçalarını gösteren sıralı diyagram](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Parçalar arasındaki işbirliğini gösteren sıralı diyagram çizmek için

1. Yeni bir sıralı diyagram oluşturun.

     Daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

2. Dış bileşen, kullanıcı, cihaz veya bu bileşene iletiler gönderen diğer aktör (1) için yaşam çizgisi oluşturun.

     Bu yaşam çizgisinin **aktör** özelliğini true olarak ayarlayabilirsiniz. bunun için göz önüne alarak bileşenin dış olduğunu belirtebilirsiniz. Çubuk şekli yaşam çizgisinin üzerinde görünür.

3. Seçilen aktörün iletiler gönderdiği bu bileşenin sağlanan arabirimi (2) için yaşam çizgisi oluşturun.

4. Bileşenin her parçası (3) için yaşam çizgisi oluşturun.

5. Bileşenin gerekli her arabirimi (4) için yaşam çizgisi oluşturun.

6. Dış aktörden (5) gelen iletileri çizin. İletinin parçalara nasıl geçtiğini ve iletiye yanıt vermek için nasıl işbirliği yaptıklarını gösterin.

7. Gerektiği yerde gerekli arabirime (6) gönderilen iletileri gösterin. İletinin yürütmesi içinde hiçbir ayrıntıyı göstermeyin.

### <a name="is-the-component-more-than-its-parts"></a>Bileşen Parçalarından Daha Fazla Mıdır?
 Bazı durumlarda bileşen, parçalar topluluğuna verilen bir addan daha fazlası değildir. Tüm iş parçalar tarafından yapılır ve çalışma zamanında bileşeni gösteren kod veya başka bir yapı yoktur.

 Bunu modelde, bileşenin **dolaylı olarak örneklenmiş** özelliğini ayarlayarak gösterebilirsiniz. Bu durumda, bileşenin tüm arabirimleri yetki iç parçalara aktarılarak bağlantı noktaları üzerinde olmalıdır.

### <a name="describing-the-process-inside-each-part"></a>Her Parça İçindeki İşlemi Açıklama
 Etkinlik diyagramlarını bileşenin gelen her iletiyi nasıl işlediğini göstermek için kullanabilirsiniz. Daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

 ![Veri arabelleğiyle etkinlik diyagramı](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Gelen iletinin yeni bir iş parçacığı başlattığını göstermek için Olayı Kabul Etme Eylemi'ni (1) kullanın.

 Bilgi akışını ve bilginin nerede depolandığını göstermek için nesne düğümlerini ve giriş/çıkış sabitleyicilerini kullanın. Örnekte, bir nesne düğümü (2), bir iş parçacığı ile diğeri arasında arabelleğe alınan öğeleri göstermek için kullanılır.

### <a name="defining-data-and-classes"></a>Veri ve Sınıfları Tanımlama
 UML sınıf diyagramını şunların ayrıntılı içeriğini açıklamak için kullanabilirsiniz:

- Bileşenlerin arabirimleri. Bir bileşene gerektirir veya sağlar bağlantı noktası eklediğinizde, UML Model Gezgini'nde bir arabirim görünür. Bunu, özniteliklerini, işlemlerini ve diğer arabirimleriyle olan ilişkilerini göstermek için UML Sınıf Diyagramına sürükleyebilir veya kopyalayabilirsiniz.

- Arabirimlerdeki işlemlerin parametrelerinde geçirilen veriler.

- Etkinlik diyagramlarındaki nesne akışlarında gösterildiği gibi bileşenlerde depolanan veriler.

### <a name="general-dependencies-between-components"></a>Bileşenler Arasındaki Genel Bağımlılıklar
 Yalnızca tasarımınızın ana parçalarını ve onların bağımlılıklarını göstermek için bileşen diyagramını kullanabilirsiniz.

 ![Bileşenler arasında bağımlılık](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Bir bağımlılık çizmek için **bağımlılık** aracını kullanın. Bu, bir bileşenin tasarımının başka birine bağlı olduğunu gösterir.

 Bağımlılığın tipik türleri şunlardır:

- Bir bileşen diğeri içindeki kodu çağırır.

- Bir bileşen başka bir sınıfın içinde tanımlanan sınıfın örneğini oluşturur.

- Bir bileşen başka bir bileşen tarafından oluşturulan bilgileri kullanır.

  Kullanımın belirli bir türünü göstermek için bağımlılık okunun adını kullanabilirsiniz. Adı ayarlamak için oka sağ tıklayın, ardından **Özellikler**' e tıklayın ve Özellikler penceresinde **ad** alanını ayarlayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML Bileşen diyagramları:](../modeling/uml-component-diagrams-reference.md) [başvuru UML](../modeling/uml-sequence-diagrams-reference.md) [kullanım örneği diyagramları](../modeling/uml-use-case-diagrams-reference.md) : başvuru UML [sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru [video: fiziksel yapıyı Bileşen diyagramları kullanarak tasarlama](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
