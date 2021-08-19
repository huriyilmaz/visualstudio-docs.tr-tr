---
title: DslDefinition.dsl Dosyası
description: DslDefinition.dsl dosyasının yapısı hakkında bilgi edinmek için etki alanına özgü bir dil tanımlayan DSL Araçları çözümünün Dsl projesini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c31d6b6b5cc1c1542c27b15af4e6ee741272c3d8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085357"
---
# <a name="the-dsldefinitiondsl-file"></a>DslDefinition.dsl Dosyası

Bu konuda, bir çözümün Dsl projesinde bulunan ve etki alanına özgü bir dili tanımlayan DslDefinition.dsl [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] *dosyasının yapısı açıklanmıştır.* DslDefinition.dsl dosyası, etki alanına özgü bir dilin sınıflarını ve ilişkilerini, etki alanına özgü dilin ve düzenleme araçlarının diyagram, şekiller, bağlayıcılar, serileştirme biçimi ve **Araç** Kutusu ile birlikte açıklar. Etki alanına özgü bir dil çözümünde, bu araçları tanımlayan kod DslDefinition.dsl dosyasındaki bilgilere göre oluşturulur.

Genellikle, DslDefinition.dsl *Alana Özgü Dil Tasarımcısı* için Alana Özgü Dil Tasarımcısı dosyasını kullanırsanız. Ancak, ham biçimi XML'tir ve bir XML düzenleyicisinde DslDefinition.dsl dosyasını açabilirsiniz. Dosyanın hangi bilgileri içerdiğini ve hata ayıklama ve uzantı amaçları için nasıl düzenleniyor olduğunu anlamanız yararlı olabilir.

Bu konudaki örnekler Bileşen Diyagramı çözüm şablonundan alındır. Bir örneği görmek için Bileşen Modelleri çözüm şablonunu temel alan etki alanına özgü bir dil çözümü oluşturun. Çözümü oluşturdukta, DslDefinition.dsl dosyası Domain-Specific Dil Tasarımcısı'nda görünür. Dosyasını kapatın, dosyada sağ tıklayın, **Çözüm Gezgini aç'ın** üzerine **gelin,** **XML Düzenleyicisi'ne** tıklayın ve ardından Tamam'a **tıklayın.**

## <a name="sections-of-the-dsldefinitiondsl-file"></a>DslDefinition.dsl Dosyasının Bölümleri

kök öğesidir ve öznitelikleri etki alanına özgü dilin adını, ad alanını ve sürüme yönelik ana ve \<Dsl> ikincil sürüm numaralarını belirtir. Şema, `DslDefinitionModel` geçerli bir DslDefinition.dsl dosyasının içeriğini ve yapısını tanımlar.

Kök öğenin \<Dsl> alt öğeleri aşağıdaki gibidir:

### <a name="classes"></a>Sınıflar

Bu bölüm, oluşturulan kodda bir sınıf oluşturan her etki alanı sınıfını tanımlar.

### <a name="relationships"></a>İlişkiler

Bu bölüm modelde her ilişkiyi tanımlar. Kaynak ve hedef, bir ilişkinin iki tarafını temsil ediyor.

### <a name="types"></a>Türler

Bu bölüm her türü ve ad alanını tanımlar. Etki alanı özellikleri iki türe sahiptir. `DomainEnumerations` modelde tanımlanır ve DomainModel.cs içinde türler oluşturulur. `ExternalTypes` başka bir yerde tanımlanan türlere (veya `String` gibi) bakın `Int32` ve hiçbir şey oluşturmaz.

### <a name="shapes"></a>Şekiller

Bu bölüm, modelin tasarımcıda nasıl göründüğüne açıklayan şekilleri tanımlar. Bu geometrik şekiller Diyagram bölümündeki model sınıflarına eşlenmiş.

### <a name="connectors"></a>Bağlayıcılar

Bu bölüm, bir tasarımcıda görünen bağlayıcıların görünümünü tanımlar. Bu geometrik stil açıklamaları Diyagram bölümündeki modelde yer alan belirli ilişkilerle eşlenmiş.

### <a name="xmlserializationbehavior"></a>Xmlserializationbehavior

Bu bölüm bir serileştirme şeması tanımlar ve her sınıfın bir dosyaya nasıl kaydedildikleri hakkında ek bilgi sağlar.

### <a name="explorerbehavior"></a>Explorerbehavior

Bu bölüm, kullanıcı **bir modeli düzenlerken DSL** Gezgini penceresinin nasıl görüntülendiğinden tanımlar.

### <a name="connectionbuilders"></a>ConnectionBuilders

Bu bölüm, her bağlayıcı aracı için bir bağlantı oluşturucu tanımlar (bağlanacak iki sınıf arasında bağlantı oluşturma aracı). Bu bölüm, bir kaynakla hedef sınıf arasında bağlantı kurıp bağlanamayabilirsiniz.

### <a name="diagram"></a>Diyagram

Bu bölüm bir diyagram tanımlar ve bunu arka plan rengi ve kök sınıfı gibi özellikleri belirtmek için kullanırsiniz. (Kök sınıf, diyagram tarafından bir bütün olarak temsil edilen etki alanı sınıfıdır.) Diyagram bölümü, her bir etki alanı sınıfını veya ilişkisini temsil eden şekli veya bağlayıcıyı belirten ShapeMap ve ConnectorMap öğelerini de içerir.

### <a name="designer"></a>Tasarımcı

Bu bölüm bir Araç Kutusu, doğrulama **ayarları,** diyagram ve serileştirme şemasını bir araya getiren bir tasarımcıyı (düzenleyici) tanımlar. Tasarımcı bölümü ayrıca modelin kök sınıfını da tanımlar ve bu da genellikle diyagramın kök sınıfıdır.

### <a name="explorer"></a>Gezgin

Bu bölüm **DSL** Gezgini davranışını tanımlar (XmlSerializationBehavior bölümünde tanımlanır).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>DslDefinition.dsl dosyasındaki bilinen adlar

DslDefinition.dsl dosyası boyunca, belirli öğelere çapraz başvurular yapmak için bilinen adlar kullanabilirsiniz. Örneğin, her İlişki tanımı bir Kaynak alt bölüm ve bir Hedef alt bölüm içerir. Her alt bölüm, bu ilişkiyle bağlanebilecek nesne sınıfının bilinen adı içerir:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Genellikle, başvurulan öğenin ad alanı (bu örnekte, etki alanı sınıfı) başvuran öğeyle aynıdır (bu örnekte `Library` LibraryHasMembers etki alanı ilişkisi). Bu gibi durumlarda, bilinen ad yalnızca sınıfın adını vermektedir. Aksi takdirde, /Namespace/Name tam formunu kullanabilirsiniz:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Bilinen ad sistemi, XML ağacında eşlerin ayrı adlara sahip olması gerekir. Bu nedenle, örneğin aynı adla iki sınıfa sahip olan etki alanına özgü bir dil tanımını kaydetmeye çalışsanız doğrulama hataları oluşur. DslDefinition.dsl dosyasını daha sonra doğru şekilde yeniden yükleyebilirsiniz.

Her türün kendi bilinen adı türü vardır: DomainClassMoniker, DomainRelationshipMoniker ve diğer.

## <a name="types"></a>Türler

Türler bölümü DslDefinition.dsl dosyasının içerdiği tüm türleri özellik türleri olarak belirtir. Bu türler iki türe sahiptir: System.String gibi dış türler ve numaralu türler.

### <a name="external-types"></a>Dış Türler

Bileşen Diyagramı örneğinde standart temel türler listelese de, yalnızca bazıları kullanılır.

Her Dış Tür tanımı yalnızca bir ad ve Dize ve Sistem gibi bir ad alanı içerir:

```xml
<ExternalType Name="String" Namespace="System" />
```

Türlerin tam adları, "string" gibi eşdeğer derleyici anahtar sözcükleri yerine kullanılır.

Dış türler standart kitaplık türleriyle sınırlı değildir.

### <a name="enumerations"></a>Listelemeler

Tipik bir Numaralama belirtimi şu örnekteki gibi olur:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

özniteliği, oluşturulan kodun ön ek olarak Common Language Runtime (CLR) özniteliğinin ek verisi ekli olup olmadığını kontrol eder. Bu öznitelik, numaralama değerlerinin bit olarak birleştirip `IsFlags` `[Flags]` birleştirileneceğni belirler. Bu öznitelik true olarak ayarlanırsa, değişmez değerler için iki güç değeri belirtmeniz gerekir.

## <a name="classes"></a>Sınıflar

Etki alanına özgü bir dilin herhangi bir tanımında yer alan öğelerin çoğu doğrudan veya dolaylı olarak `DomainClass` örneğidir. , , ve `DomainClass` alt `DomainRelationship` `Shape` `Connector` sınıflarını `Diagram` içerir. `Classes`DslDefinition.dsl dosyasının bölümünde etki alanı sınıfları listelemektedir.

Her sınıfın bir özellik kümesi vardır ve bir temel sınıfı olabilir. Bileşen Diyagramı örneğinde, `NamedElement` türü dize olan bir özelliği olan soyut bir `Name` sınıftır:

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement`, 'den devralınan özelliğine ek olarak kendi özelliklerine sahip olan gibi `Component` `Name` diğer sınıflardan birkaçıdır. `NamedElement` BaseClass alt düğümü bir bilinen ad başvurusu içerir. Başvurulan sınıf aynı ad alanı içinde olduğundan, bilinen ad için yalnızca adı gereklidir:

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Her etki alanı sınıfı (ilişkiler, şekiller, bağlayıcılar ve diyagramlar dahil) şu özniteliklere ve alt düğümlere sahip olabilir:

- **Kimlik.** Bu öznitelik bir GUID'dir. Dosyada bir değer sağlanmayacaksa, Domain-Specific Dil Tasarımcısı bir değer oluşturacak. (Bu belgede yer kazanmak için bu öznitelik genellikle atlanır.)

- **Ad ve Ad Alanı.** Bu öznitelikler, oluşturulan kodda sınıfının adını ve ad alanını belirtir. Bunlar birlikte etki alanına özgü dilde benzersiz olmalıdır.

- **InheritanceModifier.** Bu öznitelik "soyut", "korumalı" veya hiçbiridir.

- **Displayname.** Bu öznitelik, Özellikler penceresinde görünen **addır.** DisplayName özniteliği boşluklar ve diğer noktalama işaretleri içerebilir.

- **GeneratesDoubleDerived.** Bu öznitelik true olarak ayarlanırsa, iki sınıf oluşturulur ve biri diğerin alt sınıfıdır. Oluşturulan tüm yöntemler tabandadır ve oluşturucular alt sınıfa dahil edilir. Bu özniteliği ayarerek, özel kodda oluşturulan herhangi bir yöntemi geçersiz kılabilirsiniz.

- **HasCustomConstructor**. Bu öznitelik true olarak ayarlanırsa, oluşturucu oluşturulan koddan atlanır, böylece kendi sürümlerinizi yazabilirsiniz.

- **Öznitelikler**. Bu öznitelik, oluşturulan sınıfın CLR Özniteliklerini içerir.

- **BaseClass**. Bir temel sınıf belirtirsiniz, aynı türde olması gerekir. Örneğin, bir etki alanı sınıfının temeli olarak başka bir etki alanı sınıfı ve bölme şekli bir bölme şekline sahip olmalıdır. Temel bir sınıf belirtmezseniz, oluşturulan kodda sınıfı standart bir çerçeve sınıfından türetir. Örneğin, bir etki alanı sınıfı ' den `ModelElement` türetildi.

- **Özellikler .** Bu öznitelik, işlem denetimi altında bakımı yapılan ve model kaydediken kalıcı olan özellikleri içerir.

- **ElementMergeDirectives**. Her öğe birleştirme yönergesi, başka bir sınıfın farklı bir örneğinin üst sınıfın bir örneğine nasıl ekli olduğunu kontrol eder. Bu konunun devamlarında öğe birleştirme yönergeleri hakkında daha fazla ayrıntı bulabilirsiniz.

- bölümünde listelenen her etki alanı sınıfı için bir C# sınıfı `Classes` oluşturulur. C# sınıfları Dsl\GeneratedCode\DomainClasses.cs içinde oluşturulur.

### <a name="properties"></a>Özellikler

Her etki alanı özelliğinin bir adı ve türü vardır. Ad, etki alanı sınıfı ve geçişli tabanları içinde benzersiz olmalıdır.

Tür, bölümünde listelenenlerden birini ifade `Types` etmek gerekir. Genellikle, bilinen ad alanı içermesi gerekir.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Her etki alanı özelliği şu özniteliklere de sahip olabilir:

- **IsBrowsable**. Bu öznitelik, kullanıcı üst sınıfın bir **nesnesine** tıkladığında özelliğin Özellikler penceresinde görünür olup olmadığını belirler.

- **IsUIReadOnly**. Bu öznitelik, kullanıcının Özellikler penceresinde veya  özelliğin sun olduğu bir dekoratör aracılığıyla özelliği değiştirip değiştiremeyeceklerini belirler.

- **Tür:**. Bu özniteliği Normal, Hesaplanan veya CustomStorage olarak ayarlayın. Bu özniteliği Hesaplanan olarak belirlersanız, değeri belirleyen özel kod sağlayabilirsiniz ve özellik salt okunur olur. Bu özniteliği CustomStorage olarak ayarlarsanız, hem değerleri alan hem de ayaran kod sağlayabilirsiniz.

- **IsElementName**. Bu öznitelik true olarak ayarlanırsa, üst sınıfın bir örneği oluşturulduğunda değeri otomatik olarak benzersiz bir değere ayarlanır. Bu öznitelik, her sınıfta bir dize türü olması gereken tek bir özellik için true olarak ayarlandırabilirsiniz. Bileşen Diyagramı örneğinde özelliği `Name` `NamedElement` true olarak `IsElementName` ayarlanmıştır. Kullanıcı bir öğe `Component` oluşturduğunda (öğesinden devralan), ad otomatik olarak `NamedElement` "Component6" gibi bir adla başlatılır.

- `DefaultValue`. Bu özniteliği belirttiysanız, belirttiğiniz değer bu sınıfın yeni örnekleri için bu öznitelike atanır. `IsElementName`ayarlanırsa, DefaultValue özniteliği yeni dizenin ilk bölümünü belirtir.

- **Kategori,** özelliğin Özellikler penceresinde görünt olduğu üst **bilgidir.**

## <a name="relationships"></a>İlişkiler

bölümünde, `Relationships` etki alanına özgü dil ile tüm ilişkiler listelene bir liste yer almaktadır. Her `Domain Relationship` biri ikilidir ve kaynak sınıfın üyelerini hedef sınıfın üyelerine bağlar. Kaynak ve hedef sınıflar genellikle etki alanı sınıflarıdır, ancak diğer ilişkilerle ilişkilere de izin verilir.

Örneğin, Bağlantı ilişkisi OutPort sınıfının üyelerini InPort sınıfının üyelerine bağlar. İlişkinin her bağlantı örneği bir OutPort örneğini bir InPort örneğine bağlar. İlişki çoka çok olduğundan, her OutPort içinde kaynakları olan birçok Bağlantı bağlantısı olabilir ve her InPort örneğinde onu hedef alan birçok Bağlantı bağlantısı olabilir.

### <a name="source-and-target-roles"></a>Kaynak ve hedef roller

Her ilişki, aşağıdaki özniteliklere sahip kaynak ve hedef rolleri içerir:

- özniteliği `RolePlayer` bağlı örneklerin etki alanı sınıfına başvurur: Kaynak için OutPort, hedef için InPort.

- Özniteliğin `Multiplicity` dört olası değeri vardır (ZeroMany, ZeroOne, One ve OneMany). Bu öznitelik, bu ilişkinin bir rol oynatıcısı ile ilişkilendirilen bağlantı sayısını ifade eder.

- özniteliği, `PropertyName` diğer uçta yer alan nesnelere erişmek role playing sınıfında kullanılan adı belirtir. Bu ad, ilişkide çapraz geçiş yapmak için şablonda veya özel kodda kullanılır. Örneğin, kaynak `PropertyName` rolün özniteliği olarak `Targets` ayarlanır. Bu nedenle, aşağıdaki kod çalışır:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Kural gereği, çokluğun ZeroMany veya OneMany olması özellik adları çoğul olur.

     Bir rolün çokluğu, bu rolün her bir örneğiyle karşıt rolün kaç taneyle ilişkilendirilip ilişkilendirilene bir şey olduğunu ifade eder. Örneğin, ComponentHasPorts ilişkisinde hedef rol, özniteliği Bağlantı Noktası, öznitelik Bileşen olarak, öznitelik ise ZeroOne olarak `RolePlayer` `PropertyName` `Multiplicity` ayarlanmıştır. Bu nedenle, bu rolü kullanmak için uygun kod:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Rolün `Name` adı, İlişki sınıfında bir bağlantının bu sonuna başvurmak için kullanılan addır. Kural gereği, her bağlantının her ucunda yalnızca bir örnek olduğundan rol adı her zaman tekildir. Aşağıdaki kod işe çalışacaktır:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Varsayılan olarak, `IsPropertyGenerator` özniteliği true olarak ayarlanır. False olarak ayarlanırsa Rol Oynatıcısı sınıfında hiçbir özellik oluşturulmaz. (Bu `op.Targets` durumda, , örneğin, çalışmaz). Ancak, özel kod ilişkiyi açıkça kullanıyorsa, özel kod kullanarak ilişkiyi çapraz geçiş yapmak veya bağlantılara erişim elde etmek yine de mümkündür:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>İlişki öznitelikleri

Tüm sınıflar için kullanılabilen özniteliklere ve alt düğümlere ek olarak, her ilişkinin şu öznitelikleri vardır:

- **IsEmbedding**. Bu Boole özniteliği, ilişkinin ekleme ağacının parçası olup olmadığını belirtir. Her modelin ekleme ilişkileri olan bir ağaç oluşturması gerekir. Bu nedenle her etki alanı sınıfı, bir modelin kökü olmadığı sürece en az bir ekleme ilişkisinin hedefi olmalıdır.

- **AllowsDuplicates**. Varsayılan olarak false olan bu Boole özniteliği yalnızca hem kaynak hem de hedefte "çok" çokluğu olan ilişkiler için geçerlidir. Dil kullanıcılarının tek bir kaynak ve hedef öğe çiftini aynı ilişkinin birden fazla bağlantısıyla bağp kurayamaylarını belirler.

## <a name="designer-and-toolbox-tabs"></a>Tasarımcı ve Araç Kutusu Sekmeleri

DslDefinition.dsl dosyasının Tasarımcı bölümünün ana bölümü **ToolboxTab öğeleridir.**  Bir tasarımcının bu öğelerden her biri, oluşturulan tasarımcının Araç Kutusunda bir bölüme doğru giden bölümü **temsil eden birkaç öğeye sahip olabilir.** Her **ToolboxTab** öğesi bir veya daha fazla **ElementTool öğesi,** **ConnectionTool öğesi veya** her ikisini birden içerebilir.

Öğe araçları belirli bir etki alanı sınıfının örneklerini oluşturabilir. Kullanıcı bir öğe aracını diyagrama sürükler, sonuç bu konunun ilerleyen kısımlarında öğe birleştirme yönergeleri hakkında bölümünde açıklandığı gibi öğe birleştirme yönergeleri tarafından belirlenir.

Her bağlantı aracı belirli bir bağlantı oluşturucusu çağırabilirsiniz. Bağlantı oluşturucuları hakkında bölümünde açıklandığı gibi, bir bağlantı oluşturucusu, kullanıcının fareyle nereye tıkladığında bağlı olarak birden fazla ilişki türü oluşturabilir.

Hiçbir araç türü doğrudan şekil veya bağlayıcı oluşturmaz. Her biri bir etki alanı sınıfı veya etki alanı ilişkisi örneği sağlar; Ardından Şekil ve Bağlayıcı eşlemeleri, bu etki alanı sınıfı veya etki alanı ilişkisinin nasıl görüntülendiğinden karar alır.

## <a name="paths"></a>Yollar

Etki alanı yolları DslDefinition.dsl dosyasındaki çeşitli konumlarda görünür. Bu yollar, modeldeki bir öğeden (yani etki alanına özgü dilin bir örneğine) bir dizi bağlantı belirtir. Yol söz dizimi basit ancak ayrıntılıdır.

Yollar DslDefinition.dsl dosyasında etiketlerde `<DomainPath>...</DomainPath>` görünür. Yollar birden çok bağlantı arasında gezinese de, uygulamada çoğu örnek yalnızca bir bağlantıdan geçiş sağlar.

Yol, bir segment dizisini içerir. Her segment, bir nesneden bir bağlantıya veya bir nesneye bağlantıdan atlar. Bu nedenle atlamalar genellikle uzun bir yolda alternatiftir. İlk atlama bir nesneden bağlantıya, ikinci atlama bağlantının diğer ucundaki nesneye, üçüncü atlama bir sonraki bağlantıya ve bu şekilde devam eder. Bu sıranın ara sıra özel durumu, bir ilişkinin kendisi başka bir ilişkinin kaynağı veya hedefi olduğu durumdur.

Her segment bir ilişki adıyla başlar. Bir nesneden bağlantıya atlamada ilişki bir noktadan önce ve özellik adı: " `Relationship . Property` ". Bir bağlantıdan nesneye atlamada ilişki bir ünlem işareti ve rol adı önündedir: " `Relationship ! Role` ".

Bileşen Diyagramı örneği, InPort için ShapeMap'in ParentElementPath'inde bir yol içerir. Bu yol aşağıdaki gibi başlar:

```
    ComponentHasPorts.Component
```

Bu örnekte InPort, ComponentPort'un bir alt sınıfıdır ve ComponentHasPorts ile bir ilişkisi vardır. özelliği Bileşen olarak adlandırılan bir özelliktir.

Bu modele karşı C# yazarken, ilişkinin ilişkili olduğu sınıfların her biri üzerinde oluşturulan özelliğini kullanarak tek adımda bir bağlantının üzerinden atlayın:

```
     InPort port; ...  Component c = port.Component;
```

Ancak, her iki atlamayı da Yol Söz Dizimsinde açıkça yapmak gerekir. Bu gereksinim nedeniyle ara bağlantıya daha kolay erişebilirsiniz. Aşağıdaki kod, Bileşen bağlantısından atlayıp tamamlar:

```
    ComponentHasPorts.Component / ! Component
```

(İlişki adını, önceki segmentte olduğu gibi atlarsiniz.)

## <a name="element-merge-directives"></a>Öğe Birleştirme Yönergeleri

Dil kullanıcısı bir öğeyi Araç Kutusundan **diyagrama** sürüklerse, aracın sınıfının bir örneği oluşturulur. Ayrıca, bu örnek ve mevcut model öğeleri arasında bağlantılar yapılır. Dil kullanıcısı bunları Araç Kutusundan diyagramın boş bir parçasına  sürüklerken bileşenler veya açıklamalar gibi bazı öğeler oluşturulur. Dil kullanıcısı bunları diğer konak öğelerine sürüklerken diğer öğeler oluşturulur. Örneğin, dil kullanıcısı bunu bir bileşene sürüklerken bir OutPort veya InPort oluşturulur.

Bileşen gibi olası bir konak sınıfı, yalnızca konak sınıfının yeni öğe sınıfı için bir öğe birleştirme yönergesi varsa yeni bir öğeyi kabul eder. Örneğin, Name="Component" olan DomainClass düğümü şunları içerir:

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Dizin düğümü altında olan sınıf bilinen adı, kabul edilebilecek öğe sınıfına başvurur. Bu durumda ComponentPort, InPort ve OutPort'un soyut temel sınıfıdır. Bu nedenle, bu öğelerden herhangi biri kabul edilebilir.

Dilin kök sınıfı olan ComponentModel, bileşenler ve açıklamalar için öğe birleştirme yönergelerine sahiptir. Dil kullanıcısı, diyagramın boş bölümleri kök sınıfı temsil etmelerinden dolayı bu sınıflar için öğeleri doğrudan diyagrama sürükleyebilirsiniz. Ancak ComponentModel, ComponentPort için öğe birleştirme yönergesine sahip değildir. Bu nedenle, dil kullanıcısı InPorts veya OutPorts'ı doğrudan diyagrama sürükleyemez.

Öğe birleştirme yönergesi, yeni öğenin mevcut modelle tümleştirileye veya birleştirene kadar hangi bağlantının veya bağlantıların oluşturulacaklarını belirler. Bir ComponentPort için ComponentHasPorts örneği oluşturulur. DomainPath, yeni öğenin ekli olduğu üst sınıf Ports öğesinin hem ilişkisini hem de özelliğini tanımlar.

Bir öğe birleştirme yönergesi üzerinde birden fazla bağlantı oluşturma yolu dahil olmak üzere birden fazla bağlantı oluşturabilirsiniz. Yollardan birinin eklenmiş olması gerekir.

Bağlantı oluşturma yolunda birden fazla kesim kullanabilirsiniz. Bu durumda, son segment hangi bağlantının oluşturulacak olduğunu tanımlar. Önceki segmentler üst sınıftan yeni bağlantının oluşturulacak nesnesine doğru ilerler.

Örneğin, bu öğe birleştirme yönergesi bileşen sınıfına eklenmiştir:

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Dil kullanıcıları daha sonra bir açıklamayı bir bileşene sürükleyip yeni açıklamanın bileşene bir bağlantıyla otomatik olarak oluşturulduğundan.

İlk bağlantı oluşturma yolu yolundan yoluna gidildi ve `Component` `ComponentModel` ardından ekleme ilişkisinin bir örneğini `ComponentModelHasComments` oluşturur. İkinci bağlantı oluşturma yolu, konak Bileşeninden yeni Açıklamaya CommentsReferenceComponents başvuru ilişkisinin bir bağlantısını oluşturur. Tüm bağlantı oluşturma yolları konak sınıfıyla başlamalı ve yeni örneği oluşturulan sınıfa doğru giden bir bağlantıda bitsin.

## <a name="xmlclassdata"></a>Xmlclassdata

Her etki alanı sınıfı (ilişkiler ve diğer alt türler dahil) `XmlClassData` DslDefinition.dsl dosyasının bölümünde görünen bir düğümde sağlanan `XmlSerializationBehavior` ek bilgilere sahip olabilir. Bu bilgiler özellikle bir model bir dosyaya kaydediken sınıf örneklerinin serileştirilmiş formda nasıl depolandığıyla ilgilidir.

Etkileyen oluşturulan kodun büyük `XmlSerializationBehavior` birı `Dsl\GeneratedCode\Serializer.cs` içindedir.

Her `XmlClassData` düğüm şu alt düğümleri ve öznitelikleri içerir:

- Verilerin uygulandığı sınıfa başvurulan bilinen düğüm.

- Sınıfında tanımlanan her özellik için **XmlPropertyData.**

- Sınıfında kaynak olarak oluşturulan her ilişki için **XmlRelationshipData.** (İlişkilerin kendi XmlClassData düğümleri de vardır.)

- Oluşturulan kodda serileştirme yardımcı sınıfının adını belirleyen **TypeName** dize özniteliği.

- Bu sınıfın serileştirilmiş örneklerinin XML etiketini belirleyen **ElementName** dizesi. Kural gereği, ElementName genellikle sınıf adıyla aynıdır ancak ilk harf küçük harftir. Örneğin, örnek bir model dosyası aşağıdakiyle başlar:

    ```xml
    <componentModel ...
    ```

- Kullanıcının serileştirilmiş model dosyalarında **MonikerElementName.** Bu öznitelik, bu sınıfa başvurulan bir bilinen ad sağlar.

- Bilinen ad içindeki XML özniteliğinin adını tanımlayan **MonikerAttributeName.** Bir kullanıcının serileştirilmiş dosyasının bu parçasında, etki alanına özgü dilin yazarı **MonikerElementName'i** "inPortMoniker" ve **MonikerAttributeName'i** "path" olarak tanımladı:

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Her bağlantı aracı için bir bağlantı oluşturucu tanımlanır. Her bağlantı oluşturucusu, her biri bir veya daha fazla SourceDirective ve bir veya daha fazla TargetDirective öğe içeren bir veya daha fazla LinkConnectDirective öğeden oluşur. Kullanıcı bir bağlantı aracına tık kullandıktan sonra SourceDirective öğeleri listesinde görünen model öğesine eşlenmiş herhangi bir şekilden bağlantı başlatabilirsiniz. Bağlantı daha sonra TargetDirective öğeleri listesinde görünen bir öğeyle eşlenen bir şekil üzerinde tamamlanır. İlişki örneği başlatan sınıfı, bağlantının başlat olduğu yere göre belirlenen LinkConnectDirective öğesine bağlıdır.

### <a name="xmlpropertydata"></a>Xmlpropertydata

**DomainPropertyMoniker** özniteliği, verilerin başvurduğu özelliği tanımlar. Bu öznitelik, kapsayan ClassData sınıfının bir özelliği olması gerekir.

**XmlName özniteliği,** XML'de görünmesi gerektiği gibi ilgili öznitelik adını verir. Kural gereği, bu dize özellik adıyla aynıdır ancak ilk harf küçük harftir.

Varsayılan olarak, **Gösterim özniteliği** Öznitelik olarak ayarlanır. Gösterim **Öğesi** olarak ayarlanırsa XML'de bir alt düğüm oluşturulur. Gösterim **Yoksay** olarak ayarlanırsa özelliği seri hale getirili değildir.

**IsMonikerKey** ve **IsMonikerQualifier** öznitelikleri, üst sınıfın örneklerini tanımlamada bir özellik rolü sağlar. Bir sınıf tarafından tanımlanan veya devralınan bir özellik için **IsMonikerKey'i** true olarak ayarlayın. Bu öznitelik, üst sınıfın tek bir örneğini tanımlar. olarak ayar genellikle bir `IsMonikerKey` ad veya başka bir anahtar tanımlayıcısıdır. Örneğin, `Name` dize özelliği NamedElement ve türetilmiş sınıfları için bilinen anahtardır. Kullanıcı bir modeli dosyaya kaydederken, bu öznitelik ekleme ilişkileri ağacına her örnek için benzersiz değerler içermesi gerekir.

Serileştirilmiş model dosyasında, bir öğenin tam bilinen adı, ekleme ilişkileri ağacının sonundaki model kökünden bir yoldur ve her noktada bilinen anahtardan alıntılar. Örneğin, InPort'lar Bileşenler'in içine katıştırılmıştır ve bunlar da model köküne katıştırılmıştır. Bu nedenle geçerli bir bilinen ad:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Bir dize özelliği **için IsMonikerQualifier özniteliğini** ayarlayın ve bir öğenin tam adını oluşturmak için ek bir yol sebilirsiniz. Örneğin, DslDefinition.dsl dosyasında **Ad Alanı** bir bilinen ad niteleyicisi.

### <a name="xmlrelationshipdata"></a>Xmlrelationshipdata

Serileştirilmiş model dosyasında bağlantılar (hem ekleme hem de başvuru ilişkilerinin), ilişkinin kaynak sonunun alt düğümleriyle temsil edilen. Ekleme ilişkileri için alt düğüm bir alt ağaç içerir. Başvuru ilişkileri için alt düğüm, ağacın başka bir parçasına başvurulan bir bilinen ad içerir.

**XmlClassData özniteliğinde XmlRelationshipData** özniteliği, alt düğümlerin kaynak öğe içinde tam olarak nasıl iç içe geçmiş olduğunu tanımlar.  Etki Alanı Sınıfındaki bir kaynak olan her ilişkinin bir **XmlRelationshipData özniteliği** vardır.

**DomainRelationshipMoniker** özniteliği, sınıfındaki ilişkilerden birini tanımlar.

**RoleElementName özniteliği,** serileştirilmiş verilerde alt düğümü kapsayan XML etiket adını verir.

Örneğin, DslDefinition.dsl dosyası şunları içerir:

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Bu nedenle, serileştirilmiş dosya şunları içerir:

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

**UseFullForm** özniteliği true olarak ayarlanırsa, fazladan bir iç içe yerleştirme katmanı ek olarak tanıtıldı. Bu katman, ilişkinin kendisini temsil eder. İlişkinin özellikleri varsa özniteliği true olarak ayar gerekir.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Serileştirilmiş dosya şunları içerir:

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

(Bağlantı İlişkisi, öğesi ve öznitelik adlarını sağlayan kendi XML sınıfı verilerine sahip.)

**OmitElement** özniteliği true olarak ayarlanırsa, ilişki rolü adı atlanır. Bu ad serileştirilmiş dosyayı kısaltır ve iki sınıfta birden fazla ilişki yoksa belirsiz olur. Örnek:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Domain-Specific Dil Tanımının Seri hale Getirme

DslDefinition.dsl dosyasının kendisi serileştirilmiş bir dosyadır ve etki alanına özgü dil tanımına uyum sağlar. Xml serileştirme tanımlarının bazı örnekleri aşağıda verilmiştir:

- **Dsl,** RootClass düğümü ve diyagramın sınıfıdır. DomainClass, DomainRelationship ve diğer öğeler altında `Dsl` katıştırılmıştır.

- **Sınıflar,** Domain-Specific Language ile DomainClass arasındaki **ilişkinin RoleElementName'idir.**

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- **XmlSerializationBehavior** özniteliği özniteliğinin altına katıştırıldı, ancak ekleme ilişkisi üzerinde `Dsl` **OmitElement** özniteliği ayarlanmıştır. Bu nedenle, hiçbir `RoleElementName` öznitelik müdahale etmez. Buna karşılık **ClassData** özniteliği, `RoleElementName` **xmlSerializationBehavior** özniteliği ile **XmlClassData** özniteliği arasındaki ekleme ilişkisinin özniteliğidir.

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators, ile arasındaki ekleme `Connector` `Decorator` ilişkisidir. `UseFullForm` , ilişki adının bağlayıcı nesnesinden her bir bağlantı için özellikler listesiyle birlikte görünmesi için ayarlanmıştır. Ancak, `OmitElement` `RoleElementName` içine eklenen birden çok bağlantıyı hiçbir şekilde içermemesi için de ayarlanmıştır `Connector` :

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Şekiller ve bağlayıcılar

Şekil ve bağlayıcı tanımları, aşağıdaki özelliklere ek olarak, etki alanı sınıflarından öznitelikleri ve alt düğümleri miras alır:

- `Color` ve `Line``Style` öznitelikleri.

- **ExposesFillColorAsProperty** ve benzeri birkaç öznitelik. Bu Boole öznitelikleri, ilgili özellik değişkenini Kullanıcı tarafından yapar. Genellikle, bir dil kullanıcısı diyagramda bir şekle tıkladığında, **Özellikler** penceresinde görünen özellikler, şeklin eşlendiği etki alanı sınıfı örneğinden oluşur. `ExposesFillColorAsProperty`True olarak ayarlanırsa, şeklin bir özelliği de görüntülenir.

- **Shapehasdekoratörler**. Bu özniteliğin bir örneği her metin, simge veya genişletme/daraltma dekoratör için oluşur. (DslDefinition. dsl dosyasında, `ShapeHasDecorators` `UseFullForm` true olarak ayarlanmış bir ilişkidir.)

## <a name="shape-maps"></a>şekil Haritalar

Şekil haritaları, belirli bir etki alanı sınıfının örneklerinin, bir şekil tarafından temsil edildiği şekilde ekranda nasıl göründüğünü belirlenir. Hem şekil hem de bağlayıcı haritaları `Diagram` DslDefinition. dsl dosyasının bölümünün altında görünür.

Aşağıdaki örnekte olduğu gibi, `ShapeMap` öğeleri en azından, bir etki alanı sınıfının bilinen adı, bir şeklin bilinen adı ve bir `ParentElementPath` öğesi vardır:

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

Öğesinin birincil işlevi, `ParentElementPath` aynı nesne sınıfının farklı bağlamlarda farklı bir şekil olarak görünebilmesini sağlayacak. Örneğin, bir `InPort` yoruma de gömülebilir, `InPort` Bu amaçla farklı bir şekil olarak görünebilir.

İkinci olarak, yol şeklin üst öğesiyle ilişkisini belirler. DslDefinition. dsl dosyasındaki şekiller arasında ekleme yapısı tanımlanmamıştır. Yapıyı şekil haritalarından çıkarmalısınız. Bir şeklin üst öğesi, üst öğe yolunun tanımladığı etki alanı öğesiyle eşlenen şekildir. Bu durumda yol, `InPort` ait olduğu bileşeni tanımlar. Başka bir şekil eşlemesinde, bileşen sınıfı ComponentShape ile eşleştirilir. Bu nedenle, yeni `InPort` şekil, bileşenin bir alt şekli haline getirilir `ComponentShape` .

Bunun yerine, InPort şeklini diyagrama eklediyseniz, üst öğe yolunun, diyagram ile eşlenmiş bileşen modeline başka bir adım olması gerekir:

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

Modelin kökünde bir şekil Haritası yok. Bunun yerine, köke bir öğesi olan doğrudan diyagramdan başvurulur `Class` :

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>dekoratör Haritalar

Dekoratör eşlemesi eşlenen sınıftaki bir özelliği şekildeki dekoratör ile ilişkilendirir. Özellik numaralandırılmış veya Boolean bir tür ise, değeri dekoratörün görünür olup olmadığını belirleyebilir. Dekoratör bir metin dekoratör ise, özelliğin değeri görünebilir ve Kullanıcı onu düzenleyebilir.

### <a name="compartment-shape-maps"></a>bölme şekli Haritalar

Bölme şekli eşlemeleri şekil haritalarının alt türleri.

## <a name="connector-maps"></a>bağlayıcı Haritalar

En az bağlayıcı eşlemesi bir bağlayıcıya ve bir ilişkiye başvurur:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Bağlayıcı haritaları, dekoratör haritaları da içerebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)