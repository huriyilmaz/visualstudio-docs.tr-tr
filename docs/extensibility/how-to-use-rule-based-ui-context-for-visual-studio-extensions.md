---
title: Kullanıcı arabirimi uzantıları için kural Visual Studio kullanma
titleSuffix: ''
description: Uzantı yazarlarının bir KULLANıCı Arabirimi Bağlamı etkinleştirildiğinde ve VSPackage'lar yüklendiğinde koşulları tanımlamalarına olanak sağlayan Kural tabanlı UI Bağlamları'nın nasıl kullanılamayacaklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 0ce09edd20c0c46a6b93ace77808fdfc7d5d1c5d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626252"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl yapabilirsiniz: Kullanıcı arabirimi uzantıları için kural Visual Studio kullanma

Visual Studio, bilinen belirli s'ler etkinleştirildiğinde VSPackage'ların <xref:Microsoft.VisualStudio.Shell.UIContext> yüklenmesine izin verir. Ancak bu KULLANıCı Arabirimi Bağlamları, uzantı yazarlarının VSPackage'ın yüklemesi istediği noktadan önce etkinleştirilen kullanılabilir bir KULLANıCı Arabirimi Bağlamı seçmekten başka bir seçenek bırakmayacak şekilde ince bilgili değildir. İyi bilinen kullanıcı arabirimi bağlamlarının listesi için bkz. <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Paketlerin yüklenmesi performansı etkileyebilir ve gerektiğinden daha erken yüklenmesi en iyi yöntem değildir. Visual Studio 2015'te, uzantı yazarlarının kullanıcı arabirimi bağlamının etkinleştirildikten ve ilişkili VSPackage'ların yükleniyor olduğu kesin koşulları tanımlamalarına olanak sağlayan kural tabanlı UI Bağlamları kavramı ortaya çıktı.

## <a name="rule-based-ui-context"></a>Kural Tabanlı Kullanıcı Arabirimi Bağlamı

"Kural" yeni bir KULLANıCı Arabirimi Bağlamı (GUID) ve mantıksal "and", "or", "not" işlemleriyle birleştirilmiş bir veya daha fazla "Terime" başvurulan Boole ifadelerinden oluşur. "Terimler", çalışma zamanında dinamik olarak değerlendirilir ve terimlerden herhangi biri her değiştiklerinde ifade yeniden değerlendirilir. İfade true olarak değerlendirildiğinde ilişkili KULLANıCı Arabirimi Bağlamı etkinleştirilir. Aksi takdirde KULLANıCı Arabirimi Bağlamı devre dışıdır.

Kural tabanlı UI Bağlamı çeşitli yollarla kullanılabilir:

1. Komutlar ve araç pencereleri için görünürlük kısıtlamalarını belirtin. Kullanıcı Arabirimi Bağlam kuralı karşı gelene kadar komutlar/araçlar pencerelerini gizleyebilirsiniz.

2. Otomatik yükleme kısıtlamaları olarak: Paketleri yalnızca kurala karşı geldiğinde otomatik olarak yükle.

3. Gecikmeli bir görev olarak: Belirtilen bir aralık geçinceye ve kural yine karşı olana kadar yüklemeyi geciktirin.

   Mekanizma herhangi bir uzantı tarafından Visual Studio kullanılabilir.

## <a name="create-a-rule-based-ui-context"></a>Kural tabanlı ui bağlamı oluşturma
 TestPackage adlı bir uzantınız olduğunu ve bu uzantının yalnızca uzantıya sahip dosyalar için geçerli *.config* düşünün. VS2015'den önce en iyi seçenek, UI Bağlamı etkinleştirildiğinde TestPackage <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> yüklemekti. TestPackage'ın bu şekilde yüklenmesi verimli değildir çünkü yüklenen çözümde bir.config *bile* bulunamıyor olabilir. Bu adımlar, kullanıcı arabirimi bağlamını yalnızca.configuzantısına sahip bir  dosya seçildiğinde etkinleştirmek ve bu UI Bağlamı etkinleştirildiğinde TestPackage yüklemek için kural tabanlı UI Bağlamının nasıl kullanıl olduğunu gösterir.

1. Yeni bir UIContext GUID tanımlayın ve VSPackage sınıfına ve <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> ekleyin.

    Örneğin, yeni bir UIContext "UIContextGuid" ekleniyor olduğunu varsayalım. Oluşturulan GUID (Araçlar GUID Oluştur'a tıklayarak GUID oluşturabilirsiniz)  >  "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B" şeklindedir. Ardından paket sınıfınıza aşağıdaki bildirimi ekleyin:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Öznitelikler için şu değerleri ekleyin: (Bu özniteliklerin ayrıntıları daha sonra açıklanmıştır)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Bu meta veriler yeni UIContext GUID'sini (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terim olan "DotConfig" terimine başvuran bir ifadeyi tanımlar. Etkin hiyerarşide geçerli seçim ".config$" normal ifade deseniyle eşleşen bir ada sahip olduğunda "DotConfig" terimi true olarak \\ *değerlendirilir*(.config). (Varsayılan) değeri, hata ayıklama için yararlı olan kural için isteğe bağlı bir ad tanımlar.

    Özniteliğin değerleri daha sonra derleme zamanında oluşturulan pkgdef'e eklenir.

2. TestPackage komutlarının VSCT dosyasında uygun komutlara "DynamicVisibility" bayrağını ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT'nin Görünürlükler bölümünde, uygun komutları aşağıdaki komutlarda tanımlanan yeni UIContext GUID'#1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde UIContext tanımını ekleyin:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Artık, *\*.config* dosyaları için bağlam menüsü komutları yalnızca çözüm gezgininde seçilen öğe bir *.config* dosyası olduğunda görünür olur ve bu komutlardan biri seçilene kadar paket yüklenmez.

   Ardından, paketin yalnızca beklediğiniz zaman yük olduğunu onaylamak için bir hata ayıklayıcı kullanın. TestPackage'da hata ayıklamak için:

5. yönteminde bir kesme noktası <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> ayarlayın.

6. TestPackage'ı derleme ve hata ayıklamayı başlatma.

7. Proje oluşturun veya bir proje açın.

8. dosya adı dışında bir uzantıya sahip herhangi bir *.config.* Kesme noktası isabetli değildir.

9. App.Config *seçin.*

   TestPackage yüklenir ve kesme noktası içinde durur.

## <a name="add-more-rules-for-ui-context"></a>UI Bağlamı için daha fazla kural ekleme
 UI Bağlam kuralları Boole ifadeleri olduğu için, ui bağlamı için daha fazla kısıtlanmış kural ekleyin. Örneğin, yukarıdaki KULLANıCı Arabirimi Bağlamı'da kuralın yalnızca projeli bir çözüm yüklendiğinde geçerli olduğunu belirtabilirsiniz. Bu şekilde, bir.configdosyasını projenin bir parçası *olarak* değil tek başına dosya olarak açarsanız komutlar gösterlanmaz.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 İfade şimdi üç terime başvurur. İlk iki terim olan "SingleProject" ve "MultipleProjects" diğer iyi bilinen KULLANıCı Arabirimi Bağlamlarına (GUID'leri tarafından) başvurur. Üçüncü terim olan "DotConfig", bu makalenin başlarında tanımlanan kural tabanlı KULLANıCı Arabirimi Bağlamıdır.

## <a name="delayed-activation"></a>Gecikmeli etkinleştirme
 Kurallar isteğe bağlı bir "Gecikme" olabilir. Gecikme milisaniye cinsinden belirtilir. Varsa, bu gecikme kuralın kullanıcı arabirimi bağlamının etkinleştirilmesini veya devre dışı bırakılmasına neden olur. Kural gecikme aralığından önce değişirse hiçbir şey olmaz. Bu mekanizma, özellikle de süreölçilere güvenmeden veya boşta bildirimlere kaydolmadan tek kez başlatma olmak üzere başlatma adımlarını "basamaklama" için kullanılabilir.

 Örneğin, test yük kuralınızı 100 milisaniyelik bir gecikme olacak şekilde belirterek:

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

Desteklenen çeşitli terim türleri şu şekildedir:

|Süre|Açıklama|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nn-nnnn}|GUID, kullanıcı arabirimi bağlamına başvurur. Kullanıcı Arabirimi Bağlamı etkin olduğunda terimi true, aksi takdirde false olur.|
|HierSingleSelectionName:\<pattern>|Etkin hiyerarşide yapılan seçim tek bir öğe olduğunda ve seçilen öğenin adı "desen" tarafından verilen .Net normal ifadesiyle eşle her eşlese terim true olur.|
|UserSettingsStoreQuery:\<query>|"query", kullanıcı ayarları deposuna giden ve sıfır olmayan bir değer olarak değerlendirilmesi gereken tam yolu temsil eder. Sorgu, son eğik çizgide bir "koleksiyon" ve "propertyName" olarak bölünüyor.|
|ConfigSettingsStoreQuery:\<query>|"query", yapılandırma ayarları deposuna giden ve sıfır olmayan bir değer olarak değerlendirilmesi gereken tam yolu temsil eder. Sorgu, son eğik çizgide bir "koleksiyon" ve "propertyName" olarak bölünüyor.|
|ActiveProjectFlavor:\<projectTypeGuid>|Şu anda seçili olan proje aromalı olduğunda (toplanmış) ve verilen proje türü GUID ile eşleşen bir aromaya sahip olduğunda bu terim true olur.|
|ActiveEditorContentType:\<contentType>|Seçilen belge, verilen içerik türüne sahip bir metin düzenleyicisi olduğunda bu terim true olur. Not: Seçilen belge yeniden adlandırıldı, dosya kapatılana ve yeniden açılana kadar bu terim yenilenmez.|
|ActiveProjectCapability:\<Expression>|Etkin proje özellikleri sağlanan ifadeyle eş olduğunda bu terim true olur. İfade, CSharp gibi VB &#124; olabilir.|
|SolutionHasProjectCapability:\<Expression>|Yukarıdakine benzer ancak çözümde ifadeyle eşleşen yüklü herhangi bir proje olduğunda terim true olur.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Bir çözümde aromalı (toplanmış) bir proje olduğunda ve verilen proje türü GUID ile eşleşen bir aromaya sahip olduğunda bu terim true olur.|
|ProjectAddedItem:\<pattern>| "Desen" ile eşleşen bir dosya, açılan çözünürlük içinde bir projeye ekleniyorsa bu terim true olur.|
|ActiveProjectOutputType:\<outputType>|Etkin projenin çıkış türü tam olarak eş olduğunda bu terim true olur.  outputType bir tamsayı veya tür <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> olabilir.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Etkin proje belirtilen derleme özelliğine sahip olduğunda ve özellik değeri sağlanan regex filtresiyle eş olduğunda bu terim true olur. Derleme özellikleri [hakkında daha fazla bilgi için MSBuild Project](internals/persisting-data-in-the-msbuild-project-file.md) Dosyalarında Kalıcı Veriler'e bakın.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Çözümde belirtilen derleme özelliği ve özellik değeri sağlanan regex filtresiyle eşleşen yüklenmiş bir proje olduğunda bu terim true olur.|

## <a name="compatibility-with-cross-version-extension"></a>Sürümler arası uzantıyla uyumluluk

Kural tabanlı UI Bağlamları, Visual Studio 2015'te yeni bir özelliktir ve önceki sürümlere taşınabilir. Önceki sürümlere bağlantının eski sürümlere bağlantıyla ilgili değil, birden çok sürümü hedef alan uzantılar/paketler ile ilgili bir Visual Studio. Bu sürümlerin hem Visual Studio 2013 hem de önceki sürümlerde otomatik olarak yüklenmiş olması gerekir, ancak 2015'te otomatik olarak yüklenmeyi önlemek için kural tabanlı UI Bağlamlarından Visual Studio olabilir.

bu tür paketleri desteklemek için, kayıt defterindeki oto loadpackages girdileri artık girişin Visual Studio 2015 ve üzeri sürümlerde atlanacağını göstermek için değer alanında bir bayrak sağlayabilir. Bu, öğesine bir bayrak seçeneği eklenerek yapılabilir <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . vspackages artık, girişin Visual Studio 2015 ve üzeri sürümlerde yoksayılması gerektiğini belirtmek için kendi özniteliğine **skipwhenuicontextrulesactive** seçeneğini ekleyebilirler <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> .
## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI bağlam kuralları

Bazen, paketler statik UI bağlamı kurallarını kullanamaz. Örneğin, komut durumunun içeri aktarılan MEF sağlayıcıları tarafından desteklenen düzenleyici türlerini temel aldığı gibi, genişletilebilirliği destekleyen bir paketiniz olduğunu varsayalım. Geçerli düzenleme türünü destekleyen bir uzantı varsa komut etkinleştirilir. Bu gibi durumlarda, şartlar hangi MEF uzantılarının kullanılabilir olduğuna bağlı olarak değişecağından, paketin kendisi statik bir UI bağlamı kuralı kullanamaz.

Bu tür paketleri desteklemek için, kural tabanlı kullanıcı arabirimi bağlamları, aşağıdaki tüm koşulların veya ile birleştirildiğini gösteren "*" sabit kodlanmış ifadesini destekler. Bu, ana paketin bilinen kural tabanlı bir kullanıcı arabirimi bağlamını tanımlamasına ve komut durumunu bu bağlama bağlamasına olanak sağlar. Daha sonra ana paket için hedeflenen MEF uzantısı, diğer terimleri veya ana ifadeyi etkilemeden desteklediği düzenleyicilerin koşullarını ekleyebilir.

Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeleri, GENIŞLETILEBILIR UI bağlam kuralları için söz dizimini gösterir.
