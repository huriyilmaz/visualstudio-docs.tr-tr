---
title: DslDefinition.dsl Dosyası
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97736dd9893f3a5d0c07f464ae75849395270d4b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114925"
---
# <a name="the-dsldefinitiondsl-file"></a>DslDefinition.dsl Dosyası

Bu konu, [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] *etki alanına özgü bir dili*tanımlayan bir çözümün DSL projesindeki DslDefinition. dsl dosyasının yapısını açıklar. DslDefinition. dsl dosyası, etki alanına özgü dilin sınıflarını ve ilişkilerini, etki alanına özgü dilin ve onun düzen araçlarının **araç kutusunu** ile birlikte açıklar. Etki alanına özgü bir dil çözümünde, bu araçları tanımlayan kod DslDefinition. dsl dosyasındaki bilgilere göre oluşturulur.

Genellikle, DslDefinition. dsl dosyasını düzenlemek için *alana özgü dil Tasarımcısı* kullanırsınız. Ancak ham biçimi XML 'dir ve bir DslDefinition. dsl dosyasını bir XML düzenleyicisinde açabilirsiniz. Dosyanın hangi bilgileri içerdiğini ve hata ayıklama ve genişletme amaçları için nasıl düzenlendiğini anlamak yararlı olabilir.

Bu konudaki örnekler bileşen diyagramı çözüm şablonundan alınmıştır. Örnek görmek için, bileşen modelleri çözüm şablonunu temel alan, etki alanına özgü bir dil çözümü oluşturun. Çözümü oluşturduktan sonra DslDefinition. dsl dosyası Alana Özgü Dil Tasarımcısı görüntülenir. Dosyayı kapatın, **Çözüm Gezgini**' de sağ tıklayın, **birlikte Aç**' ın üzerine gelin, **XML Düzenleyicisi**' ne tıklayın ve ardından **Tamam**' a tıklayın.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>DslDefinition. dsl dosyasının bölümleri

Kök öğesi \<Dsl> ve öznitelikleri, etki alanına özgü dilin adını, ad alanını ve sürüm oluşturma için büyük ve küçük sürüm numaralarını belirler. `DslDefinitionModel`Şema geçerli bir DslDefinition. dsl dosyası için içerik ve yapıyı tanımlar.

\<Dsl>Kök öğesinin alt öğeleri aşağıdaki gibidir:

### <a name="classes"></a>Sınıflar

Bu bölüm, oluşturulan kodda bir sınıf üreten her bir etki alanı sınıfını tanımlar.

### <a name="relationships"></a>İlişkiler

Bu bölüm modeldeki her ilişkiyi tanımlar. Kaynak ve hedef, bir ilişkinin iki tarafını temsil eder.

### <a name="types"></a>Türler

Bu bölüm her türü ve ad alanını tanımlar. Etki alanı özelliklerinde iki tür vardır. `DomainEnumerations` modelde tanımlanır ve DomainModel.cs içine türler oluşturur. `ExternalTypes` başka bir yerde (veya gibi) tanımlanmış türlere `String` `Int32` ve hiçbir şey oluşturmamasına bakın.

### <a name="shapes"></a>Şekiller

Bu bölüm, modelin bir tasarımcıda nasıl göründüğünü betimleyen şekilleri tanımlar. Bu geometrik şekiller, diyagram bölümünde modeldeki sınıflarla eşleştirilir.

### <a name="connectors"></a>Bağlayıcılar

Bu bölümde, bir tasarımcıda görüntülenen bağlayıcıların görünümü tanımlanmaktadır. Bu geometrik stil açıklamaları, diyagram bölümünde modeldeki belirli ilişkilerle eşleştirilir.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Bu bölüm bir serileştirme şeması tanımlar ve her sınıfın bir dosyaya nasıl kaydedildiği hakkında ek bilgiler sağlar.

### <a name="explorerbehavior"></a>ExplorerBehavior

Bu bölüm, Kullanıcı bir modeli düzenlediğinizde **DSL Gezgini** penceresinin nasıl göründüğünü tanımlar.

### <a name="connectionbuilders"></a>ConnectionBuilder 'lar

Bu bölüm, her bağlayıcı aracı için bir bağlantı Oluşturucu (bağlı olabilecek iki sınıf arasında bağlantı oluşturmak için araç) tanımlar. Bu bölüm, bir kaynak ve hedef sınıfa bağlanıp bağlanamadığını belirler.

### <a name="diagram"></a>Diyagram

Bu bölüm bir diyagramı tanımlar ve arka plan rengi ve kök sınıf gibi özellikleri belirtmek için kullanılır. (Kök sınıfı, diyagram tarafından bir bütün olarak temsil edilen etki alanı sınıfıdır.) Diyagram bölümü, her bir etki alanı sınıfını veya ilişkiyi temsil eden şekli veya bağlayıcıyı belirten ShapeMap ve ConnectorMap öğelerini de içerir.

### <a name="designer"></a>Tasarımcı

Bu bölüm bir **araç kutusunu**, doğrulama ayarlarını, bir diyagramı ve bir serileştirme şemasını birlikte getiren bir tasarımcı (düzenleyici) tanımlar. Tasarımcı bölümü, genellikle diyagramın kök sınıfı olan modelin kök sınıfını da tanımlar.

### <a name="explorer"></a>Gezgin

Bu bölümde **DSL Gezgini** davranışı (XmlSerializationBehavior bölümünde tanımlanmıştır) tanımlanmaktadır.

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>DslDefinition. dsl dosyasındaki takma adlar

DslDefinition. dsl dosyası boyunca, belirli öğelere çapraz başvurular yapmak için takma adlar kullanabilirsiniz. Örneğin, her Ilişki tanımı bir kaynak alt bölümü ve bir hedef alt bölümü içerir. Her alt bölüm, bu ilişkiyle bağlanabilen nesne sınıfının bilinen adını içerir:

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

Genellikle, başvurulan öğenin ad alanı (Bu örnekte, `Library` etki alanı sınıfı) başvuru öğesiyle aynı (Bu durumda, LibraryHasMembers etki alanı ilişkisi) ile aynıdır. Bu durumlarda, bilinen ad yalnızca sınıfın adını vermelidir. Aksi takdirde,/Namespace/Name tam biçimini kullanmanız gerekir:

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Bilinen ad sistemi, XML ağacındaki eşdüzey öğelerinin ayrı adlara sahip olmasını gerektirir. Bu nedenle, örneğin, aynı ada sahip iki sınıf olan bir etki alanına özgü dil tanımını kaydetmeye çalışırsanız doğrulama hataları oluşur. DslDefinition. dsl dosyasını kaydetmeden önce bu tür yinelenen adı her zaman düzeltmeniz gerekir, böylece daha sonra yeniden yükleyebilirsiniz.

Her türün kendi bilinen adı vardır: DomainClassMoniker, Domainrelationshiptakma adı ve benzeri.

## <a name="types"></a>Türler

Türler bölümü DslDefinition. dsl dosyasının Özellik türleri olarak içerdiği tüm türleri belirtir. Bu türler iki tür için ayrılır: System. String ve numaralandırılmış türler gibi dış türler.

### <a name="external-types"></a>Dış türler

Bileşen diyagramı örneği, bir dizi standart temel türü listeler, ancak yalnızca bazıları kullanılabilir.

Her harici tür tanımı, dize ve sistem gibi yalnızca bir ad ve ad alanından oluşur:

```xml
<ExternalType Name="String" Namespace="System" />
```

Türlerin tam adları, "String" gibi eşdeğer derleyici anahtar sözcükleri yerine kullanılır.

Dış türler standart kitaplık türleriyle sınırlı değildir.

### <a name="enumerations"></a>Listelemeler

Tipik bir numaralandırma belirtimi bu örneğe benzer:

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

`IsFlags`Özniteliği, oluşturulan koda `[Flags]` ortak dil çalışma zamanı (CLR) özniteliği tarafından ön ekli olup olmadığını denetler; bu, numaralandırmanın değerlerinin bit düzeyinde birleştirilip birleştirimeyeceğini belirler. Bu öznitelik true olarak ayarlanırsa, değişmez değerler için iki bitlik değeri belirtmeniz gerekir.

## <a name="classes"></a>Sınıflar

Etki alanına özgü dilin herhangi bir tanımındaki öğelerin çoğu doğrudan veya dolaylı olarak örnekleridir `DomainClass` . ,, `DomainClass` Ve dahil alt sınıfları `DomainRelationship` `Shape` `Connector` `Diagram` . `Classes`DslDefinition. dsl dosyasının bölümünde, etki alanı sınıfları listelenir.

Her sınıfın bir özellikler kümesi vardır ve bir temel sınıfa sahip olabilir. Bileşen diyagramı örneğinde, `NamedElement` türü String olan bir özelliğine sahip soyut bir sınıftır `Name` :

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

`NamedElement``Component`, ' `Name` den Devralındığı özelliğe ek olarak kendi özelliklerine sahip olan gibi diğer sınıfların birtabanının temelini içerir `NamedElement` . BaseClass alt düğümü bir ad başvurusu içeriyor. Başvurulan sınıf aynı ad alanında olduğundan, bilinen ad için yalnızca adı gereklidir:

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

Her etki alanı sınıfı (ilişkiler, şekiller, bağlayıcılar ve diyagramlar dahil) bu özniteliklere ve alt düğümlere sahip olabilir:

- **Kimliği.** Bu öznitelik bir GUID 'dir. Dosyada bir değer sağlamazsanız Alana Özgü Dil Tasarımcısı bir değer oluşturacaktır. (Bu belgedeki çizimlerde, bu öznitelik genellikle alan kazanmak için atlanır.)

- **Ad ve ad alanı.** Bu öznitelikler, oluşturulan koddaki sınıfın adını ve ad alanını belirtir. Bunların birlikte, etki alanına özgü dil içinde benzersiz olması gerekir.

- **InheritanceModifier.** Bu öznitelik "abstract", "Sealed" veya None 'tur.

- **DisplayName.** Bu öznitelik, **Özellikler** penceresinde görünen addır. DisplayName özniteliği boşluk ve diğer noktalama işaretlerini içerebilir.

- **GeneratesDoubleDerived.** Bu öznitelik true olarak ayarlanırsa, iki sınıf oluşturulur ve diğeri diğerinin bir alt sınıfıdır. Oluşturulan tüm yöntemler temelde bulunur ve oluşturucular alt sınıfta bulunur. Bu özniteliği ayarlayarak, özel kodda oluşturulan herhangi bir yöntemi geçersiz kılabilirsiniz.

- **Hasccustomconstructor**. Bu öznitelik true olarak ayarlanırsa, kendi sürümünüzü yazabileceğiniz şekilde Oluşturucu oluşturulan koddan çıkarılır.

- **Öznitelikler**. Bu öznitelik, oluşturulan sınıfın CLR özniteliklerini içerir.

- **BaseClass**. Bir temel sınıf belirtirseniz, aynı türde olmalıdır. Örneğin, bir etki alanı sınıfı temel olarak başka bir etki alanı sınıfına sahip olmalıdır ve bölme şeklinin bir bölme şekli olmalıdır. Bir temel sınıf belirtmezseniz, oluşturulan koddaki sınıfı standart bir çerçeve sınıfından türetilir. Örneğin, bir etki alanı sınıfı öğesinden türetilir `ModelElement` .

- **Özellikler**. Bu öznitelik, işlem denetimi altında tutulan ve model kaydedildiğinde kalıcı olan özellikleri içerir.

- **Elementmergedirektifi**. Her öğe birleştirme yönergesi, bir başka sınıfın farklı bir örneğinin üst sınıf örneğine nasıl ekleneceğini denetler. Bu konunun ilerleyen kısımlarında, öğe birleştirme yönergeleri hakkında daha fazla ayrıntı bulabilirsiniz.

- Bölümünde listelenen her bir etki alanı sınıfı için bir C# sınıfı oluşturulur `Classes` . C# sınıfları Dsl\GeneratedCode\DomainClasses.cs. içinde oluşturulur

### <a name="properties"></a>Özellikler

Her etki alanı özelliğinin bir adı ve türü vardır. Ad, etki alanı sınıfı ve geçişli tabanların içinde benzersiz olmalıdır.

Türün, bölümünde listelenenlerden birine başvurması gerekir `Types` . Genellikle bilinen ad ad alanını içermelidir.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Her etki alanı özelliği de şu özniteliklere sahip olabilir:

- **Igözatılabilir**. Bu öznitelik, Kullanıcı üst sınıfın bir nesnesine tıkladığında özelliğin **Özellikler** penceresinde görünüp görünmeyeceğini belirler.

- **IsUIReadOnly**. Bu öznitelik, kullanıcının **Özellikler** penceresinde veya özelliğin sunulduğu bir dekoratör aracılığıyla özelliği değiştirip değiştiremeyeceğini belirler.

- **Tür**. Bu özniteliği normal, hesaplanan veya CustomStorage olarak ayarlayabilirsiniz. Bu özniteliği hesaplanmak üzere ayarlarsanız, değeri belirleyen özel kod sağlamanız gerekir ve özellik salt okunurdur. Bu özniteliği CustomStorage olarak ayarlarsanız, değerleri alıp ayarlayan kodu sağlamanız gerekir.

- **IsElementName**. Bu öznitelik true olarak ayarlanırsa, üst sınıfın bir örneği oluşturulduğunda değeri otomatik olarak benzersiz bir değere ayarlanır. Bu öznitelik, bir dize türü olması gereken her sınıfta yalnızca bir özellik için true olarak ayarlanabilir. Bileşen diyagramı örneğinde, `Name` içindeki özelliği `NamedElement` `IsElementName` true olarak ayarlanmıştır. Bir Kullanıcı bir öğe oluşturduğunda `Component` (öğesinden devralırsa `NamedElement` ), ad "Component6" gibi bir şekilde otomatik olarak başlatılır.

- `DefaultValue`. Bu özniteliği belirttiyseniz, belirttiğiniz değer bu sınıfın yeni örnekleri için bu özniteliğe atanır. `IsElementName`Ayarlanırsa, DefaultValue özniteliği yeni dizenin ilk kısmını belirtir.

- **Kategori** , özelliğin **Özellikler** penceresinde görüneceği üst bilgi olur.

## <a name="relationships"></a>İlişkiler

Bu `Relationships` bölümde, etki alanına özgü dildeki tüm ilişkiler listelenir. Her `Domain Relationship` biri ikili ve yönlendirilir, kaynak sınıfın üyeleri bir hedef sınıfın üyelerine bağlanıyor. Kaynak ve hedef sınıflar genellikle etki alanı sınıflarıdır, ancak diğer ilişkilerle olan ilişkilere da izin verilir.

Örneğin, bağlantı ilişkisi OutPort sınıfının üyelerini InPort sınıfının üyelerine bağlar. İlişkinin her bağlantı örneği bir OutPort örneğini bir InPort örneğine bağlar. İlişki çok fazla olduğundan, her bir çıkış noktası üzerinde kaynakları olan çok sayıda bağlantı bağlantısı olabilir ve her bir InPort örneği, onu hedefleyen çok sayıda bağlantı bağlantısına sahip olabilir.

### <a name="source-and-target-roles"></a>Kaynak ve hedef roller

Her ilişki aşağıdaki özniteliklere sahip kaynak ve hedef rolleri içerir:

- `RolePlayer`Öznitelik, bağlantılı örneklerin etki alanı sınıfına başvurur: kaynak için çıkış noktası, hedef Için InPort.

- `Multiplicity`Özniteliğin olası dört değeri (sıfır, sıfır sıfırlama, bir, ve OneMany) vardır. Bu öznitelik, bu ilişkinin bir rol oyuncusu ile ilişkilendirilebilen bağlantı sayısını ifade eder.

- `PropertyName`Özniteliği, rol oynatma sınıfında diğer uçtaki nesnelere erişmek için kullanılan adı belirtir. Bu ad, ilişkide geçiş yapmak için şablonda veya özel kodda kullanılır. Örneğin, `PropertyName` kaynak rolün özniteliği olarak ayarlanır `Targets` . Bu nedenle, aşağıdaki kod işe alınacaktır:

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Kurala göre, çoğulluk sıfır veya OneMany ise özellik adları plural 'dir.

     Bir rolün çoğulluğu, bu rolün her örneğiyle karşı bir rolün kaç tane ile ilişkilendirilebilen ile ilgilidir. Örneğin, ComponentHasPorts ilişkisinde, hedef rolün `RolePlayer` özniteliği bağlantı noktası, `PropertyName` özniteliği bileşen olarak ayarlanan öznitelik ve `Multiplicity` sıfırlama bir tane olarak ayarlanan özniteliği vardır. Bu nedenle, bu rolü kullanmak için uygun kod şunlardır:

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Rol, `Name` bir bağlantının sonuna başvurmak Için ilişki sınıfı içinde kullanılan addır. Kural gereği, her bağlantının her uçta yalnızca bir örneği olduğundan, rol adı her zaman tekil olur. Aşağıdaki kod çalışır:

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Varsayılan olarak, `IsPropertyGenerator` özniteliği true olarak ayarlanır. False olarak ayarlanırsa, rol oynatıcı sınıfında hiçbir özellik oluşturulmaz. (Bu durumda, `op.Targets` Örneğin, çalışmaz). Bununla birlikte, ilişkiye çapraz geçiş yapmak için özel kod kullanmak veya özel kod ilişkiyi açıkça kullandığında bağlantılara erişim elde etmek yine de mümkündür:

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>İlişki öznitelikleri

Tüm sınıfların kullanabildiği özniteliklerin ve alt düğümlerin yanı sıra, her ilişki şu özniteliklere sahiptir:

- **Ibımbedding**. Bu Boole özniteliği, ilişkinin ekleme ağacının bir parçası olup olmadığını belirtir. Her modelin, katıştırma ilişkilerine sahip bir ağaç oluşturmalıdır. Bu nedenle, bir modelin kökü olmadığı müddetçe, her etki alanı sınıfının en az bir katıştırma ilişkisinin hedefi olması gerekir.

- **Allowsyinelemelerini**. Varsayılan olarak false olan bu Boolean özniteliği yalnızca kaynak ve hedefte "çok" çokluğu olan ilişkiler için geçerlidir. Dil kullanıcılarının tek bir kaynak ve hedef öğe çiftinden aynı ilişkinin birden fazla bağlantısı tarafından bağlanıp bağlanamadığını belirler.

## <a name="designer-and-toolbox-tabs"></a>Tasarımcı ve araç kutusu sekmeleri

DslDefinition. dsl dosyasının **Tasarımcı** bölümünün ana bölümü **ToolboxTab** öğeleridir. Bir tasarımcıda, her biri oluşturulan tasarımcı **araç kutusundaki**bir uçlu bölümü temsil eden bu öğelerden birkaçı olabilir. Her **ToolboxTab** öğesi bir veya daha fazla **ElementTool** öğesi, **ConnectionTool** öğesi veya her ikisini içerebilir.

Öğe araçları, belirli bir etki alanı sınıfının örneklerini oluşturabilir. Kullanıcı diyagram üzerine bir öğe aracı sürüklediğinde, sonuç, bu konunun ilerleyen kısımlarında bulunan öğe birleştirme yönergeleri hakkında bölümünde açıklandığı gibi öğe birleştirme yönergeleri tarafından belirlenir.

Her bağlantı aracı, belirli bir bağlantı oluşturucuyu çağırabilir. Bir bağlantı Oluşturucu, bağlantı oluşturucular hakkında bölümünde açıklandığı gibi kullanıcının fareyle tıkladığı yere bağlı olarak birden çok ilişki türü oluşturabilir.

Ne tür bir araç doğrudan şekil veya bağlayıcı oluşturur. Her biri bir etki alanı sınıfını veya bir etki alanı ilişkisini başlatır; Şekil ve bağlayıcı eşlemeleri daha sonra bu etki alanı sınıfının veya etki alanı ilişkisinin nasıl göründüğünü belirlenir.

## <a name="paths"></a>Yollar

Etki alanı yolları DslDefinition. dsl dosyasındaki çeşitli konumlarda görünür. Bu yollar, bir modeldeki bir öğeden (yani, etki alanına özgü dilin bir örneğine) bir bağlantı dizisi belirtir. Yol sözdizimi basit ancak ayrıntılıdır.

Yollar, DslDefinition. dsl dosyasında Etiketler ' de görünür `<DomainPath>...</DomainPath>` . Yollar birden çok bağlantı aracılığıyla gezinebilse de, çoğu örnek yalnızca tek bir bağlantıda geçiş yapar.

Bir yol, bir dizi kesimden oluşur. Her segment, bir nesneden bağlantı ya da bir nesne bağlantısından bir atlama olur. Bu nedenle, atlama genellikle uzun bir yolda alternatif olarak yapılır. İlk atlama bir nesneden bir bağlantıya, ikinci atlama ise bağlantının diğer sonundaki nesneye, üçüncü atlama ise sonraki bağlantıya ve bu şekilde devam eder. Bu sıranın olağan dışı özel durumu, ilişkinin kendisinin kaynağı veya başka bir ilişkinin hedefi olduğu yerdir.

Her segment bir ilişki adıyla başlar. Bir nesneden bağlantıya atlamada, ilişki bir noktayla ve özellik adından önce gelir: " `Relationship . Property` ". Bir bağlantı nesnesi atlaması içinde, ilişki bir ünlem işaretiyle ve rol adından önce gelir: " `Relationship ! Role` ".

Bileşen diyagramı örneği, InPort için ShapeMap 'in ParentElementPath öğesinde bir yol içerir. Bu yol aşağıdaki gibi başlatılır:

```
    ComponentHasPorts.Component
```

Bu örnekte, InPort, ComponentPort 'un bir alt sınıfıdır ve bir ilişki ComponentHasPorts içerir. Özelliği bileşen olarak adlandırılır.

C# ' ı bu modele göre yazarken, ilişkinin her bir sınıf üzerinde oluşturduğu özelliği kullanarak tek bir adımda bir bağlantı üzerinden atlayabilirsiniz:

```
     InPort port; ...  Component c = port.Component;
```

Ancak, her iki durağı de yol sözdiziminde açıkça yapmanız gerekir. Bu gereksinim nedeniyle, ara bağlantıyı daha kolay bir şekilde erişebilirsiniz. Aşağıdaki kod, bileşene olan bağlantıdan atlama işlemini tamamlar:

```
    ComponentHasPorts.Component / ! Component
```

(Önceki kesimdeki ile aynı olan ilişki adını atlayabilirsiniz.)

## <a name="element-merge-directives"></a>Öğe birleştirme yönergeleri

Dil kullanıcısı **araç kutusundan** bir öğeyi diyagram üzerine sürüklediğinde, aracın sınıfının bir örneği oluşturulur. Ayrıca, bu örnek ve var olan model öğeleri arasında bağlantılar yapılır. **Araç kutusu** Kullanıcı tarafından diyagramın boş bir kısmına sürüklendiğinde, bileşenler veya açıklamalar gibi bazı öğeler oluşturulur. Diğer öğeler, dil kullanıcısı tarafından diğer ana bilgisayar öğelerine sürüklendiğinde oluşturulur. Örneğin, dil kullanıcısı onu bir bileşene sürüklediğinde bir OutPort veya InPort oluşturulur.

Bileşen gibi potansiyel bir konak sınıfı, yalnızca konak sınıfının yeni öğenin sınıfı için bir öğe birleştirme yönergesine sahipse yeni bir öğeyi kabul eder. Örneğin, "Component" adlı DomainClass düğümü şunları içerir:

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

Dizin düğümü altındaki sınıf bilinen adı, kabul edilebilir öğe sınıfına başvurur. Bu durumda, ComponentPort, InPort ve OutPort soyut temel sınıfıdır. Bu nedenle, bu öğelerden biri kabul edilebilir.

Dilin kök sınıfı olan ComponentModel, bileşenler ve açıklamalar için öğe birleştirme yönergeleri içerir. , Diyagramın boş kısımları kök sınıfı temsil ettiğinden, dil kullanıcısı bu sınıfların öğelerini doğrudan diyagrama sürükleyebilir. Ancak ComponentModel, ComponentPort için bir öğe birleştirme yönergesine sahip değildir. Bu nedenle, dil kullanıcısı InPort 'ları veya çıkışları doğrudan diyagram üzerine sürüklemez.

Öğe birleştirme yönergesi, yeni öğenin var olan modele tümleştirileceği veya birleştirebilmesi için hangi bağlantının veya bağlantıların oluşturulduğunu belirler. Bir ComponentPort için ComponentHasPorts 'nin bir örneği oluşturulur. DomainPath, hem ilişkiyi hem de üst sınıf, bağlantı noktaları ve yeni öğenin ekleneceği özelliği tanımlar.

Birden fazla bağlantı oluşturma yolu ekleyerek bir öğe birleştirme yönergesinde birden fazla bağlantı oluşturabilirsiniz. Yollardan biri katıştırılmalıdır.

Bir bağlantı oluşturma yolunda birden fazla segment kullanabilirsiniz. Bu durumda, son segment hangi bağlantının oluşturulması gerektiğini tanımlar. Önceki parçalar, üst sınıftan yeni bağlantının oluşturulması gereken nesneye gider.

Örneğin, bu öğe birleştirme yönergesini bileşen sınıfına ekleyebilirsiniz:

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

Dil kullanıcıları daha sonra bir bileşene bir açıklama sürükleyebilir ve yeni açıklamanın bileşen bağlantısıyla otomatik olarak oluşturulmasını sağlayabilir.

İlk bağlantı oluşturma yolu öğesinden `Component` öğesine gider `ComponentModel` ve sonra ekleme ilişkisinin bir örneğini oluşturur `ComponentModelHasComments` . İkinci bağlantı oluşturma yolu, ana bilgisayar bileşeninden yeni yoruma yorum olarak Yorumtsreferencecomponents bağlantı ilişkisi oluşturur. Tüm bağlantı oluşturma yolları ana bilgisayar sınıfıyla başlamalıdır ve yeni örneklenmiş sınıfa doğru bir bağlantı ile bitmelidir.

## <a name="xmlclassdata"></a>XmlClassData

Her etki alanı sınıfı (ilişkiler ve diğer alt türler dahil), `XmlClassData` `XmlSerializationBehavior` DslDefinition. dsl dosyasının bölümü altında görüntülenen bir düğümde sağlanmış ek bilgilere sahip olabilir. Bu bilgiler, bir model bir dosyaya kaydedildiğinde sınıf örneklerinin serileştirilmiş biçimde nasıl depolandığını özellikle ele alınır.

' İ etkileyen üretilen kodun çoğu `XmlSerializationBehavior` içinde `Dsl\GeneratedCode\Serializer.cs` .

Her `XmlClassData` düğüm şu alt düğümleri ve öznitelikleri içerir:

- Verilerin geçerli olduğu sınıfa başvuran bir bilinen ad düğümü.

- Sınıfında tanımlanan her bir özellik için **XmlPropertyData** .

- Sınıfında kaynağı bulunan her ilişki için **XmlRelationshipData** . (İlişkilerin Ayrıca kendi XmlClassData düğümleri de vardır.)

- Oluşturulan koddaki serileştirme Yardımcısı sınıfının adını belirleyen **TypeName** dize özniteliği.

- **ElementName** dize, bu sınıfın SERILEŞTIRILMIŞ örneklerinin XML etiketini belirler. Kurala göre, ElementName genellikle ilk harf küçük harfli olan sınıf adı ile aynıdır. Örneğin, örnek bir model dosyası aşağıdakiler ile başlar:

    ```xml
    <componentModel ...
    ```

- **MonikerElementName** , kullanıcının serileştirilmiş model dosyalarında. Bu öznitelik, bu sınıfa başvuran bir bilinen ad tanıtır.

- Bir ad içindeki XML özniteliğinin adını tanımlayan **MonikerAttributeName**. Kullanıcının serileştirilmiş dosyasının bu parçasında, etki alanına özgü dilin yazarı, "ınportyıas" ve **MonikerAttributeName** as "path" **olarak tanımlanmıştır:**

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilder 'lar

Her bağlantı aracı için bir bağlantı Oluşturucu tanımlanmıştır. Her bir bağlantı Oluşturucusu bir veya daha fazla SourceDirective öğesi ve bir veya daha fazla TargetDirective öğesi içeren bir veya daha fazla LinkConnectDirective öğesinden oluşur. Bir bağlantı aracına tıkladıktan sonra, Kullanıcı SourceDirective öğeleri listesinde görünen model öğesiyle eşlenen herhangi bir şekilden bağlantı başlatabilir. Daha sonra bağlantı, TargetDirective öğeleri listesinde görünen bir öğe ile eşlenmiş bir şekil üzerinde tamamlanabilir. Örneklenmiş ilişki sınıfı, bağlantının başlatıldığı yer tarafından belirlenen LinkConnectDirective öğesine bağlıdır.

### <a name="xmlpropertydata"></a>XmlPropertyData

**Domainpropertydomainattribute** özniteliği, verilerin başvurduğu özelliği tanımlar. Bu öznitelik kapsayan ClassData sınıfının bir özelliği olmalıdır.

**XmlName** ÖZNITELIĞI, XML dosyasında görünmesi için karşılık gelen öznitelik adını verir. Kural gereği, bu dize, ilk harf küçük harfli olan özellik adı ile aynıdır.

Varsayılan olarak, **Gösterim** özniteliği özniteliği olarak ayarlanır. **Temsili** öğesi olarak AYARLANDıYSA, XML 'de bir alt düğüm oluşturulur. **Temsili** Ignore olarak ayarlandıysa, özellik serileştirilmez.

**IsMonikerKey** ve **IsMonikerQualifier** öznitelikleri, bir özelliğe üst sınıfın bazı örneklerini tanımlayan bir rol verir. Bir sınıf tarafından tanımlanan veya devralınan bir özellik için **IsMonikerKey** değerini true olarak ayarlayabilirsiniz. Bu öznitelik, üst sınıfın tek bir örneğini tanımlar. Olarak ayarladığınız özelliği `IsMonikerKey` genellikle bir ad veya başka bir anahtar tanımlayıcısıdır. Örneğin `Name` dize özelliği, NamedElement ve türetilmiş sınıflarının bilinen ad anahtarıdır. Kullanıcı bir modeli dosyaya kaydettiğinde, bu özniteliğin her bir örnek için benzersiz değerler içermesi gerekir, bu öznitelik, katıştırma ilişkisi ağacındaki eşdüzey değerleri arasında her bir örnek için benzersiz değerler içermelidir.

Seri hale getirilmiş model dosyasında, bir öğenin tam bilinen adı, her bir noktada bilinen ad anahtarı ' nı tırnak içine alarak, ekleme ilişkilerinin ağacı olan model kökünün bir yoludur. Örneğin, InPort bileşenleri içine katıştırılır ve bu da model köküne katıştırılır. Bu nedenle geçerli bir bilinen ad:

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Bir dize özelliği için **IsMonikerQualifier** özniteliğini ayarlayabilir ve bir öğenin tam adını oluşturmak için ek bir yol sağlayabilirsiniz. Örneğin, DslDefinition. dsl dosyasında **ad alanı** bir ad niteleyicisi.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

Seri hale getirilmiş bir model dosyasında, bağlantılar (katıştırma ve başvuru ilişkilerinin her ikisi de), ilişkinin kaynak ucunun alt düğümleri tarafından temsil edilir. İlişki ekleme için alt düğüm bir alt ağaç içerir. Başvuru ilişkileri için alt düğüm, ağacın başka bir bölümüne başvuran bir bilinen ad içerir.

Bir **XmlClassData** özniteliğinde **XmlRelationshipData** özniteliği, alt düğümlerin kaynak öğe içinde nasıl iç içe yerleştiğinizi tam olarak tanımlar. Etki alanı sınıfındaki bir kaynak olan her ilişki bir **XmlRelationshipData** özniteliğine sahiptir.

**Domainrelationshipbilinen** adı özniteliği, sınıfında kaynak olan ilişkilerden birini tanımlar.

**RoleElementName** özniteliği, seri hale getirilen verilerde alt düğümü kapsayan XML etiketi adını verir.

Örneğin, DslDefinition. dsl dosyası şunları içerir:

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

**UseFullForm** özniteliği true olarak ayarlanırsa, ek bir iç içe geçme katmanı ortaya çıkartılır. Bu katman ilişkiyi temsil eder. İlişkinin özellikleri varsa özniteliğin true olarak ayarlanması gerekir.

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

(Bağlantı Ilişkisinin kendi öğesi ve öznitelik adlarını sağlayan kendi XML sınıfı verileri vardır.)

**OmitElement** özniteliği true olarak ayarlanırsa, ilişki rolü adı atılır, bu, serileştirilmiş dosyayı abbreviates ve iki sınıfın birden fazla ilişkisi yoksa çok büyük olur. Örneğin:

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Etki alanına özgü dil tanımının serileştirilmesi

DslDefinition. dsl dosyası bir seri hale getirilmiş dosyadır ve alana özgü dil tanımına uyar. Aşağıda XML serileştirme tanımlarının bazı örnekleri verilmiştir:

- **DSL** , RootClass düğümüdür ve diyagram sınıfıdır. DomainClass, DomainRelationship ve diğer öğeler altına katıştırılır `Dsl` .

- **Sınıflar** , etki alanına özgü dil ve DomainClass arasındaki Ilişkinin **RoleElementName** ' dir.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- **XmlSerializationBehavior** özniteliği özniteliğin altına katıştırılır `Dsl` , ancak ekleme Ilişkisinde **OmitElement** özniteliği ayarlanmıştır. Bu nedenle, hiçbir `RoleElementName` öznitelik müdahalesi yok. Buna karşılık, bir **ClassData** özniteliği, `RoleElementName` bir **XmlSerializationBehavior** özniteliği ve **XmlClassData** özniteliği arasındaki katıştırma ilişkisinin özniteliğidir.

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- Connectorhasdekorators, ve arasındaki katıştırma ilişkisidir `Connector` `Decorator` . `UseFullForm` , ilişki adının bağlayıcı nesnesinden her bir bağlantı için özellikler listesiyle birlikte görünmesi için ayarlanmıştır. Ancak, `OmitElement` `RoleElementName` içine eklenen birden çok bağlantıyı hiçbir şekilde içermemesi için de ayarlanmıştır `Connector` :

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

## <a name="shape-maps"></a>Şekil haritaları

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

### <a name="decorator-maps"></a>Dekoratör haritaları

Dekoratör eşlemesi eşlenen sınıftaki bir özelliği şekildeki dekoratör ile ilişkilendirir. Özellik numaralandırılmış veya Boolean bir tür ise, değeri dekoratörün görünür olup olmadığını belirleyebilir. Dekoratör bir metin dekoratör ise, özelliğin değeri görünebilir ve Kullanıcı onu düzenleyebilir.

### <a name="compartment-shape-maps"></a>Bölme şekli eşlemeleri

Bölme şekli eşlemeleri şekil haritalarının alt türleri.

## <a name="connector-maps"></a>Bağlayıcı haritaları

En az bağlayıcı eşlemesi bir bağlayıcıya ve bir ilişkiye başvurur:

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Bağlayıcı haritaları, dekoratör haritaları da içerebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
