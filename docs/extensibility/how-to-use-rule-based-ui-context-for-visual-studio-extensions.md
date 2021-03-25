---
title: Visual Studio uzantıları için kural tabanlı kullanıcı arabirimi bağlamını kullanma
titleSuffix: ''
description: Uzantı yazarlarının, bir kullanıcı arabirimi bağlamı etkinleştirildiğinde ve VSPackages yüklendiğinde koşul tanımlamasına izin veren kural tabanlı kullanıcı arabirimi bağlamlarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 0ce09edd20c0c46a6b93ace77808fdfc7d5d1c5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057370"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl yapılır: Visual Studio uzantıları için kural tabanlı kullanıcı arabirimi bağlamını kullanma

Visual Studio, belirli bir tanınmış s etkinleştirildiğinde VSPackages yüklemesine olanak tanır <xref:Microsoft.VisualStudio.Shell.UIContext> . Ancak, bu UI bağlamları, uzantı yazarlarını hiçbir seçim yapmadan, ancak VSPackage 'ın yüklenmesini gerçekten istedikleri noktadan önce etkinleştiren kullanılabilir bir kullanıcı arabirimi bağlamını seçmeyen hassas değildir. İyi bilinen kullanıcı arabirimi bağlamlarının bir listesi için bkz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> ..

Paketlerin yüklenmesi bir performans etkisine sahip olabilir ve bu uygulamaların gerekenden daha kısa bir şekilde yüklenmesi en iyi uygulamadır. Visual Studio 2015, uzantı yazarlarının bir UI bağlamı etkinleştirildiği ve ilişkili VSPackages 'nin yüklendiği kesin koşulları tanımlamasına imkan tanıyan bir mekanizma olan kural tabanlı UI bağlamları kavramını sunmuştur.

## <a name="rule-based-ui-context"></a>Kural tabanlı kullanıcı arabirimi bağlamı

"Rule" yeni bir kullanıcı arabirimi bağlamından (GUID) ve mantıksal "ve", "veya", "değil" işlemlerine göre birleştirilmiş bir veya daha fazla "terim" başvurusu yapan bir Boolean ifadeden oluşur. "Terimler", çalışma zamanında dinamik olarak değerlendirilir ve koşullarından herhangi biri değiştiğinde ifade yeniden değerlendirilir. İfade true olarak değerlendirilirse, ilişkili UI bağlamı etkinleştirilir. Aksi takdirde, Kullanıcı arabirimi bağlamı da devre dışı bırakılır.

Kural tabanlı kullanıcı arabirimi bağlamı çeşitli yollarla kullanılabilir:

1. Komutlar ve araç pencereleri için görünürlük kısıtlamalarını belirtin. Kullanıcı arabirimi bağlam kuralı karşılanana kadar komutlar/araçlar pencerelerini gizleyebilirsiniz.

2. Otomatik yükleme kısıtlamaları olarak: yalnızca kural karşılandığında paketleri otomatik yükle.

3. Geciktirilen bir görev: belirtilen bir Aralık geçene ve kural hala karşılanana kadar yükleme gecikmesi.

   Mekanizması herhangi bir Visual Studio uzantısı tarafından kullanılabilir.

## <a name="create-a-rule-based-ui-context"></a>Kural tabanlı kullanıcı arabirimi bağlamı oluşturma
 Yalnızca *. config* uzantılı dosyalar için geçerli olan bir menü komutu sunan testpackage adlı bir uzantıya sahip olduğunuzu varsayalım. VS2015 önce, UI bağlamı etkinleştirildiğinde en iyi seçenek TestPackage 'i yükleiydi <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> . Bu şekilde TestPackage yüklemesi etkili değildir, çünkü yüklenen çözüm bir *. config* dosyası içeremez. Bu adımlarda, kural tabanlı kullanıcı arabirimi bağlamının yalnızca *. config* uzantılı bir dosya SEÇILDIĞINDE bir UI bağlamını etkinleştirmek ve bu kullanıcı arabirimi bağlamı etkinleştirildiğinde testpackage 'i yüklemek için nasıl kullanılabileceği gösterilmektedir.

1. Yeni bir UIContext GUID tanımlayın ve VSPackage sınıfına ve öğesine ekleyin <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Örneğin, yeni bir UIContext "Uıcontextguid" ekleneceğini varsayalım. Oluşturulan GUID ( **Araçlar** oluştur GUID ' ye tıklayarak bir GUID oluşturabilirsiniz  >  ) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B" olur. Ardından, paket sınıfınızın içine aşağıdaki bildirimi eklersiniz:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Öznitelikler için şu değerleri ekleyin: (Bu özniteliklerin ayrıntıları daha sonra açıklanacaktır)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Bu meta veriler, yeni UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terime başvuran bir ifade ("DotConfig") tanımlar. Etkin hiyerarşideki geçerli seçimin ". config $" normal ifade düzeniyle eşleşen bir adı olduğunda "DotConfig" terimi true olarak değerlendirilir \\ ( *. config* ile biter). (Varsayılan) değeri, hata ayıklama için yararlı bir kural için isteğe bağlı bir ad tanımlar.

    Öznitelik değerleri, derleme zamanı sırasında oluşturulan pkgdef öğesine eklenir.

2. TestPackage komutları için VSCT dosyasında, uygun komutlara "DynamicVisibility" bayrağını ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT 'ın görünürlükleri bölümünde, uygun komutları #1 tanımlı yeni Uıtext GUID 'sine bağlayın:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde UIContext tanımını ekleyin:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Artık, *\* . config* dosyaları için bağlam menüsü komutları yalnızca Çözüm Gezgini 'ndeki seçili öğe bir *. config* dosyası olduğunda ve bu komutlardan biri seçilene kadar paket yüklenemeyecek şekilde görünür.

   Daha sonra, paketin yalnızca bunu beklediğinde yüklediğini doğrulamak için bir hata ayıklayıcı kullanın. TestPackage hata ayıklaması yapmak için:

5. Yönteminde bir kesme noktası ayarlayın <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

6. TestPackage oluşturun ve hata ayıklamayı başlatın.

7. Bir proje oluşturun veya birini açın.

8. Uzantısı *. config* dışında herhangi bir dosya seçin. Kesme noktası isabet ettirilmemelidir.

9. *App.Config* dosyasını seçin.

   TestPackage kesme noktasında yüklenir ve durmaktadır.

## <a name="add-more-rules-for-ui-context"></a>UI bağlamı için daha fazla kural ekleyin
 UI bağlam kuralları Boole ifadeleri olduğundan, bir UI bağlamı için daha kısıtlı kurallar ekleyebilirsiniz. Örneğin, yukarıdaki kullanıcı arabirimi bağlamında, kuralın yalnızca proje içeren bir çözüm yüklendiğinde uygulanacağını belirtebilirsiniz. Bu şekilde, bir *. config* dosyasını bir projenin parçası olarak değil tek başına bir dosya olarak açarsanız komutlar gösterilmez.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Artık ifade üç koşullara başvurur. İlk iki terim olan "SingleProject" ve "MultipleProjects", iyi bilinen diğer kullanıcı arabirimi bağlamlarına (GUID 'lerine göre) başvurur. "DotConfig" üçüncü terimi, bu makalede daha önce tanımlanan kural tabanlı kullanıcı arabirimi bağlamıdır.

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

|Süre|Açıklama|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID, bir UI bağlamını ifade eder. Kullanıcı arabirimi bağlamı etkin olduğunda terim true, aksi durumda false olur.|
|HierSingleSelectionName:\<pattern>|Etkin hiyerarşide seçim tek bir öğe olduğunda ve seçili öğenin adı "model" tarafından verilen .net normal ifadesiyle eşleştiğinde, terim true olur.|
|UserSettingsStoreQuery:\<query>|"sorgu", sıfır olmayan bir değer olarak değerlendirilmesi gereken Kullanıcı ayarları deposunun tam yolunu temsil eder. Sorgu, son eğik çizgiden bir "Collection" ve "propertyName" olarak bölünür.|
|ConfigSettingsStoreQuery:\<query>|"sorgu", sıfır olmayan bir değere değerlendirilmesi gereken yapılandırma ayarları deposunun tam yolunu temsil eder. Sorgu, son eğik çizgiden bir "Collection" ve "propertyName" olarak bölünür.|
|ActiveProjectFlavor:\<projectTypeGuid>|Şu anda seçili olan proje flavokken (toplanmış) ve belirtilen proje türü GUID 'SI ile eşleşen bir Flavor olduğunda, terim doğru olacaktır.|
|ActiveEditorContentType:\<contentType>|Seçili belge, verilen içerik türüne sahip bir metin Düzenleyicisi olduğunda, terim true olur. Not: Seçilen belge yeniden adlandırıldığında, Dosya kapatılıp yeniden açılıncaya kadar bu terim yenilenmez.|
|ActiveProjectCapability:\<Expression>|Etkin proje özellikleri, belirtilen ifadeyle eşleşiyorsa, terim true olur. Bir ifade VB &#124; CSharp gibi bir şey olabilir.|
|SolutionHasProjectCapability:\<Expression>|Yukarıdaki ifadeye benzer ancak çözüm, ifadeyle eşleşen herhangi bir yüklü projeye sahip olduğunda terim doğrudur.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Bir çözümde flavored (toplanmış) projesi olduğunda ve belirtilen proje türü GUID 'SI ile eşleşen bir Flavor olduğunda terim true olur.|
|Projectaddedıtem:\<pattern>| "Model" ile eşleşen bir dosya, açılan bir projede bir projeye eklendiğinde true olur.|
|ActiveProjectOutputType:\<outputType>|Etkin projenin çıkış türü tam olarak eşleştiğinde terim true olur.  OutputType bir tamsayı veya <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> tür olabilir.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Etkin proje belirtilen derleme özelliğine sahip olduğunda ve değeri, Regex filtresiyle eşleşen özellik değeri ile eşleştiğinde, bu koşul doğrudur. Derleme özellikleri hakkında daha fazla bilgi için [MSBuild proje dosyalarındaki kalıcı verilere](internals/persisting-data-in-the-msbuild-project-file.md) bakın.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Çözümde belirtilen derleme özelliğine sahip yüklü bir proje olduğunda ve özellik değeri, Regex filtresi ile eşleştiğinde terim true olur.|

## <a name="compatibility-with-cross-version-extension"></a>Sürümler arası uzantıyla uyumluluk

Kural tabanlı kullanıcı arabirimi bağlamları, Visual Studio 2015 ' deki yeni bir özelliktir ve önceki sürümlere verilmez. Önceki sürümlere taşıma, Visual Studio 'nun birden çok sürümünü hedefleyen uzantılar/paketlerle ilgili bir sorun oluşturur. Bu sürümlerin Visual Studio 2013 ve önceki sürümlerde otomatik olarak yüklenmesi gerekir, ancak Visual Studio 2015 ' de otomatik olarak yüklenmesini engellemek için kural tabanlı kullanıcı arabirimi bağlamlarından faydalanabilir.

Bu tür paketleri desteklemek için, kayıt defterindeki oto Loadpackages girdileri artık girişin Visual Studio 2015 ve üzeri sürümlerde atlanması gerektiğini göstermek için değer alanında bir bayrak sağlayabilir. Bu, öğesine bir bayrak seçeneği eklenerek yapılabilir <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . VSPackages artık, girişin Visual Studio 2015 ve üzeri sürümlerde yoksayılıp sayılmayacağını belirtmek için kendi özniteliğine **Skipwhenuicontextrulesactive** seçeneğini ekleyebilirler <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> .
## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI bağlam kuralları

Bazen, paketler statik UI bağlamı kurallarını kullanamaz. Örneğin, komut durumunun içeri aktarılan MEF sağlayıcıları tarafından desteklenen düzenleyici türlerini temel aldığı gibi, genişletilebilirliği destekleyen bir paketiniz olduğunu varsayalım. Geçerli düzenleme türünü destekleyen bir uzantı varsa komut etkinleştirilir. Bu gibi durumlarda, şartlar hangi MEF uzantılarının kullanılabilir olduğuna bağlı olarak değişecağından, paketin kendisi statik bir UI bağlamı kuralı kullanamaz.

Bu tür paketleri desteklemek için, kural tabanlı kullanıcı arabirimi bağlamları, aşağıdaki tüm koşulların veya ile birleştirildiğini gösteren "*" sabit kodlanmış ifadesini destekler. Bu, ana paketin bilinen kural tabanlı bir kullanıcı arabirimi bağlamını tanımlamasına ve komut durumunu bu bağlama bağlamasına olanak sağlar. Daha sonra ana paket için hedeflenen MEF uzantısı, diğer terimleri veya ana ifadeyi etkilemeden desteklediği düzenleyicilerin koşullarını ekleyebilir.

Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeleri, GENIŞLETILEBILIR UI bağlam kuralları için söz dizimini gösterir.
