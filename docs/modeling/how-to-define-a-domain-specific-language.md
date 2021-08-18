---
title: 'Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama'
description: Etki alanına özgü Visual Studio (DSL) tanımlamak için şablondan bir çözüm oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 58a8e3d9f86d11ba5bbd669b841ef5176373225b6be0aa5cee25cfaec32063aa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386425"
---
# <a name="how-to-define-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama
Etki alanına özgü bir dil (DSL) tanımlamak için şablondan Visual Studio bir çözüm oluşturursanız. Çözümün önemli bölümü DslDefinition.dsl içinde depolanan DSL Tanımı diyagramıdır. DSL Tanımı, DSL'nin sınıflarını ve şekillerini tanımlar. Bu öğeleri değiştirdikten ve ekledikten sonra, DSL'yi daha ayrıntılı özelleştirmek için program kodu eklediniz.

DSL'leri yeni başladıysanız DSL **Araçları** Laboratuvarı'nın üzerinden çalışmanız önerilir. Bu sitede bulabilirsiniz: [Görselleştirme ve Modelleme SDK'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Şablon Çözümü Seçme

DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olması gerekir:

- Visual Studio
- Visual Studio uzantısı geliştirme iş yükü (Visual Studio SDK'sı dahil)
- Modelleme SDK'sı (sdk'yı tek bir bileşen olarak Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Etki alanına özgü yeni bir dil oluşturmak için, Domain-Specific Language proje şablonunu kullanarak yeni bir Visual Studio çözüm oluşturursanız.

### <a name="to-create-a-dsl-solution"></a>DSL çözümü oluşturmak için

1. Yeni bir Etki **Alanına Özgü Dil projesi** oluşturun.

   ::: moniker range="vs-2017"

    ![DSL Oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    Etki **Alanına Özgü Dil Sihirbazı açılır** ve ŞABLON DSL çözümlerinin bir listesini görüntüler.

2. Açıklamayı görmek için her şablona tıklayın. Oluşturmak istediğiniz çözüme en çok benzeyen çözümü seçin.

    Her DSL şablonu, çalışan temel bir DSL tanımlar. Bu DSL'yi kendi gereksinimlerinize uyacak şekilde düzenleyebilirsiniz.

    Daha fazla bilgi için her bir örneği tıklatın.

   - **Kullanlar Flow** DSL oluşturmak için Görev Yöneticisi'ne seçin. Kulanlar diyagramın dikey veya yatay bölümleridir.

   - Bağlantı **noktaları olan bir** DSL oluşturmak için Bileşen Modelleri'ne seçin. Bağlantı noktaları, daha büyük bir şeklin kenarında yer alan küçük şekillerdir.

   - Bölme **şekillerine sahip bir** DSL tanımlamak için Sınıf Diyagramları'ı seçin. Bölme şekilleri öğe listelerini içerir.

   - Diğer **durumlarda veya** belirsiz durumda En Az Dil'i seçin.

   - Windows Forms veya **WPF** yüzeyinde görüntülenen bir DSL oluşturmak için En Az **WinForm** Tasarımcısı'Windows WPF Tasarımcısı'ı seçin. Düzenleyiciyi tanımlamak için kod yazmanız gerekir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

        [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Dsl'niz için uygun sihirbaz sayfasına bir dosya adı uzantısı girin. Bu, DSL'nizin örneklerini içeren dosyaların kullanabileceği uzantıdır.

   - Bilgisayarınızda veya DSL'yi yüklemek istediğiniz herhangi bir bilgisayarda herhangi bir uygulamayla ilişkilendirilen bir dosya adı uzantısı seçin. Örneğin **docx ve** **html dosyaları** kabul edilemez dosya adı uzantıları olabilir.

   - Girdiğiniz uzantı DSL olarak kullanılıyorsa sihirbaz sizi uyaracak. Farklı bir dosya adı uzantısı kullanmayı göz önünde bulundurabilirsiniz. Eski deneysel tasarımcıları temizlemek Visual Studio SDK Deneysel örneğini de sıfırlayabilirsiniz. **Başlat'a** tıklayın, Tüm **Programlar**'a tıklayın, **Microsoft Visual Studio 2010 SDK'sı**, **Araçlar'a** tıklayın ve ardından **Microsoft Visual Studio 2010 Deneysel örneğini sıfırlayın.**

4. Diğer sayfalarda ayarları ayarlayabilir veya varsayılan değerleri bırakın.

5. **Finish (Son)** düğmesine tıklayın.

    Sihirbaz, iki veya üç proje içeren bir çözüm oluşturur ve DSL tanımından kod oluşturur.

   Kullanıcı arabirimi artık aşağıdaki resme benzer.

   ![dsl tasarımcısı](../modeling/media/dsl_designer.png)

   Bu çözüm, etki alanına özgü bir dil tanımlar. Daha fazla bilgi için [bkz. Domain-Specific Dil Araçları'Kullanıcı Arabirimi.](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)

### <a name="test-the-solution"></a>Çözümü Test Etmek
 Şablon çözümü, olduğu gibi değiştirerek veya kullanabileceğiniz çalışan bir DSL sağlar.

 Çözümü test etmek için F5 veya CTRL+F5 tuşlarına basın. Yeni bir Visual Studio deneysel modda açılır.

 Yeni Visual Studio örneğinde Çözüm Gezgini dosyasını açın. Araç kutusuyla birlikte diyagram olarak açılır.

 Minimal Dil şablonundan oluşturduğunuz bir  çözümü çalıştırırsanız deneysel Visual Studio aşağıdaki örnekteki gibi olacaktır:

 ![Visual Studio'de etki alanına özgü dil örnek Visual Studio](../modeling/media/dsl_min.png)

 Araçlarla denemeler. Öğeleri oluşturun ve bunları birbirine bağlayın.

 Deneysel Visual Studio.

> [!NOTE]
> DSL'i değiştirildiğinde, Artık Örnek test dosyasında şekilleri göremeyeceksiniz. Ancak yeni öğeler oluşturabilirsiniz.

### <a name="modifying-the-template-dsl"></a>Şablon DSL'sini değiştirme
 Etki alanı sınıflarının ve şekil sınıflarının bir veya hepsini şablon DSL tanımında yeniden adlandır ve tut. Yeni sınıf adlarınız boşluk veya noktalama işareti olmadan geçerli CLR adları olmalıdır.

 Bu sınıfların tutularak özellikle yararlı olur:

- Kök sınıf DSL Tanımı diyagramının sol üst kısmında Sınıflar ve İlişkiler **altında görünür.** DSL'den farklı bir adla yeniden adlandırarak. Örneğin, **MusicLibrary adlı bir** DSL'nin Müzik adlı bir kök sınıfı **olabilir.**

- Diyagram sınıfı DSL Tanımı diyagramının sağ alt köşesindeki Diyagram Öğeleri **sütununda** görünür. Görmek için sağa kaydırmak zorunda olabilir. Genellikle _YourDsl_ Diagram olarak **adlandırılmıştır.**

- **Task Flow** şablonunu kullandıysanız ve kullanlarla diyagramlar oluşturmak için Actor etki alanı sınıfını ve ActorSwimlane şeklini kullanın.

  Diğer sınıfları gereksinimlerinize uyacak şekilde silin veya yeniden adlandırabilirsiniz.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> DSL Tanımlama Desenleri
 Aynı anda bir veya iki özellik ekleyerek veya ayarlayarak DSL geliştirmenizi öneririz. Bir özellik ekleyin, DSL'yi çalıştırın ve testin ardından bir veya iki özellik daha ekleyin. DSL'nizin tipik bir özelliği şöyle olabilir:

- Etki alanı sınıfı, öğeyi modele bağlayan ekleme ilişkisi, diyagramda o sınıfın öğelerini görüntülemek için gereken şekil ve kullanıcıların öğe oluşturmalarını sağlayan öğe aracı.

- Bir etki alanı sınıfının etki alanı özellikleri ve bunları bir şekilde görüntüleyen dekoratörler.

- Bir başvuru ilişkisi ve bunu diyagramda ve kullanıcıların bağlantı oluşturmalarına olanak sağlayan bağlayıcı aracında görüntüleyen bağlayıcı.

- Doğrulama kısıtlaması veya menü komutu gibi program kodu gerektiren bir özelleştirme.

  Aşağıdaki bölümlerde, dsl özelliklerinin en yararlı türleri oluşturma açıklanmaktadır. DSL'nin başka birçok deseni de vardır ancak bunlar en sık kullanılan desendir.

> [!NOTE]
> Bir özellik ekledikten sonra DSL'nizi derlemeden ve çalıştırmadan önce Çözüm Gezgini araç çubuğunda Tüm Şablonları Dönüştür'e tıklamayı unutmayın. 

 Aşağıdaki şekilde, dsl'nin bu konuda örnek olarak kullanılan bir parçası olan sınıflar ve ilişkiler yer almaktadır.

 ![Ekleme ve Başvuru ilişkileri](../modeling/media/music_classes.png)

 Aşağıdaki şekilde bu DSL'nin örnek bir modeli yer a tır:

 ![Oluşturulan DSL'nin örnek modeli](../modeling/media/music_instance.png)

> [!NOTE]
> "Model", kullanıcıların oluşturduğu dsl örneğinizi ifade eder ve genellikle diyagram olarak görüntülenir. Bu konuda hem DSL Tanımı diyagramı hem de DSL'niz kullanılırken görünen model diyagramları ele almaktadır.

## <a name="defining-domain-classes"></a><a name="classes"></a> Etki Alanı Sınıflarını Tanımlama
 Etki Alanı Sınıfları DSL'nizin kavramlarını temsil ediyor. Örnekler, model *öğeleridir.* Örneğin bir **MusicLibrary DSL'de,** Müzik ve Şarkı adlı Etki **Alanı Sınıflarınınız** **olabilir.**

 Bir etki alanı sınıfı oluşturmak için  Adlandırılmış Etki Alanı Sınıfı aracından diyagrama sürükleyip sınıfı yeniden adlandırabilirsiniz.

 Daha fazla bilgi için [bkz. Etki Alanı Sınıflarının Özellikleri.](../modeling/properties-of-domain-classes.md)

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Her Etki Alanı Sınıfı için Ekleme İlişkisi Oluşturma
 Kök sınıf dışındaki her etki alanı sınıfının en az bir ekleme ilişkisinin hedefi olması veya ekleme ilişkisinin hedefi olan bir sınıftan devralması gerekir.

 Modelde her model öğesi, ekleme ilişkilerinin tek bir ağacında yer alan bir düğüm olur. Ekleme ilişkisinin kaynağı ve hedefi genellikle üst ve alt öğe olarak adlandırılır.

 Bir etki alanı sınıfı için üst öğe seçimi, öğelerinin yaşam sürelerinin diğer öğelere nasıl bağımlı olması istediğinize bağlıdır. Bir ağacın düğümü silinirse, alt ağacı da genellikle silinir. Bu nedenle bağımsız bir varlığına sahip öğe sınıfları doğrudan kök sınıfının altına katıştırılmıştır.

 Genellikle, başka bir öğenin içinde bir öğe görüntülerseniz, bir sahip ilişkisini belirtmek istersiniz. Bu durumda, en uygun üst sınıf kapsayıcının sınıfıdır. Bunun istisnası, kapsayıcının içinde gördüğünüz öğenin aslında bağımsız bir öğenin başvuru bağlantısı olduğu durumdur. Bu durumda, kapsayıcı silindi, başvuru silindi ancak hedefi silindi.

 Bu konu başlığında açıklanan DSL tanımı düzenleri içinde, kapsayıcı silindiğinde kapsayıcı içinde görüntülenen öğelerin silinecek olduğunu varsayalım. Daha karmaşık şemalar mümkündür ve kurallar tanımlayarak elde edilebilir.

|Öğenin görüntülenme|Üst (ekleme) sınıfı|DSL Çözüm Şablonu örneği|
|-|-|-|
|Diyagram üzerinde şekil.<br /><br /> Swimlane.|DSL'nin kök sınıfı.|Minimum Dil.<br /><br /> Görev Flow: Aktör sınıfı.|
|Kulitikte şekillendirme.|Kullan olarak görüntülenen öğelerin etki alanı sınıfı.|Görev Flow: Görev sınıfı.|
|Şekilli listede yer alan ve kapsayıcı silinirse öğenin silin olduğu öğe.<br /><br /> Şeklin kenarında bağlantı noktası.|Kapsayıcı şekliyle eşlenen etki alanı sınıfı.|Sınıf diyagramı: Öznitelik sınıfı.<br /><br /> Bileşen diyagramı: Bağlantı noktası sınıfı.|
|Kapsayıcı silinirse listede yer alan öğe silinmez.|DSL'nin kök sınıfı.<br /><br /> Listede başvuru bağlantıları görüntülenir.||
|Doğrudan görüntülenmez.|Bölümü oluşturan sınıfı.||

 Müzik Kitaplığı örneğinde, Köşeler, Şarkı başlıklarının listelenmiş olduğu dikdörtgenler olarak görüntülenir. Bu nedenle, Şarkı'nın üst öğesi Music kök sınıfı, Song'ın üst öğesi ise Music'tir.

 Aynı anda bir etki alanı sınıfı ve onun eklemesini oluşturmak için Ekleme İlişkisi aracına tıklayın, ardından üst sınıfa tıklayın ve diyagramın boş bir parçasına tıklayın. 

 Sınıf adlarını otomatik olarak izleyeceklerinden, ekleme ilişkisinin ve rollerinin adını ayarlamak genellikle gerekli değildir.

 Daha fazla bilgi için [bkz. Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md) [ve Etki Alanı Rollerinin Özellikleri.](../modeling/properties-of-domain-roles.md)

> [!NOTE]
> Ekleme devralma ile aynı değildir. Ekleme ilişkisine sahip olan çocuklar, özellikleri üstlerinden devralmaz.

### <a name="add-domain-properties-to-each-domain-class"></a>Her Etki Alanı Sınıfına Etki Alanı Özellikleri Ekleme
 Etki alanı özellikleri değerleri depolar. Örnekler: Ad, Başlık, Yayın Tarihi.

 sınıfında **Etki Alanı** Özellikleri'ne tıklayın, ENTER tuşuna basın ve ardından bir özelliğin adını yazın. Bir etki alanı özelliğinin varsayılan türü Dize'dir. Türü değiştirmek için etki alanı özelliğini seçin ve Özellikler penceresinde **Tür'e** tıklayın.  Istediğiniz tür açılan listede yer alıyorsa bkz. [Özellik Türleri Ekleme.](#addTypes)

 **Öğe Adı özelliğini ayarlayın.** Dil gezgininde öğeleri tanımlamak için kullanılan bir etki alanı özelliği seçin. Örneğin, Song etki alanı sınıfında Title etki alanı özelliğini seçebilirsiniz. Özellikler penceresinde **Öğe** Adı **olarak** `true` ayarlayın.

### <a name="create-derived-domain-classes"></a>Türetilmiş Etki Alanı Sınıfları Oluşturma
 Bir etki alanı sınıfının özelliklerini ve ilişkilerini devralan varyantlara sahip olmak için, bundan türetilen sınıflar oluşturun. Örneğin, Bazında türetilen sınıflar WMA ve MP3 olabilir.

 Etki Alanı Sınıfı aracını kullanarak türetilmiş **sınıfı** oluşturun.

 Devralma **aracına** tıklayın, türetilmiş sınıfa tıklayın ve ardından temel sınıfa tıklayın.

 Temel sınıfın **Devralma Değiştiricisini soyut** olarak ayarlamayı göz önünde **bulundurabilirsiniz.** Temel sınıfın örneklerine ihtiyacınız olabileceğini düşünüyorsanız, bunun yerine onlar için ayrı bir türetilmiş sınıf oluşturmayı göz önünde bulundurarak.

 Türetilmiş sınıflar, temel sınıflarının özelliklerini ve rollerini devralabilir.

### <a name="tidy-the-dsl-definition-diagram"></a>DSL Tanım Diyagramını Düzenli Olarak Toplama
 İlişki eklerken sınıflardan bazıları birden fazla yerde görünür. Görünüm sayısını azaltmak ve diyagramı daha geniş hale getirmek için, bir ilişkinin hedef sınıfına sağ tıklayın ve ardından Ağacı Buraya **Getir'e tıklayın.** Ters etki için bir ilişkinin hedef sınıfına sağ tıklayın ve Ağacı **Böl'e tıklayın.** Bu menü komutlarını görmüyorsanız yalnızca etki alanı sınıfının seçili olduğundan emin olun.

 Etki alanı sınıflarını ve şekil sınıflarını taşımak için CTRL+Yukarı ve CTRL+Aşağı tuşlarını kullanın.

### <a name="test-the-domain-classes"></a>Etki alanı sınıflarını test etmek

##### <a name="to-test-the-new-domain-classes"></a>Yeni Etki Alanı Sınıflarını test etmek için

1. **DSL tasarımcısı kodunu oluşturmak için** Çözüm Gezgini araç çubuğunda Tüm Şablonları Dönüştür'e tıklayın. Bu adımı otomatikleştirin. Daha fazla bilgi için [bkz. How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **DSL'i derleme ve çalıştırma.** Deneysel modda yeni bir örnek çalıştırmak için F5 veya CTRL+F5 Visual Studio tuşlarına basın. Visual Studio örneğinde DSL'nizin dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Gezgin'i açın.** Diyagramın yan tarafında dil gezgini penceresi vardır ve bu pencere genellikle Dil Gezgini *olarak adlandırılmıştır.* Bu pencereyi görmüyorsanız bu pencere, pencerenin altındaki bir sekmede Çözüm Gezgini. Bu seçeneği bulamazsanız, **Görünüm menüsünde** Diğer Girişler'Windows üzerine **gelin** ve Ardından *Dil Gezgini'niz'e* **tıklayın.**

     Gezgininiz modelin ağaç görünümünü sunar.

4. **Yeni öğeler oluşturun.** En üstte kök düğüme sağ tıklayın ve ardından Yeni Sınıf **Ekle'ye**_tıklayın._

     Dil Gezgini'nde sınıfınıza yeni bir örnek görünür.

5. Yeni örnekler oluşturmanın her örneğin farklı bir adı olduğunu doğrulayın. Bu yalnızca bir etki alanı özelliğinde **Öğe Adı'dır** bayrağını ayarladıysanız oluşur.

6. **Etki alanı özelliklerini inceleme. Sınıfınıza bir örnek seçili durumdayken,** Özellikler penceresi. Bu etki alanı sınıfında tanımlandığı etki alanı özelliklerini göster olmalıdır.

7. **Dosyayı kaydedin, kapatın ve yeniden açın.** Oluşturduğunuz tüm örnekler, düğümleri genişletdikten sonra gezginde görünür olmalıdır.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Diyagramda Şekil Tanımlama
 Diyagramda görünen öğelerin sınıflarını dikdörtgen, üç nokta veya simge olarak tanımlayabilirsiniz.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Diyagramda şekil olarak görünen öğelerin sınıfını tanımlamak için

1. **Etki Alanı Sınıflarını Tanımlama konusunda açıklandığı gibi bir etki alanı sınıfı tanımlayın** ve test [etmek.](#classes)   

   - Sınıfın üst öğesi kök sınıf olmalı. Başka bir ifadeyle, kök sınıf ile yeni etki alanı sınıfı arasında bir ekleme ilişkisi olmalıdır.

   - Diyagramınızda kullanlar varsa üst öğe, kullana eşlenen etki alanı sınıfı olabilir. Bu yordama devam etmeden önce [bkz. Kullanlar olan bir DSL tanımlama.](#swimlanes)

2. **Model diyagramında öğeleri** temsil eden bir şekil sınıfı ekleyin. Aşağıdaki araçlardan birini DSL Tanım diyagramına sürükleyin:

   - **Geometri Şekli** bir dikdörtgen veya üç nokta sağlar.

   - **Görüntü Şekli,** sizin sağ istediğiniz bir görüntüyü görüntüler.

   - **Bölme Şekli,** bir veya daha fazla öğe listesi içeren bir dikdörtgendir.

     DSL Tanımı diyagramının sağ tarafında Şekiller ve Bağlayıcılar'ın altında görünecek şekil sınıfını yeniden adlandırabilirsiniz.

3. **Görüntü şekli oluşturduysanız bir görüntü tanımlayın.**

   1. Herhangi bir boyutta bir görüntü dosyası oluşturun. BMP, JPEG, GIF ve EMF biçimleri de desteklemektedir.

   2. Bu Çözüm Gezgini Dsl\Resources altındaki çözüme ekleyin.

   3. DSL Tanımı diyagramına geri dönüp yeni görüntü şekli sınıfını seçin.

   4. Aşağıdaki Özellikler penceresi **Image özelliğine** tıklayın.

   5. Görüntü **Seç iletişim** kutusunda Dosya adı altındaki açılan menüye **tıklayın ve** görüntüyü seçin.

4. **Etki alanı özelliklerini görüntülemek için şekle metin dekoratörleri ekleyin.**

    Model öğesinin adını veya başlığını görüntülemek için büyük olasılıkla en az bir metin dekoratörü gerekir.

    Şekil sınıfının üst bilgisini sağ tıklatın, Ekle'nin üzerine **gelin ve** ardından Metin **Dekoratörü'ne tıklayın.** Dekoratörün adını ve Özellikler penceresi olarak **ayarlayın.**

5. **Bağlan diyagram öğesi eşlemesi olan her bir şekli, görüntülemesi gereken etki alanı sınıfına eşler.**

    Diyagram Öğesi **Eşleme aracına** tıklayın, ardından etki alanı sınıfına ve ardından şekil sınıfına tıklayın.

6. **Özellikleri metin dekoratörlerine eşler.**

   1. Etki alanı sınıfı ile diyagram öğesi eşlemeyi temsil eden şekil sınıfı arasındaki gri çizgiyi seçin.

   2. DSL **Ayrıntıları penceresinde** Dekoratörün Görünüm **sekmesine Haritalar** tıklayın. **DSL** Ayrıntıları penceresini görmüyorsanız, Görünüm menüsünde Diğer Ayarlar'ın  üzerine gelin ve **Windows** DSL Ayrıntıları'ne **tıklayın.** Sık sık tüm içeriğini görmek için bu pencerenin üst kısmından yükseltmek gerekir.

   3. Dekoratör adını seçin. Display **özelliği altında,** etki alanı sınıfının bir özelliğinin adını seçin. Bunu her dekoratör için tekrarlayın.

       İlgili öğenin bir özelliğini görüntülemek için, özelliğini görüntülemek için Yol altındaki açılır ağaç **gezginine tıklayın.**

   4. Her dekoratör adının yanında bir onay işaretinin göründüğünden emin olun.

      ![Şekil Eşlemeleri ve DSL Ayrıntıları penceresi](../modeling/media/dsldetailswindow.png)

7. **Etki alanı sınıfının öğelerini oluşturmak için bir araç kutusu öğesi oluşturma.**

   1. **DSL Gezgini'nde** Düzenleyici **düğümünü** ve tüm alt düğümlerini genişletin.

   2. DSL'niz ile **aynı adı (örneğin** MusicLibrary) sahip Araç Kutusu Sekmeleri'nin altındaki düğüme sağ tıklayın. Öğe **Aracı Ekle'ye tıklayın.**

       > [!NOTE]
       > Araçlar düğümüne sağ **tıklarsanız** Öğe Aracı **Ekle'yi görmezsiniz.** Bunun yerine, üzerindeki düğüme tıklayın.

   3. Yeni Özellikler penceresi aracı seçiliyken, Sınıf'a **yakın** zamanda eklemiş olduğunu etki alanı sınıfı olarak ayarlayın.

   4. Resim **Yazısı ve** Araç **İpucu'nı ayarlayın.**

   5. Araç **Kutusu Simgesi'ne** araç kutusunda görünecek bir simge ayarlayın. Bunu yeni bir simgeye veya başka bir araç için zaten kullanılan bir simgeye ayarlayın.

        Yeni bir simge oluşturmak için Dsl\Resources'i **Çözüm Gezgini.** Var olan öğe aracı BMP dosyalarından birini kopyalayıp yapıştırın. Yapıştıran kopyayı yeniden adlandırın ve düzenlemek için çift tıklayın.

        DSL Tanımı diyagramına geri dönüp aracı seçin ve araç çubuğunda araç Özellikler penceresi **simgesine tıklayın** **.** Bit **Eşlem Seç** iletişim kutusunda, açılan .BMP dosyanızı seçin.

   Daha fazla bilgi için [bkz. Geometri Şekillerinin Özellikleri](../modeling/properties-of-geometry-shapes.md) [ve Görüntü Şekillerinin Özellikleri.](../modeling/properties-of-image-shapes.md)

#### <a name="to-test-shapes"></a>Şekilleri Test Etmek için

1. **DSL tasarımcısı kodunu oluşturmak için** Çözüm Gezgini araç çubuğunda Tüm Şablonları Dönüştür'e tıklayın.

2. **DSL'i derleme ve çalıştırma.** Deneysel modda yeni bir örnek çalıştırmak için F5 veya CTRL+F5 Visual Studio tuşlarına basın. Deneysel Visual Studio DSL'nizin dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Öğe araçlarının araç kutusunda görüntü olduğunu doğrulayın.**

4. **Bir araçtan** model diyagramına sürükleyerek şekiller oluşturun.

5. **Her metin dekoratörün görüntülendiğinden ve şunları** doğrulayın:

   1. Etki alanı özelliğinde Kullanıcı Arabirimi Salt Okunur **bayrağını ayarlamadıysanız** düzenleyebilirsiniz.

   2. Özelliği Özellikler penceresi veya dekoratörde düzenlerken diğer görünüm güncelleştirilir.

   Bir şekli ilk kez test ettikten sonra bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek iyi olabilir. Daha fazla bilgi için, [bkz. Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Başvuru İlişkilerini Tanımlama
 Herhangi bir kaynak etki alanı sınıfı ve herhangi bir hedef etki alanı sınıfı arasında bir başvuru ilişkisi tanımlayabilirsiniz. Başvuru ilişkileri genellikle diyagramda şekiller arasındaki çizgiler olan bağlayıcılar olarak görüntülenir.

 Örneğin, diyagramınızda Müzik Müzikleri ve Ressamlar şekil olarak görüntüleniyorsa ArtistsAppearedOnAlbums adlı bir ilişki tanımlayabilirsiniz. Bu ilişki, Artists'ı üzerinde çalıştıkları Sanatkarlara bağlar. Şekildeki örneğine bakın.

 ![Oluşturulan DSL'nin örnek modeli](../modeling/media/music_instance.png)

 Başvuru ilişkileri aynı türdeki öğeleri de bağlantılandırabilirsiniz. Örneğin, bir aile ağacını temsil eden DSL'de, ebeveynlerin ve çocuklarının arasındaki ilişki Kişiden Kişiye başvuru ilişkisidir.

### <a name="define-a-reference-relationship"></a>Başvuru İlişkisi Tanımlama
 Başvuru İlişkisi aracına tıklayın, ardından ilişkinin kaynak etki alanı sınıfına ve ardından hedef etki alanı sınıfına tıklayın. Hedef sınıf, kaynak sınıfla aynı olabilir.

 Her ilişkinin, ilişki kutusunun her tarafındaki çizgiyle temsil edilen iki rolü vardır. Her rolü seçerek bu rolün özelliklerini Özellikler penceresi.

 **rollerini yeniden anma düşünün.** Örneğin, Kişi ve Kişi arasındaki bir ilişkide, varsayılan adları Aile ve Çocuk, Yönetici ve Alt, Öğretmen ve Öğrenci olarak değiştirebilirsiniz.

 **Gerekirse, her rolün çoklulıklarını** ayarlayın. Her Bir Kişinin en fazla bir Yöneticiye sahip olduğunu görmek için diyagramda Yönetici etiketinin altında görünen çokluğu 0...1 olarak ayarlayın.

 **İlişkiye etki alanı özellikleri ekleyin.** Şekilde, ilişki Artist-Album rolün bir özelliği vardır.

 **Aynı sınıftan birden fazla bağlantı** aynı model öğeleri çifti arasında mevcutsa ilişkinin Yinelenenlere Izin Verir özelliğini ayarlayın. Örneğin, bir Öğretmen'in aynı Öğrenciye birden fazla Konu öğretmesine izin vesersiniz.

 ![Bağlayıcılar için şekil haritaları](../modeling/media/music_connector.png)

 Daha fazla bilgi için [bkz. Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md) [ve Etki Alanı Rollerinin Özellikleri.](../modeling/properties-of-domain-roles.md)

### <a name="define-a-connector-to-display-the-relationship"></a>İlişkiyi Görüntülemek için Bağlayıcı Tanımlama
 Bağlayıcı, model diyagramında iki şekil arasında bir çizgi görüntüler.

 Bağlayıcı **aracını** DSL tanım diyagramına sürükleyin.

 Bağlayıcıda etiketleri görüntülemek için metin dekoratörleri ekleyin. Konumlarını ayarlayın. Kullanıcının bir metin dekoratörü taşımasına izin için, Taşınabilir **özelliğini** ayarlayın.

 Bağlayıcıyı **başvuru ilişkisine** bağlamak için Diyagram Öğesi Eşleme aracını kullanın.

 Diyagram öğesi haritası seçiliyken **DSL** Ayrıntıları penceresini açın ve Dekoratör Haritalar **açın.**

 Her **dekoratörü seçin** ve **Display özelliğini doğru** etki alanı özelliği olarak ayarlayın.

 Dekoratörler listesinde her öğenin yanında bir onay işareti **göründüğünden emin** olun.

### <a name="define-a-connection-builder-tool"></a>Bağlantı Oluşturucu Aracı Tanımlama
 DSL **Gezgini penceresinde** Düzenleyici **düğümünü ve** tüm alt düğümlerini genişletin.

 DSL'niz ile aynı adı kullanan düğüme sağ tıklayın ve ardından Yeni Bağlantı Aracı **Ekle'ye tıklayın.**

 Yeni araç seçiliyken, Özellikler penceresi:

- Açıklamalı **Alt Yazı ve** Araç **İpucu'nı ayarlayın.**

- Bağlantı **Oluşturucu'ya** tıklayın ve yeni ilişki için uygun oluşturucu seçin.

- **Araç Kutusu Simgesi'ne** araç kutusunda görünmesini istediğiniz simgeyi ayarlayın. Bunu yeni bir simgeye veya başka bir araç için zaten kullanılan bir simgeye ayarlayın.

     Yeni bir simge oluşturmak için Dsl\Resources'i **Çözüm Gezgini.** Var olan öğe aracı BMP dosyalarından birini kopyalayıp yapıştırın. Yapıştıran kopyayı yeniden adlandırın ve düzenlemek için çift tıklayın.

     DSL Tanımı diyagramına geri dönüp aracı seçin ve araç çubuğunda araç Özellikler penceresi **simgesine tıklayın** **.** Bit **Eşlem Seç** iletişim kutusunda, açılan .BMP dosyanızı seçin.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Bir Başvuru İlişkisi ve Bağlayıcıyı Test Etmek için

1. **DSL tasarımcısı kodunu oluşturmak için** Çözüm Gezgini araç çubuğunda Tüm Şablonları Dönüştür'e tıklayın.

2. **DSL'i derleme ve çalıştırma.** Visual Studio yeni bir örneğini deneysel modda çalıştırmak için f5 veya CTRL + f5 tuşlarına basın. Visual Studio deneysel örneğinde, DSL 'niz dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Bağlantı aracının araç kutusunda göründüğünü doğrulayın.**

4. Bir araçtan model diyagramına sürükleyerek **şekiller oluşturun** .

5. Şekiller arasında **bağlantı oluşturun** . Bağlayıcı aracına tıklayın, bir şekle tıklayın ve ardından başka bir şekle tıklayın.

6. **Uygunsuz sınıflar arasında bağlantı oluşturmediğinizi doğrulayın.** Örneğin, ilişkiniz albümler ve sanatçı arasındaysa, sanatçıların sanatçıların bağlantısını doğrulayabildiğinizi doğrulayın.

7. **Çeşitlilimler doğru olduğundan emin olun. Örneğin, bir kişiyi birden fazla yöneticiye bağlayabildiğinizi doğrulayın.**

8. **Her metin dekoratın göründüğünü** ve şunları doğrulayın:

   1. Etki alanı özelliğinde **Kullanıcı arabirimi salt okuma** bayrağını ayarlamadığınız takdirde düzenleyebilirsiniz.

   2. Özelliği Özellikler penceresi veya dekoratör içinde düzenlediğinizde, diğer görünüm güncellenir.

   Bir bağlayıcıyı ilk kez test ettikten sonra bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Listeler Içeren şekilleri tanımlama: bölme şekilleri
 Bir bölme şekli bir veya daha fazla öğe listesi içerir. Örneğin, bir müzik kitaplığı DSL 'de, müzik albümlerini temsil etmek için bölme şekillerini kullanabilirsiniz. Her albümdeki şarkıların bir listesi vardır.

 ![Bölme şekli](../modeling/media/compartmentshape.png)

 Bu etkiyi bir DSL tanımında elde etmek için en basit yöntemde, kapsayıcı için bir etki alanı sınıfı ve her bir liste için bir etki alanı sınıfı tanımlarsınız. Kapsayıcı sınıfı, bölme şekline eşlenir.

 ![Şekil haritası](../modeling/media/music_mapcomp.png)

 Daha fazla bilgi için bkz. [bölme şekillerinin özellikleri](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Bir bölme şekli tanımlamak için

1. **Kapsayıcı etki alanı sınıfını oluşturun**. **Ilişki ekleme** aracına tıklayın, modelin kök sınıfına tıklayın ve ardından DSL tanımı diyagramının boş bir kısmına tıklayın. Bu, örnek şekilde albüm olarak adlandırılan etki alanı sınıfını oluşturur.

     Alternatif olarak, kök sınıfına eklemek yerine kapsayıcıyı bir Kulvar ile eşlenmiş bir etki alanı sınıfına ekleyebilirsiniz.

     Sınıfa ad gibi bir etki alanı özelliği ekleyin ve Özellikler penceresi **öğe adı** bayrağını ayarlayın.

2. **Liste öğesi alanı sınıfını oluşturun**. **Ilişki ekleme** aracına tıklayın, kapsayıcı sınıfına (albüm) tıklayın ve ardından diyagramın boş bir kısmına tıklayın. Bu, örnek şekilde Song adlı etki alanı sınıfını oluşturur.

     Sınıfa başlık gibi bir etki alanı özelliği ekleyin ve **öğesinin öğe adı** bayrağını ayarlayın.

     Diğer etki alanı özelliklerini ekleyin.

     Göstermek istediğiniz her bir liste için başka bir liste öğesi alan sınıfı ekleyin.

3. **Listedeki birçok öğe türünü karıştırmak için**, liste sınıfından kalıtımla alan sınıflar oluşturun. **Devralma değiştiricisini** ayarlayarak liste sınıfını soyut hale getirin.

     Örneğin, klasik müziğin sanatçı yerine besteci olarak sıralanmasını istiyorsanız, bir şarkının iki alt sınıfı, ClassicalSong ve NonClassicalSong oluşturabilirsiniz.

4. **Bölme şeklini oluşturun**. **Bölme şekli** aracından DSL tanımı diyagramına sürükleyin.

     Bir metin dekoratörü ekleyin ve adını ayarlayın.

     Bir bölme ekleyin ve adını ayarlayın.

5. Kullanıcının liste bölmeleri gizlemesini sağlamak için, bölme şekli sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **dekoratör ' ı Genişlet/Daralt**' a tıklayın. Özellikler penceresi dekoratör konumunu ayarlayın.

6. **Diyagram öğesi eşleme** aracına tıklayın, kapsayıcı etki alanı sınıfına tıklayın ve sonra bölme şekline tıklayın.

7. Etki alanı sınıfı ve şekil arasındaki diyagram öğe eşleme bağlantısını seçin. **DSL ayrıntıları** penceresinde:

    1. **Dekoratörler** sekmesine tıklayın. Dekoratör adına tıklayın ve ardından **görüntü özelliği** altında uygun öğeyi seçin. Dekoratör adının yanında bir onay işaretinin göründüğünden emin olun.

    2. **bölme Haritalar** sekmesine tıklayın.

         Bölme adına tıklayın.

         **Görüntülenmiş öğeler koleksiyonu yolu**' nun altında, liste öğesi sınıfına (Song) gidin. Açılan oka tıklayarak gezgin aracını kullanın.

         **Görüntü özelliği** altında, listede gösterilmesi gereken özelliği seçin. Örnekte, bu başlıktır.

> [!NOTE]
> Dekoratör eşleme ve bölme eşleme alanlarındaki yol alanlarını kullanarak, etki alanı sınıfları ve bölme şekli arasında daha karmaşık ilişkiler yapabilirsiniz.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Şekli oluşturmak için bir araç tanımlamak için

1. **Alan sınıfının öğelerini oluşturmak için bir araç kutusu öğesi oluşturun.**

2. **DSL Gezgini**' nde, **Düzenleyici** düğümünü ve tüm alt düğümlerini genişletin.

3. DSL ile aynı ada sahip **araç kutusu sekmeleri** altındaki düğüme sağ tıklayın, örneğin, MusicLibrary. **Öğe Ekle aracı**' na tıklayın.

    > [!NOTE]
    > **Araçlar** düğümüne sağ tıklarsanız, **öğe Ekle aracını** görmezsiniz. Bunun yerine, yukarıdaki düğüme tıklayın.

4. Yeni öğe aracı seçiliyken Özellikler penceresi, **sınıfı** en son eklediğiniz etki alanı sınıfına ayarlayın.

5. **Açıklamalı altyazı** ve **araç ipucu** ayarlayın.

6. **Araç kutusu simgesini** araç kutusunda görünecek bir simgeye ayarlayın. Bunu yeni bir simge veya başka bir araç için zaten kullanılan bir simge olarak ayarlayabilirsiniz.

     Yeni bir simge oluşturmak için, **Çözüm Gezgini**'de Dsl\Resources dosyasını açın. Mevcut öğe aracından birini kopyalayıp .BMP yapıştırın. Yapıştırılan kopyayı yeniden adlandırın ve ardından düzenlemek için çift tıklayın.

     DSL tanımı diyagramına dönün, aracı seçin ve Özellikler penceresi **araç kutusu simgesinde** **[...]** simgesine tıklayın. **Bit eşlem Seç** iletişim kutusunda, AÇıLAN menüden BMP dosyanızı seçin.

#### <a name="to-test-a-compartment-shape"></a>Bir bölme şeklini test etmek için

1. DSL Tasarımcısı kodu oluşturmak için Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür ' e tıklayın** .

2. **DSL derleyin ve çalıştırın.** Visual Studio yeni bir örneğini deneysel modda çalıştırmak için f5 veya CTRL + f5 tuşlarına basın. Visual Studio deneysel örneğinde, DSL 'niz dosya adı uzantısına sahip bir dosya açın veya oluşturun.

3. **Aracın araç kutusunda göründüğünü doğrulayın.**

4. Aracı model diyagramının üzerine sürükleyin. Bir şekil oluşturulur.

    Öğenin adının göründüğünü ve varsayılan değere otomatik olarak ayarlandığını doğrulayın.

5. Yeni şeklin üst bilgisine sağ tıklayın ve sonra *liste öğesini* Ekle ' ye tıklayın. Örnekte, komut şarkı ekleyin.

    Listede bir öğenin göründüğünü ve yeni bir ada sahip olduğunu doğrulayın.

6. Liste öğelerinden birine tıklayın ve ardından Özellikler penceresi inceleyin. Liste öğelerinin özelliklerini görmeniz gerekir.

7. Dil Gezginini açın. İçindeki liste öğesi düğümleri ile kapsayıcı düğümlerini görebildiğinizi doğrulayın.

   ![DSL Gezgini oluşturuldu](../modeling/media/music_explorer.png)

   Bir bölme şeklini ilk kez test ettikten sonra bazı özelliklerini ayarlamak ve daha gelişmiş özellikler eklemek isteyebilirsiniz. Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Bir bölme içinde başvuru bağlantısı görüntüleme
 Genellikle, bir bölme içinde görüntülenen bir öğe, bölme şekli tarafından temsil edilen öğenin bir alt öğesidir. Ancak bazen bir başvuru ilişkisiyle bağlantılı bir öğeyi göstermek istersiniz.

 Örneğin, albümle bağlantılı sanatçıların listesini görüntüleyen albümle şekle ikinci bir bölme ekleyebiliriz.

 Bu durumda, Bölüm başvurulan öğesi yerine bağlantıyı görüntülemelidir. Bunun nedeni, kullanıcının bölmedeki öğeyi seçtiği ve DELETE 'e bastığı, bağlantının başvurulan öğenin değil, silinmesini istediğiniz bir öğesidir.

 Bununla birlikte, başvurulan öğenin adının bölmesinde görünmesini sağlayabilirsiniz.

 Aşağıdaki yordam, bu bölümün önceki kısımlarında açıklandığı gibi, etki alanı sınıfını, başvuru ilişkisini, bölme şeklini ve diyagram öğesi haritasını zaten oluşturmuş olduğunuzu varsayar.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Bir bölmedeki başvuru bağlantısını görüntüleme

1. **Bölme şekline bir bölme ekleyin**. DSL tanımı diyagramında bölme şekli sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve **bölme**' ya tıklayın.

2. **Görüntülenecek Öğeler koleksiyon yolunu** , hedef öğesi yerine bağlantısına gitmek için ayarlayın. Açılan menüye tıklayın ve ağaç görünümünü kullanarak, hedefi yerine başvuru ilişkisini seçin. Örnekte, ilişki **Artistappearedonalbümler**' dir.

3. Hedef öğeye olan bağlantıdan gezinmek için **görüntülenecek özelliğin yolunu** ayarlayın. Örnekte, bu **sanatçı**' dır.

4. **Display özelliğini** , örneğin **Name** gibi Target öğesinin uygun özelliğine ayarlayın.

5. **Tüm şablonları dönüştürün**, DSL oluşturup çalıştırın ve bir test modeli açın.

6. Model diyagramında uygun şekil sınıflarını oluşturun, adlarını ayarlayın ve aralarında bir bağlantı oluşturun. Bölme şeklinin içinde, bağlantılı öğelerin adları görünmelidir.

7. Bağlantı ya da bölme şeklindeki öğeyi seçin. Hem bağlantı hem de öğe kaybolmalıdır.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Başka bir şeklin sınırında bağlantı noktalarını tanımlama
 Bağlantı noktası, başka bir şeklin sınırında bulunan bir şekildir.

 Bağlantı noktaları, başka bir şekle, kullanıcının bağlayıcılar çizebileceği bir sabit bağlantı noktası sağlamak için de kullanılabilir. Bu durumda, bağlantı noktası şeklini saydam hale getirebilirsiniz.

 Bağlantı noktalarını kullanan bir örneği görmek için yeni bir DSL çözümü oluştururken **bileşen diyagramı** şablonunu seçin. Bu örnek, bağlantı noktalarını tanımlarken göz önünde bulundurmanız gereken ana noktaları gösterir:

- Bağlantı noktalarının kapsayıcısını temsil eden bir etki alanı sınıfı vardır `Component` .

- Bağlantı noktalarını temsil eden bir etki alanı sınıfı vardır. Örnekte, bu `ComponentPort` .

- Kapsayıcı etki alanı sınıfından bağlantı noktası etki alanı sınıfına bir katıştırma ilişkisi vardır. Daha fazla bilgi için bkz. [etki alanı sınıfları tanımlama](#classes).

- Farklı bağlantı noktası türlerinin aynı kapsayıcıda karışık olmasını istiyorsanız, bağlantı noktası etki alanı sınıfının alt sınıflarını oluşturabilirsiniz. Örnekte, ve ' `InPort` `OutPort` den devralma `ComponentPort` .

- Kapsayıcı etki alanı sınıfı herhangi bir şekil türüne eşlenebilir. Örnekte, `ComponentShape` . Daha fazla bilgi için bkz. [şekilleri tanımlama](#shapes).

- Bağlantı noktası etki alanı sınıfları bağlantı noktası şekillerine eşlenir. Türetilmiş sınıfları, bağlantı noktası şekil sınıflarını ayrı ayrı eşleyebilirsiniz veya temel sınıfı bir bağlantı noktası şekil sınıfına eşleyebilirsiniz.

  Diğer bir durumda, bağlantı noktası şekilleri [şekilleri tanımlama](#shapes)bölümünde açıklandığı gibi davranır.

  Daha fazla bilgi için bkz. [bağlantı noktası şekillerinin özellikleri](../modeling/properties-of-port-shapes.md).

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Kulvarları olan bir DSL tanımlama
 Kulvarlar bir diyagramın yatay veya dikey bölümüdür. Her kulvar bir model öğesine karşılık gelir. DSL tanımınız, kulvar öğeleri için bir etki alanı sınıfı gerektirir.

 kulvarlar ile DSL oluşturmanın en iyi yolu, yeni bir dsl çözümü oluşturmak ve görev Flow çözüm şablonunu kullanmaktır. DSL tanımında aktör sınıfı, kulvara eşlenen etki alanı sınıfıdır. Bu ve diğer sınıfları projenize uyacak şekilde yeniden adlandırın.

 Kulvar içinde şekil olarak görüntülenecek bir sınıf eklemek için, kulvar sınıfı ve yeni sınıfınız arasında bir katıştırma Ilişkisi oluşturun. Kullanıcılar öğeleri bir kulvardan diğerine sürükleyebilir, ancak her öğe her zaman belirli bir Kulvar içinde yer alacak. görev Flow çözüm şablonunda, flowelement, kulvar sınıfının bir alt öğesidir.

 Kulvarlardan bağımsız olarak bir şekil olarak görüntülenecek bir sınıf eklemek için, kök sınıf ve yeni sınıfınız arasında bir katıştırma Ilişkisi oluşturun. Kullanıcılar bu şekilleri diyagram üzerinde herhangi bir yere yerleştirebilir, kulvarların sınırları ve kulvarların dışında yer alır. görev Flow çözüm şablonunda, açıklama kök sınıfının bir alt öğesidir.

 Daha fazla bilgi için bkz. [kulvarların özellikleri](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Özellik türleri ekleme

### <a name="domain-enumerations-and-literals"></a>Etki alanı numaralandırmaları ve sabit değerleri
 Etki alanı numaralandırması, birden çok değişmez değer içeren bir türdür.

 Bir etki alanı numaralandırması eklemek için, **DSL Gezgininde** modelin köküne sağ tıklayın ve ardından **yeni etki alanı numaralandırması Ekle**' ye tıklayın. Öğesi, **etki alanı türleri** düğümünün altında **DSL Gezgini** 'nde görünür. Bu öğe diyagramda görünmüyor.

 Etki alanı numaralandırmasında sabit listesi sabit değerleri eklemek için **DSL Gezgininde** etki alanı numaralandırması ' ne sağ tıklayın ve ardından **Yeni sabit listesi sabit değeri Ekle**' ye tıklayın.

 Varsayılan olarak, bir numaralandırma türüne sahip bir özellik, bir kerede numaralandırmanın yalnızca bir değerine ayarlanabilir. Kullanıcıların ve programcıların herhangi bir değer birleşimini ayarlayabilmesini istiyorsanız-bir "bit alanı"-numaralandırmanın **IsFlags** özelliğini ayarlayın.

### <a name="external-types"></a>Dış türler
 Bir etki alanı özelliğinin türünü ayarladığınızda, **tür** açılır listesinde istediğiniz türü bulamazsanız, bir dış tür ekleyebilirsiniz. Örneğin, **System. Drawing. Color** türünü listeye ekleyebilirsiniz.

 Bir tür eklemek için, DSL Gezgini ' nde modelin köküne sağ tıklayın ve sonra **yeni dış tür Ekle**' ye tıklayın. Özellikler penceresi, adı **Color** ve ad alanı olarak **System. Drawing** olarak ayarlayın. Bu tür artık DSL Gezgini 'nde **etki alanı türleri** altında görüntülenir. Bir etki alanı özelliğinin türünü her ayarladığınızda bunu seçebilirsiniz.

## <a name="customizing-the-dsl"></a><a name="custom"></a> DSL 'yi özelleştirme
 Bu konuda açıklanan teknikleri kullanarak, bir diagrammatik gösterimi, okunabilir bir XML formu ve kod ve diğer yapıtları oluşturmak için gereken temel araçları kullanarak hızlı bir şekilde DSL oluşturabilirsiniz.

 DSL tanımını genişletmenin iki yöntemi vardır:

1. DSL tanımının daha fazla özelliğini kullanarak DSL 'yi hassas olarak ayarlayın. Örneğin, birden çok bağlayıcı türü oluşturabileceğiniz tek bir bağlayıcı aracı oluşturabilirsiniz ve bir öğenin silinmesi ile ilgili öğeleri de sildiği kuralları kontrol edebilirsiniz. Bu teknikler, genellikle DSL tanımındaki değerler ayarlanarak elde edilir ve bazıları bazı program kodu satırları gerektirir.

     Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Daha gelişmiş etkiler elde etmek için program kodunu kullanarak modelleme araçlarınızı genişletin. Örneğin, modeli değiştirecek menü komutları oluşturabilir ve iki veya daha fazla DSLs 'yi tümleştiren araçlar oluşturabilirsiniz. VMSDK, uzantılarınızı DSL tanımından oluşturulan kodla tümleştirmeyi kolaylaştırmak için özel olarak tasarlanmıştır.  Daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>DSL tanımını değiştirme
 Bir DSL tanımında herhangi bir öğe oluşturduğunuzda, çoğu varsayılan değer otomatik olarak ayarlanır. Ayarlandıklarında, bunları değiştirebilirsiniz. Bu, bir DSL geliştirmeyi basitleştirir, ancak yine de güçlü özelleştirmeler sağlar.

 Örneğin, bir şekli bir öğesiyle eşleştirdiğinizde, eşlemenin üst öğe yolu, etki alanı sınıfının katıştırma ilişkisine göre otomatik olarak ayarlanır. Ancak, daha sonra ekleme ilişkisini değiştirirseniz, üst öğe yolu otomatik olarak değiştirilmez.

 Bu nedenle, DSL tanımınızdaki bazı ilişkileri değiştirdiğiniz zaman, tanımı kaydettiğinizde ya da tüm şablonları dönüştürdüğünüzde hatalar için olağandışı değildir. Bu hataların çoğunun düzeltilmesi kolay bir işlemdir. Hatanın konumunu görmek için hata raporuna çift tıklayın.

 Ayrıca bkz. [nasıl yapılır: Domain-Specific dilin ad alanını değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Sorunu
 Aşağıdaki tabloda, bir DSL tasarlarken karşılaşılan en yaygın sorunların bazıları, çözümüne yönelik önerilerle birlikte listelenmiştir. [Görselleştirme araçları genişletilebilirlik forumundan](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx)daha fazla öneri bulabilirsiniz.

| Sorun | Öneri |
|-|-|
| DSL tanımı dosyasında yaptığım değişikliklerin etkisi yoktur. | Çözüm Gezgini yukarıdaki araç çubuğundan **Tüm Şablonları Dönüştür** ' e tıklayın ve ardından çözümü yeniden derleyin. |
| Şekiller, özellik değeri yerine bir dekoratörün adını gösterir. | Dekoratör eşlemesini ayarlayın. DSL tanımı diyagramında, alan sınıfı ve şekil sınıfı arasındaki gri çizgi olan diyagram öğe haritasına tıklayın.<br /><br /> **DSL ayrıntıları** penceresini açın. bunu göremiyorsanız, görünüm menüsünde **diğer Windows**' ın üzerine gelin ve **DSL ayrıntıları**' na tıklayın.<br /><br /> **dekoratör Haritalar** sekmesine tıklayın. Dekoratör adını seçin. Yanındaki kutunun işaretli olduğundan emin olun. **Görüntü özelliği** altında, bir etki alanı özelliğinin adını seçin.<br /><br /> Daha fazla bilgi için bkz. [diyagramdaki şekiller](#shapes). |
| DSL Gezgini 'nde bir koleksiyona ekleyemiyorum. Örneğin, araçlara sağ tıkladığınızda menüdeki "araç ekle" komutu yoktur.<br /><br /> DSL için Gezgininde bir listeye öğe ekleyemiyorum. | Denediğiniz düğümün üstündeki öğeye sağ tıklayın. Bir listeye eklemek istediğinizde, Add komutu liste düğümünde değil, kendi sahibidir. |
| Bir etki alanı sınıfı oluşturdum, ancak dil Gezgini 'nde örnek oluşturamıyorum. | Kök hariç her etki alanı sınıfı, bir katıştırma ilişkisinin hedefi olmalıdır. |
| DSL için Gezgininde öğeler yalnızca tür adlarıyla gösterilir. | DSL tanımında, sınıfının bir etki alanı özelliğini seçin ve Özellikler penceresi, **öğe adı** ' nı true ' olarak ayarlayın. |
| DSL her zaman XML düzenleyicisinde açılır. | Dosya okunurken bir hata nedeniyle bu durum oluşabilir. Ancak, bu hatayı düzelttikten sonra bile düzenleyiciyi DSL tasarımcısı olarak açıkça sıfırlamanız gerekir.<br /><br /> Proje öğesine sağ tıklayın, **birlikte Aç** ' a tıklayın ve * YourLanguage ***Tasarımcı (varsayılan)** seçeneğini belirleyin. |
| Derleme adlarını değiştirdikten sonra DSL 'nin araç kutusu görünmüyor. | İnceleme ve güncelleştirme **DslPackage\GeneratedCode\Package.tt** daha fazla bilgi için bkz. [nasıl yapılır: Domain-Specific dilin ad alanını değiştirme](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md). |
| DSL araç kutusu görünmüyor, ancak derleme adını değiştirdim.<br /><br /> Ya da bir uzantı yükleme başarısızlığını bildiren bir ileti kutusu görüntülenir. | Deneysel örneği sıfırlayın ve çözümünüzü yeniden derleyin.<br /><br /> 1. Windows Başlat menüsü **tüm programlar** altında, araçlar ' ı genişletin [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] ve ardından  **Microsoft Visual Studio deneysel örneği sıfırla**' ya tıklayın.<br />2. **Yapı** menüsünde **çözümü yeniden derle**' ye tıklayın. |

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dillerle Çalışmaya Başlama](../modeling/getting-started-with-domain-specific-languages.md)
- [Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [WPF Tabanlı Etki Alanına Özgü Dil Oluşturma](../modeling/creating-a-wpf-based-domain-specific-language.md)
