---
title: 'Nasıl yapılır: Uzantılar için kural tabanlı kullanıcı arabirimi bağlamını kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: 26f66f635b2c248af01067d9dbd96fd997593593
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535570"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl Yapılır: Visual Studio Uzantıları için Kural Tabanlı UI Bağlamı Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, belirli bir tanınmış s etkinleştirildiğinde VSPackages yüklemesine olanak tanır <xref:Microsoft.VisualStudio.Shell.UIContext> . Ancak, bu kullanıcı arabirimi bağlamları çok hassas değildir, ancak uzantı yazarlarının hiçbir seçim yapmadan, ancak VSPackage 'ın yüklenmesini gerçekten istediği noktadan önce etkinleştiren kullanılabilir bir kullanıcı arabirimi bağlamını seçer. İyi bilinen kullanıcı arabirimi bağlamlarının bir listesi için bkz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> ..

 Paketlerin yüklenmesi bir performans etkisine sahip olabilir ve bu uygulamaların gerekenden daha önce yüklenmesi en iyi uygulamadır. Visual Studio 2015, kural tabanlı kullanıcı arabirimi bağlamları kavramını kullanıma sunmuştur ve bu sayede uzantı yazarlarının, Kullanıcı arabirimi bağlamı etkinleştirilmiş ve ilişkili VSPackages 'nin altında kesin koşulları tanımlamasına imkan tanıyan bir mekanizma.

## <a name="rule-based-ui-context"></a>Kural tabanlı kullanıcı arabirimi bağlamı
 "Rule" yeni bir kullanıcı arabirimi bağlamından (GUID) ve mantıksal "ve", "veya", "değil" işlemlerine göre birleştirilmiş bir veya daha fazla "terim" başvurusu yapan bir Boolean ifadeden oluşur. "Terimler", çalışma zamanında dinamik olarak değerlendirilir ve her bir terim değiştiğinde ifade yeniden değerlendirilir. İfade true olarak değerlendirilirse, ilişkili UI bağlamı etkinleştirilir. Aksi takdirde, Kullanıcı arabirimi bağlamı da devre dışı bırakılır.

 Kural tabanlı kullanıcı arabirimi bağlamı çeşitli yollarla kullanılabilir:

1. Komutlar ve araç pencereleri için görünürlük kısıtlamalarını belirtin. Kullanıcı arabirimi bağlam kuralı karşılanana kadar komutlar/araçlar pencerelerini gizleyebilirsiniz.

2. Otomatik yükleme kısıtlamaları olarak: yalnızca kural karşılandığında paketleri otomatik yükle

3. Gecikmeli görev: belirtilen bir Aralık geçene ve kural karşılanana kadar yükleme gecikmesi.

   Mekanizması herhangi bir Visual Studio uzantısı tarafından kullanılabilir.

## <a name="create-a-rule-based-ui-context"></a>Kural tabanlı kullanıcı arabirimi bağlamı oluşturma
 Yalnızca ". config" uzantısına sahip dosyalar için geçerli olan bir menü komutu sunan TestPackage adlı bir uzantıya sahip olduğunuzu varsayalım. VS2015 önce, UI bağlamı etkinleştirildiğinde en iyi seçenek TestPackage 'i yükleiydi <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> . Bu, yüklenen çözüm bir. config dosyası içerememesine rağmen etkili değildir. Yalnızca. config uzantılı bir dosya seçildiğinde ve kullanıcı ARABIRIMI bağlamı etkinleştirildiğinde TestPackage 'i kullanarak bir UI bağlamını etkinleştirmek için kurallar tabanlı kullanıcı arabirimi bağlamının nasıl kullanılabileceğini görelim.

1. Yeni bir UIContext GUID tanımlayın ve VSPackage sınıfına ve öğesine ekleyin <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Örneğin, yeni bir UIContext "Uıcontextguid" ekleneceğini varsayalım. Oluşturulan GUID (araçlara tıklayarak bir GUID oluşturabilirsiniz-> Guid oluştur) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B" olur. Ardından paket sınıfınızın içine aşağıdakini ekleyin:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Öznitelikler için şunları ekleyin: (Bu özniteliklerin ayrıntıları daha sonra açıklanacaktır)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Bu meta veriler, yeni UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terime başvuran bir ifade ("DotConfig") tanımlar. Etkin hiyerarşideki geçerli seçimin ". config $" normal ifade düzeniyle eşleşen bir adı olduğunda "DotConfig" terimi true olarak değerlendirilir \\ (". config" ile biter). (Varsayılan) değeri, hata ayıklama için yararlı bir kural için isteğe bağlı bir ad tanımlar.

    Öznitelik değerleri, derleme zamanı sırasında oluşturulan pkgdef öğesine eklenir.

2. TestPackage komutları için VSCT dosyasında, uygun komutlara "DynamicVisibility" bayrağını ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT 'ın görünürlükleri bölümünde, uygun komutları #1 tanımlı yeni Uıtext GUID 'sine bağlayın:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde UIContext tanımını ekleyin:

   ```xml
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Artık, *. config dosyaları için bağlam menüsü komutları yalnızca Çözüm Gezgini 'ndeki seçili öğe bir ". config" dosyası olduğunda görünür ve bu komutlardan biri seçilene kadar paket yüklenmez.

   Daha sonra, paketin yalnızca öğesini beklediğimiz sırada yüklediğini doğrulamak için bir hata ayıklayıcı kullanalım. TestPackage hata ayıklaması yapmak için:

5. Yönteminde bir kesme noktası ayarlayın <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

6. TestPackage oluşturun ve hata ayıklamayı başlatın.

7. Bir proje oluşturun veya birini açın.

8. Uzantısı. config dışında herhangi bir dosya seçin. Kesme noktası isabet ettirilmemelidir.

9. App.Config dosyasını seçin.

   TestPackage kesme noktasında yüklenir ve durmaktadır.

## <a name="adding-more-rules-for-ui-context"></a>UI bağlamı için daha fazla kural ekleme
 UI bağlam kuralları Boole ifadeleri olduğundan, bir UI bağlamı için daha kısıtlı kurallar ekleyebilirsiniz. Örneğin, yukarıdaki kullanıcı arabirimi bağlamında, kuralın yalnızca proje içeren bir çözüm yüklendiğinde uygulanacağını belirtebilirsiniz. Bu şekilde, bir ". config" dosyasını bir projenin parçası olarak değil tek başına bir dosya olarak açarsanız komutlar gösterilmez.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Artık ifade üç koşullara başvurur. İlk iki terim olan "SingleProject" ve "MultipleProjects", iyi bilinen diğer kullanıcı arabirimi bağlamlarına (GUID 'lerine göre) başvurur. "DotConfig" üçüncü terimi, daha önce tanımladığımız kural tabanlı kullanıcı arabirimi bağlamıdır.

## <a name="delayed-activation"></a>Gecikmeli etkinleştirme
 Kuralların isteğe bağlı bir "gecikmesi" olabilir. Gecikme milisaniye cinsinden belirtilir. Varsa, gecikme bir kuralın Kullanıcı arabirimi bağlamının etkinleştirilmesinin veya devre dışı bırakılmasının bu zaman aralığı ile ertelenmesini sağlar. Kural gecikme aralığından önce geri değişirse hiçbir şey olmaz. Bu mekanizma, zamanlayıcılara bağlı olmadan veya boşta bildirimleri için kayıt yaptırmadan, özellikle bir kerelik başlatma adımları için "hazırlama" işlemi yapmak için kullanılabilir.

 Örneğin, test yükleme kuralınızı 100 milisaniyelik bir gecikme olacak şekilde belirtebilirsiniz:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Terim türleri
 Desteklenen çeşitli terim türleri şunlardır:

|Terim türü|Description|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID, bir UI bağlamını ifade eder. Kullanıcı arabirimi bağlamı etkin olduğunda terim true, aksi durumda false olur.|
|HierSingleSelectionName:\<pattern>|Etkin hiyerarşide seçim tek bir öğe olduğunda ve seçili öğenin adı "model" tarafından verilen .net normal ifadesiyle eşleştiğinde, terim true olur.|
|UserSettingsStoreQuery:\<query>|"sorgu", sıfır olmayan bir değer olarak değerlendirilmesi gereken Kullanıcı ayarları deposunun tam yolunu temsil eder. Sorgu, son eğik çizgiden bir "Collection" ve "propertyName" olarak bölünür.|
|ConfigSettingsStoreQuery:\<query>|"sorgu", sıfır olmayan bir değer olarak değerlendirilmesi gereken yapılandırma ayarları deposunun tam yolunu temsil eder. Sorgu, son eğik çizgiden bir "Collection" ve "propertyName" olarak bölünür.|
|ActiveProjectFlavor:\<projectTypeGuid>|Şu anda seçili olan proje flavokken (toplanmış) ve belirtilen proje türü GUID 'SI ile eşleşen bir Flavor olduğunda, terim doğru olacaktır.|
|ActiveEditorContentType:\<contentType>|Seçili belge, verilen içerik türüne sahip bir metin Düzenleyicisi olduğunda, terim true olur.|
|ActiveProjectCapability:\<Expression>|Etkin proje özellikleri, belirtilen ifadeyle eşleştiğinde, terim true olur. İfade, VB &#124; CSharp gibi bir şey olabilir|
|SolutionHasProjectCapability:\<Expression>|Yukarıdaki ifadeye benzer ancak çözüm, ifadeyle eşleşen herhangi bir yüklü projeye sahip olduğunda terim doğrudur.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Bir çözümde flavored (toplanmış) projesi olduğunda ve belirtilen proje türü GUID 'SI ile eşleşen bir Flavor olduğunda terim true olur.|

## <a name="compatibility-with-cross-version-extension"></a>Sürümler arası uzantıyla uyumluluk
 Kural tabanlı kullanıcı arabirimi bağlamları, Visual Studio 2015 ' deki yeni bir özelliktir ve önceki sürümlere verilmez. Bu, Visual Studio 'nun Visual Studio 2013 ve önceki sürümlerinde otomatik olarak yüklenmesi gereken, ancak Visual Studio 2015 ' de otomatik olarak yüklenmesini engellemek için kural tabanlı kullanıcı arabirimi bağlamlarından faydalanabilecek uzantılar/paketlerle ilgili bir sorun oluşturur.

 Bu tür paketleri desteklemek için, kayıt defterindeki oto Loadpackages girdileri artık girişin Visual Studio 2015 ve üzeri sürümlerde atlanması gerektiğini göstermek için değer alanında bir bayrak sağlayabilir. Bu, öğesine bir bayrak seçeneği eklenerek yapılabilir <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . VSPackages artık, girişin Visual Studio 2015 ve üzeri sürümlerde yoksayılıp sayılmayacağını belirtmek için kendi özniteliğine **Skipwhenuicontextrulesactive** seçeneğini ekleyebilirler <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> .

## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI bağlam kuralları
 Bazen, paketler statik UI bağlamı kurallarını kullanamaz. Örneğin, komut durumunun içeri aktarılan MEF sağlayıcıları tarafından desteklenen düzenleyici türlerini temel aldığı gibi, genişletilebilirliği destekleyen bir paketiniz olduğunu varsayalım. Geçerli düzenleme türünü destekleyen bir uzantı varsa komut etkinleştirilir. Bu tür durumlarda, şartlar hangi MEF uzantılarının kullanılabilir olduğuna bağlı olarak değişecağından, paketin kendisi statik bir UI bağlam kuralını kullanamaz.

 Bu tür paketleri desteklemek için, kural tabanlı kullanıcı arabirimi bağlamları, aşağıdaki tüm koşulların veya ile birleştirildiğini belirten, "*" sabit kodlanmış ifadesini destekler. Bu, ana paketin bilinen bir kural tabanlı kullanıcı arabirimi bağlamını tanımlamasına ve komut durumunu bu bağlama bağlamaktır. Daha sonra ana paket için hedeflenen MEF uzantısı, diğer terimleri veya ana ifadeyi etkilemeden desteklediği düzenleyicilerin koşullarını ekleyebilir.

 Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeleri, GENIŞLETILEBILIR UI bağlam kuralları için söz dizimini gösterir.
