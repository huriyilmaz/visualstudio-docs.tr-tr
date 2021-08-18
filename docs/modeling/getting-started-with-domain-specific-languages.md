---
title: Etki Alanına Özgü Dillerle Çalışmaya Başlama
description: Visual Studio için modelleme SDK 'Sı ile oluşturulan, etki alanına özgü dili (DSL) tanımlama ve kullanma konusunda temel kavramları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8c9e471f3e72568ceb60c3831357548201b69433
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061304"
---
# <a name="get-started-with-domain-specific-languages"></a>Alana Özgü Dilleri Kullanmaya Başlama

Bu konuda, Visual Studio için modelleme SDK 'Sı ile oluşturulmuş bir etki alanına özgü dili (DSL) tanımlama ve kullanma konusundaki temel kavramlar açıklanmaktadır.

> [!NOTE]
> metin şablonu dönüştürme sdk 'sı ve Visual Studio modelleme sdk 'sı, Visual Studio belirli özelliklerini yüklediğinizde otomatik olarak yüklenir. Daha ayrıntılı bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)bakın.

DSLs 'yi yeni Deneyiyorsanız, bu sitede bulabileceğiniz **dsl araçları Laboratuvarı** aracılığıyla çalışmanızı öneririz: [görselleştirme ve modelleme SDK 'sı](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Domain-Specific diliyle ne yapabilirsiniz?

Etki alanına özgü dil, genellikle grafik olan ve belirli bir amaç için kullanılmak üzere tasarlanan bir gösterimidir. Bunun aksine, UML gibi dillerin genel amaçlı olması gerekir. Bir DSL 'de model öğesi türlerini ve bunların ilişkilerini ve bunların ekranda nasıl sunulduğunu tanımlayabilirsiniz.

bir DSL tasarladıktan sonra, Visual Studio tümleştirme uzantısı (vsıx) paketinin bir parçası olarak dağıtabilirsiniz. Kullanıcılar Visual Studio içindeki DSL ile çalışır:

![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

Gösterim yalnızca DSL 'nin bir parçasıdır. Gösterimle birlikte, VSıX paketiniz kullanıcıların, modellerinden malzemeleri düzenlemeye ve oluşturmaya yardımcı olmak için uygulayabileceğiniz araçları içerir.

DSLs 'nin asıl uygulamalarından biri program kodu, yapılandırma dosyaları ve diğer yapıtları oluşturmak için kullanılır. Özellikle büyük projelerde ve ürün satırlarında, bir ürünün çeşitli varyantlarının oluşturulması durumunda, DSLs 'deki değişken yönlerinin birçoğu, güvenilirlikte büyük bir artış ve gereksinimler değişikliklerine çok hızlı yanıt verebilir.

Bu genel bakışın geri kalanında, Visual Studio ' de alana özgü dil oluşturma ve kullanma ile ilgili temel işlemleri tanıtan bir izlenecek yol vardır.

## <a name="prerequisites"></a>Önkoşullar

Bir DSL tanımlamak için aşağıdaki bileşenleri yüklemiş olmanız gerekir:

| Bileşen | Bağlantı |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [https://go.microsoft.com/fwlink/?linkid=2166172](../extensibility/visual-studio-sdk.md) |
| Visual Studio için SDK modelleme | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>DSL çözümü oluşturma

yeni bir etki alanına özgü dil oluşturmak için, Domain-Specific language proje şablonunu kullanarak yeni bir Visual Studio çözümü oluşturursunuz.

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

2. **Project türleri** altında **diğer Project türleri** düğümünü genişletin ve **genişletilebilirlik**' e tıklayın.

3. **Alana özgü dil Tasarımcısı**' ye tıklayın.

     ![DSL oluştur iletişim kutusu](../modeling/media/create_dsldialog.png)

4. **Ad** kutusuna **FamilyTree** yazın. **Tamam**'a tıklayın.

     **Etki alanına özgü dil Sihirbazı** açılır ve şablon DSL çözümlerinin listesini görüntüler.

     Açıklamaları görmek için her şablona tıklayın,

     Şablonlar, yararlı başlangıç noktalarıdır. Bunların her biri, gereksinimlerinize uyacak şekilde düzenleyebileceğiniz, tamamlanmış bir çalışan DSL sağlar. Normalde, oluşturmak istediğiniz en yakın şablonu seçersiniz.

5. Bu izlenecek yol için **en az dil** şablonunu seçin.

6. Uygun sihirbaz sayfasında DSL 'niz için bir dosya adı uzantısı girin. Bu, DSL 'nin örneklerini içeren dosyaların kullanacağı uzantıdır.

    - Bilgisayarınızdaki herhangi bir uygulamayla veya DSL 'yi yüklemek istediğiniz herhangi bir bilgisayarda ilişkilendirilmemiş bir uzantı seçin. Örneğin, **docx** ve **htm** kabul edilemez dosya adı uzantıları olacaktır.

    - Girdiğiniz uzantı DSL olarak kullanılıyorsa, sihirbaz sizi uyarır. Farklı bir dosya adı uzantısı kullanmayı düşünün. ayrıca, eski deneysel tasarımcıları temizlemek için Visual Studio SDK deneysel örneğini sıfırlayabilirsiniz. **başlat**' a tıklayın, **tüm programlar**, **Microsoft Visual Studio 2010 SDK** ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 deneysel örneğini sıfırlayın**.

7. Diğer sayfaları inceleyin ve ardından **son**' a tıklayın.

     İki proje içeren bir çözüm oluşturulur. Bunlar DSL ve DslPackage olarak adlandırılır. DslDefinition. dsl adlı bir diyagram dosyası açılır.

    > [!NOTE]
    > İki projedeki klasörlerde görebileceğiniz kodun çoğu DslDefinition. dsl ' den oluşturulmuştur. Bu nedenle, bu dosyada DSL 'niz üzerinde yapılan çoğu değişiklik yapılır.

Kullanıcı arabirimi artık aşağıdaki resme benzer.

![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

Bu çözüm, etki alanına özgü bir dili tanımlar. Daha fazla bilgi için bkz. [Domain-Specific dil Araçları Kullanıcı arabirimine genel bakış](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>DSL çözümünün önemli bölümleri

Yeni çözümün aşağıdaki yönlerini görürsünüz:

- **Dsl\dsldefinition.exe** Bu, bir DSL çözümü oluştururken gördüğünüz dosyadır. Çözümdeki kodun neredeyse tamamı bu dosyadan oluşturulmuştur ve DSL tanımında yaptığınız değişikliklerin çoğu burada yapılır. Daha fazla bilgi için bkz. [DSL tanımı diyagramı Ile çalışma](../modeling/working-with-the-dsl-definition-diagram.md)ile çalışma.

- **DSL projesi** Bu proje, etki alanına özgü dili tanımlayan kodu içerir.

- **DslPackage projesi** Bu proje, Visual Studio içinde DSL örneklerinin açılmasına ve düzenlenmesine izin veren kodu içerir.

## <a name="running-the-dsl"></a><a name="Debugging"></a> DSL 'yi çalıştırma

DSL çözümünü, oluşturduktan hemen sonra çalıştırabilirsiniz. Daha sonra, her değişiklikten sonra çözümü yeniden çalıştırarak DSL tanımını kademeli olarak değiştirebilirsiniz.

### <a name="to-experiment-with-the-dsl"></a>DSL 'yi denemek için

1. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın. Bu, kaynak kodun büyük bölümünü DslDefinition. dsl 'den yeniden oluşturur.

    > [!NOTE]
    > *DslDefinition. dsl*'yi her değiştirdiğinizde, çözümü yeniden oluşturmadan önce **Tüm Şablonları Dönüştür** ' e tıklamanız gerekir. Bu adımı otomatik hale getirebilirsiniz. Daha fazla bilgi için bkz. [tüm şablonları dönüştürmeyi otomatikleştirme](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **F5** tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.

     DSL derlemeleri ve Visual Studio deneysel örneğine yüklenir.

     deneysel bir Visual Studio örneği başlar. deneysel örnek, Visual Studio uzantılarının hata ayıklama amacıyla kaydedildiği, ayarlarını kayıt defterinin ayrı bir alt ağacında alır. Normal Visual Studio örnekleri orada kayıtlı uzantılara erişemez.

3. Visual Studio deneysel örneğinde, **Çözüm Gezgini** **Test** adlı model dosyasını açın.

     \- veya

     Hata ayıklama projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **öğe**' ye tıklayın. **Öğe Ekle** iletişim kutusunda, DSL 'nizin dosya türünü seçin.

     Model dosyası boş bir diyagram olarak açılır.

     Araç kutusu açılır ve diyagram türüne uygun araçları görüntüler.

4. Diyagram üzerinde şekiller ve bağlayıcılar oluşturmak için araçları kullanın.

    1. Şekil oluşturmak için örnek Şekil aracı diyagramda sürükleyin.

    2. İki şekli bağlamak için, örnek bağlayıcı aracına tıklayın, ilk şekle tıklayın ve ardından ikinci şekle tıklayın.

5. Bunları değiştirmek için şekillerin etiketlerine tıklayın.

deneysel Visual Studio aşağıdaki örneğe benzeyecektir:

![Visual Studio etki alanına özgü dil örneği ağacı](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Bir modelin Içeriği

Bir DSL örneği olan bir dosyanın içeriğine *model* denir. *Model* <em>öğeleri</em> ve öğeler arasındaki *bağlantıları* içerir. DSL tanımı, modelde model öğesi ve bağlantı türlerinin ne tür bir bulunabilir olduğunu belirtir. Örneğin, minimum dil şablonundan oluşturulan bir DSL 'de, bir tür model öğesi ve bir bağlantı türü vardır.

DSL tanımı, modelin diyagram üzerinde nasıl göründüğünü belirtebilir. Birçok şekil ve bağlayıcı stili arasından seçim yapabilirsiniz. Bazı şekillerin diğer şekillerin içinde görünmesini sağlayabilirsiniz.

Bir modeli düzenlediğinizde, bir modeli **Gezgin** görünümünde ağaç olarak görüntüleyebilirsiniz. Diyagrama şekil eklerken, model öğeleri de gezgin 'de görüntülenir. Gezgin, diyagram yoksa bile kullanılabilir.

Visual Studio hata ayıklama örneğinde Gezgin'i görmüyorsanız, Görünüm  menüsünde Diğer **Windows'nin** üzerine gelin ve ardından Gezgin'e *\<Your Language>* **tıklayın.**

### <a name="the-api-of-your-dsl"></a>DSL'nizin API'si

DSL'niz, DSL örnekleri olan modelleri okumanızı ve güncelleştirmenizi sağlayan bir API oluşturur. API'nin bir uygulaması, modelden metin dosyaları oluşturmaktır. Daha fazla bilgi için [bkz. T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)Metin Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma.

Hata ayıklama çözümünde şablon dosyalarını ".tt" uzantısıyla açın. Bu örnekler modellerden metin oluşturma ve DSL'nizin API'sini test edin. Örneklerden biri içinde, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] diğeri içinde [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] yazılmıştır.

Her şablon dosyasının altında, bu dosya oluşturulur. Şablon dosyasını dosyanın Çözüm Gezgini ve oluşturulan dosyayı açın.

Şablon dosyası, modelde tüm öğeleri listeleen kısa bir kod kesimi içerir.

Oluşturulan dosya sonucu içerir.

Bir model dosyasını değiştirdikten sonra, dosyaları yeniden üretdikten sonra, oluşturulan dosyalarda buna karşılık gelen değişiklikleri gösterir.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Model dosyasını değiştirdikten sonra metin dosyalarını yeniden oluşturma

1. Deneysel Visual Studio model dosyasını kaydedin.

2. Her .tt dosyasındaki dosya adı parametresinin denemeler için kullanmakta olduğu model dosyasına başvurduğundan emin olun. .tt dosyasını kaydedin.

3. öğesinin **araç çubuğunda Tüm** Şablonları Dönüştür'e **Çözüm Gezgini.**

     \- veya -

     Yeniden oluşturmak istediğiniz şablonlara sağ tıklayın ve ardından Özel Aracı **Çalıştır'a tıklayın.**

Bir projeye istediğiniz sayıda metin şablonu dosyası eklemek için kullanabilirsiniz. Her şablon bir sonuç dosyası oluşturur.

> [!NOTE]
> DSL tanımını değiştirdikçe, güncelleştirmedikçe örnek metin şablonu kodu çalışmaz.

Daha fazla bilgi için [bkz. Domain-Specific Dilinden](../modeling/generating-code-from-a-domain-specific-language.md) Kod Oluşturma ve Domain-Specific [Dili Özelleştirmek için Kod Yazma.](../modeling/writing-code-to-customise-a-domain-specific-language.md)

## <a name="customizing-the-dsl"></a>DSL'i özelleştirme

DSL tanımını değiştirmek istediğiniz zaman deneysel örneği kapatın ve ana örnek örneğinde Visual Studio güncelleştirin.

> [!NOTE]
> DSL tanımını değiştirdikten sonra, önceki sürümleri kullanarak oluşturduğunuz test modellerinde bilgileri kaybedebilirsiniz.  Örneğin, hata ayıklama çözümü bazı şekiller ve bağlayıcılar içeren Sample adlı bir dosya içerir. DSL tanımınızı geliştirmeye başladıktan sonra bunlar görünmez ve dosyayı kaydeddikten sonra kaybolur.

DSL'niz için çok çeşitli uzantılar yapabilirsiniz. Aşağıdaki örnekler size olasılıklar hakkında bir izlenim verir.

Her değişiklik sonrasında DSL tanımını  kaydedin, Çözüm Gezgini'de Tüm Şablonları Dönüştür'e tıklayın ve değiştirilen DSL ile deneme yapmak için **F5** tuşuna basın. 

### <a name="rename-the-types-and-tools"></a>Türleri ve Araçları Yeniden Adlandırma

Mevcut etki alanı sınıflarını ve ilişkilerini yeniden adlandırabilirsiniz. Örneğin, Minimum Dil şablonundan oluşturulan dsl tanımından başlayarak, DSL'nin aile ağaçlarını temsil etmelerini sağlamak için aşağıdaki yeniden adı oluşturma işlemlerini gerçekleştirebilirsiniz.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Etki alanı sınıflarını, ilişkilerini ve araçlarını yeniden adlandırmak için

1. DslDefinition diyagramında, **ExampleModel'i** **FamilyTreeModel,** **ExampleElement** olarak  **Kişi,** **Hedefler** Ve Kaynaklar'ı **Alt** Olarak yeniden **adlandırabilirsiniz.** Her etikete tıklar ve bu etiketi değiştirebilirsiniz.

     ![DSL Tanımı diyagramı &#45; ağaç modeli](../modeling/media/familyt_person.png)

2. Öğesini ve bağlayıcı araçlarını yeniden adlandırabilirsiniz.

    1. DSL Gezgini penceresini açmak için aşağıdaki sekmeye Çözüm Gezgini. Bunu görmüyorsanız, Görünüm menüsünde Diğer **Seçenekler'in** üzerine gelin **Windows** DSL Gezgini'ne **tıklayın.** DSL Gezgini yalnızca DSL Tanım diyagramı etkin pencere olduğunda görünür.

    2. Aynı Özellikler penceresi DSL Gezgini'ni ve Özellikler'i aynı anda görmek için dosyayı açın ve konum olarak değiştirin.

    3. DSL Gezgini'nde Düzenleyici, **Araç** Kutusu **Sekmeleri**, *\<your DSL>* ve ardından Araçlar'ı **genişletin.**

    4. ExampleElement **'e tıklayın.** Bu, öğeleri oluşturmak için kullanılan araç kutusu öğesidir.

    5. Aşağıdaki Özellikler penceresi Name **özelliğini Kişi** olarak **değiştirebilirsiniz.**

         Caption özelliğinin **de değiştiklerini** unutmayın.

    6. Aynı şekilde **ExampleConnector** aracının adını **ParentLink olarak değiştirebilirsiniz.** Caption **özelliğini** Name özelliğinin bir kopyası olacak şekilde değiştirebilirsiniz. Örneğin Üst Bağlantı **girin.**

3. DSL'yi yeniden oluşturma.

    1. DSL Tanım dosyasını kaydedin.

    2. Uygulamanın **araç çubuğunda Tüm** Şablonları Dönüştür'e Çözüm Gezgini

    3. F5 tuşuna basın. Deneysel Visual Studio bekleyin.

4. Visual Studio'nin deneysel örneğinde hata ayıklama çözümünde bir test modeli dosyası açın. Öğeleri araç kutusundan üzerine sürükleyin. DSL Gezgini'nde araç açıklamalı alt yazıları ve tür adlarının değiştiklerini fark edin.

5. Model dosyasını kaydedin.

6. Bir .tt dosyası açın ve eski tür ve özellik adlarının oluşumlarını yeni adlarla değiştirin.

7. .tt dosyasında belirtilen dosya adının test modelinizi belirttiğinizden emin olun.

8. .tt dosyasını kaydedin. Kodu .tt dosyasında çalıştırmanın sonucu görmek için oluşturulan dosyayı açın. Doğru olduğunu doğrulayın.

### <a name="add-domain-properties-to-classes"></a>Sınıflara Etki Alanı Özellikleri Ekleme
 Bir kişinin doğum ve ölüm yıllarını temsil etmek gibi bir etki alanı sınıfına özellikler ekleyin.

 Yeni özellikleri diyagramda görünür yapmak için model *öğesini* görüntüleyen şekle dekoratörler eklemeniz gerekir. Ayrıca özellikleri dekoratörlere eşlemelisiniz.

##### <a name="to-add-properties-and-display-them"></a>Özellik eklemek ve bunları görüntülemek için

1. Özellikleri ekleyin.

   1. DSL Tanımı diyagramında Kişi etki alanı sınıfına sağ **tıklayın, Ekle'nin** üzerine **gelin** ve ardından Etki Alanı **Özelliği'ne tıklayın.**

   2. Doğum ve Ölüm gibi yeni özellik adlarının **listesini** **yazın.** Her **birinin ardından Enter** tuşuna basın.

2. Şeklin özelliklerini görüntüleyen dekoratörler ekleyin.

   1. Person etki alanı sınıfından diyagramın diğer tarafına genişletilen gri satırı izleyin. Bu bir diyagram öğesi eşlemesidir. Etki alanı sınıfını bir şekil sınıfına bağlar.

   2. Bu şekil sınıfına sağ tıklayın, Ekle'nin **üzerine gelin** ve Ardından Metin **Dekoratörü'ne tıklayın.**

   3. **BirthDecorator ve DeathDecorator** gibi adlara sahip **iki dekoratör ekleyin.**

   4. Her yeni dekoratörü seçin ve Özellikler penceresi alanını **ayarlayın.** Bu, etki alanı özellik değerinin şekil üzerinde nerede görüntü olacağını belirler. Örneğin, **InnerBottomLeft ve** **InnerBottomRight'ı ayarlayın.**

        ![Bölme şekli tanımı](../modeling/media/familyt_compartment.png)

3. Dekoratörleri özelliklerle eşler.

   1. DSL Ayrıntıları penceresini açın. Genellikle Çıkış penceresinin yanındaki bir sekmededir. Bunu görmüyorsanız, Görünüm  menüsünde Diğer girişler'in **üzerine gelin Windows** DSL Ayrıntıları'ne **tıklayın.**

   2. DSL tanım diyagramında Kişi etki alanı sınıfını **şekil** sınıfına bağlayan satıra tıklayın.

   3. **DSL Ayrıntıları'nın** **Dekoratör Haritalar,** eşlenmemiş bir dekoratörde onay kutusuna tıklayın. Görüntüleme **Özelliği'nin** altında, eşlensin istediğiniz etki alanı özelliğini seçin. Örneğin, **BirthDecorator ile Doğum** **eşle.**

4. DSL'yi kaydedin, Tüm Şablonları Dönüştür'e tıklayın ve F5 tuşuna basın.

5. Örnek model diyagramında, seçtiğiniz konumlara tıklar ve değerler yazabilirsiniz. Buna ek olarak, Kişi şeklini **seçerek** Özellikler penceresi ve Ölüm özelliklerini görüntüler.

6. Bir .tt dosyasında, her bir kişinin özelliklerini alan kod eklersiniz.

   ![Aile ağacı diyagramı, araç kutusu ve gezgin](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Yeni Sınıflar Tanımlama
 Bir modele etki alanı sınıfları ve ilişkiler ekleyebilirsiniz. Örneğin, kasaları temsil eden yeni bir sınıf ve kasadaki bir kişinin süreli olduğunu temsil eden yeni bir ilişki oluşturabilirsiniz.

 Farklı türleri bir model diyagramında farklı hale getirmek için, etki alanı sınıflarını farklı şekil türlerine veya farklı geometri ve renklere sahip şekillere eşleyebilirsiniz.

##### <a name="to-add-and-display-a-new-domain-class"></a>Yeni bir etki alanı sınıfı ekleme ve görüntüleme

1. Bir etki alanı sınıfı ekleyin ve model kökünün alt öğesi yapın.

    1. DSL tanımı diyagramında, **katıştırma ilişkisi** aracına tıklayın, **FamilyTreeModel** kök sınıfına tıklayın ve ardından diyagramın boş bir kısmına tıklayın.

         Yeni bir etki alanı sınıfı görünür, bu, bir katıştırma ilişkisi ile FamilyTreeModel 'e bağlanır.

         Adını (örneğin, **Town**) ayarlayın.

        > [!NOTE]
        > Modelin kökü hariç her etki alanı sınıfı, en az bir katıştırma ilişkisinin hedefi olmalıdır veya bir gömmenin hedefi olan bir sınıftan devralması gerekir. Bu nedenle, ekleme Ilişkisi aracı 'nı kullanarak bir etki alanı sınıfı oluşturmak sıklıkla kullanışlıdır.

    2. Yeni sınıfa bir etki alanı özelliği ekleyin, örneğin **adı**.

2. Kişi ve şehir arasında bir başvuru ilişkisi ekleyin.

    1. **Başvuru ilişkisi** aracına tıklayın, kişi ' ye ve ardından şehir ' e tıklayın.

         ![DSL tanım parçası: aile ağacı kökü](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Başvuru ilişkileri, model ağacının bir bölümünden diğerine çapraz başvuruları temsil eder.

3. Model diyagramlarında kasabalarında şubeleri 'yi temsil edecek bir şekil ekleyin.

    1. Araç kutusundan bir **geometri şeklini** diyagrama sürükleyin ve örneğin, **TownShape** gibi yeniden adlandırın.

    2. Özellikler penceresi, yeni şeklin, Fill Color ve Geometry gibi görünüm alanlarını ayarlayın.

    3. Town adını göstermek için bir dekoratörü ekleyin ve ad dekoratörü 'nı yeniden adlandırın. Position özelliğini ayarlayın.

4. Town etki alanı sınıfını Kasanşekle eşleyin.

    1. **Diyagram öğesi eşleme** aracına tıklayın, ardından Town etki alanı sınıfına ve ardından TownShape şekil sınıfına tıklayın.

    2. harita bağlayıcısı seçiliyken **DSL ayrıntıları** penceresinin **dekoratör Haritalar** sekmesinde, namedekorator ' ı işaretleyin ve **Display özelliğini** Name olarak ayarlayın.

5. Kişi ve Kasans arasındaki ilişkiyi göstermek için bir bağlayıcı oluşturun.

    1. Araç kutusundan bir bağlayıcıyı diyagrama sürükleyin. Yeniden adlandırıp görünüm özelliklerini ayarlayın.

    2. Yeni bağlayıcıyı kişi ve şehir arasındaki ilişkiye bağlamak için **diyagram öğesi eşleme** aracını kullanın.

         ![Eklenmiş Şekil haritası ile aile ağacı tanımı](../modeling/media/familyt_shapemap.png)

6. Yeni bir şehir oluşturmak için bir öğe aracı oluşturun.

    1. **DSL Gezgini**' nde **Düzenleyici** ve **araç kutusu sekmeleri**' ni genişletin.

    2. Sağ tıklayın *\<your DSL>* ve ardından **Yeni öğe Ekle aracı**' na tıklayın.

    3. Yeni aracının **Name** özelliğini ayarlayın ve **sınıf** özelliğini Town olarak ayarlayın.

    4. **Araç kutusu simgesi** özelliğini ayarlayın. **[...]** Simgesine tıklayın ve **dosya adı** alanında bir simge dosyası seçin.

7. Kasabalarında şubeleri ve kişiler arasında bağlantı oluşturmak için bir bağlayıcı aracı oluşturun.

    1. Sağ tıklayın *\<your DSL>* ve ardından **yeni bağlayıcı aracı ekle**' ye tıklayın.

    2. Yeni aracın ad özelliğini ayarlayın.

    3. **ConnectionBuilder** özelliğinde Person-Town ilişkisinin adını içeren oluşturucuyu seçin.

    4. **Araç kutusu simgesini** ayarlayın.

8. DSL tanımını kaydedin, **Tüm Şablonları Dönüştür**' e tıklayın ve **F5** tuşuna basın.

9. Visual Studio deneysel örneğinde bir test modeli dosyası açın. Kasabalarında şubeleri ve kişiler arasında kasalar ve bağlantılar oluşturmak için yeni araçları kullanın. Yalnızca doğru öğe türleri arasında bağlantı oluştururıbildiğinize dikkat edin.

10. Her birinin yaşadığı kasayı listeleyen kodu oluşturun. Metin şablonları, bu tür kodları çalıştırabileceğiniz yerlerden biridir. Örneğin, hata ayıklama çözümünde varolan Sample.tt dosyasını aşağıdaki kodu içerecek şekilde değiştirebilirsiniz:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     *. Tt dosyasını kaydettiğinizde, kişilerin listesini ve bunların onların listesini içeren bir yan kuruluş dosyası oluşturacaktır. Daha fazla bilgi için bkz. [Domain-Specific dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Doğrulama ve komutlar
 Doğrulama kısıtlamaları ekleyerek bu DSL 'yi daha da geliştirebilirsiniz. Bu kısıtlamalar, modelin doğru bir durumda olduğundan emin olmak için tanımlayabileceğiniz yöntemlerdir. Örneğin, bir alt öğenin Doğum tarihinin üst öğelerinden daha sonra olduğundan emin olmak için bir kısıtlama tanımlayabilirsiniz. DSL kullanıcısı kısıtlamaların herhangi birini kesen bir model kaydetmeye çalışırsa doğrulama özelliği bir uyarı görüntüler. Daha fazla bilgi için bkz. [Domain-Specific dilinde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 Kullanıcının çağırabileceği menü komutlarını da tanımlayabilirsiniz. Komutları modeli değiştirebilir. ayrıca, Visual Studio ve dış kaynaklarla diğer modellerle etkileşime girebilirler. Daha fazla bilgi için bkz. [nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>DSL dağıtma
 diğer kullanıcıların etki alanına özgü dili kullanmasına izin vermek için bir Visual Studio uzantısı (vsıx) dosyası dağıtırsınız. Bu, DSL çözümünü yapılandırdığınızda oluşturulur.

 Çözümünüzün bin klasöründe. vsix dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın. Bu bilgisayarda VSıX dosyasına çift tıklayın. DSL, bu bilgisayardaki tüm Visual Studio örneklerinde kullanılabilir.

 Aynı yordamı kullanarak DSL 'yi kendi bilgisayarınıza yükleyebilirsiniz. bu sayede Visual Studio Deneysel örneğini kullanmanız gerekmez.

 Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Eski deneysel DSLs 'ler kaldırılıyor
 artık istemediğiniz deneysel dsls 'leri oluşturduysanız, Visual Studio deneysel örneğini sıfırlayarak bunları bilgisayarınızdan kaldırabilirsiniz.

 bu, bilgisayarınızdan tüm deneysel dsls 'leri ve diğer deneysel Visual Studio uzantılarını kaldırır. Bunlar hata ayıklama modunda yürütülen uzantılardır.

 bu yordam, vsıx dosyası çalıştırılarak tamamen yüklenmiş olan dsls 'leri veya diğer Visual Studio uzantılarını kaldırmaz.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio deneysel örneği sıfırlamak için

1. **başlat**' a tıklayın, **tüm programlar**, **Microsoft Visual Studio 2010 SDK** ve **araçlar**' a tıklayın ve ardından **Microsoft Visual Studio 2010 deneysel örneğini sıfırlayın**.

2. hala kullanmak istediğiniz deneysel dsls 'leri veya diğer deneysel Visual Studio uzantılarını yeniden derleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
