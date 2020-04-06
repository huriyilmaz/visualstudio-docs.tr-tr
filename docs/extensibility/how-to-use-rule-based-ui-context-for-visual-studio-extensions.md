---
title: 'Nasıl kullanılır: Visual Studio Uzantıları için Kural tabanlı UI Bağlamı Kullanın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710589"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl kullanılır: Visual Studio uzantıları için kural tabanlı UI Bağlamı'nı kullanma

Visual Studio, bazı tanınmış <xref:Microsoft.VisualStudio.Shell.UIContext>s etkinleştirildiğinde VSPackages'ın yüklenmesine izin verir. Ancak, bu UI Bağlamları ince taneli değildir, bu da uzantılı yazarlara VSPackage'ın gerçekten yüklenmesini istedikleri noktadan önce etkinleştirilen kullanılabilir bir UI Bağlamı seçmekten başka seçenek bırakmaz. Tanınmış UI bağlamlarının listesi için bkz. <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>

Paketleri yüklemenin bir performans etkisi olabilir ve bunları gerekenden daha kısa sürede yüklemek en iyi uygulama değildir. Visual Studio 2015, uzantı lı yazarların Kullanıcı Birkullanıcı Arası Birimi Bağlamının etkinleştirildiği ve ilişkili VSPackages'in yüklendiği kesin koşulları tanımlamasına olanak tanıyan kurallara dayalı Kullanıcı Arası Tümleçleri kavramını tanıttı.

## <a name="rule-based-ui-context"></a>Kural tabanlı UI Bağlamı

"Kural", bir veya daha fazla "Terim"e mantıksal "ve", "veya", "değil" işlemleriyle birlikte başvuran yeni bir UI Bağlamı (GUID) ve Boolean ifadesinden oluşur. "Şartlar" çalışma zamanında dinamik olarak değerlendirilir ve terimlerinden herhangi biri değiştiğinde ifade yeniden değerlendirilir. İfade doğru olarak değerlendirildiğinde, ilişkili UI Bağlamı etkinleştirilir. Aksi takdirde, UI Bağlamı devre dışı bırakılır.

Kural tabanlı UI Bağlamı çeşitli şekillerde kullanılabilir:

1. Komutlar ve araç pencereleri için görünürlük kısıtlamalarını belirtin. Kullanıcı Günül Bağlamı kuralı karşılanana kadar komutlar/araçlar windowsunu gizleyebilirsiniz.

2. Otomatik yük kısıtlamaları olarak: otomatik yük paketleri yalnızca kural yerine getirildiğinde.

3. Gecikmiş bir görev olarak: belirli bir aralık geçene ve kural yine de karşılanana kadar yüklemeyi geciktirin.

   Mekanizma herhangi bir Visual Studio uzantısı tarafından kullanılabilir.

## <a name="create-a-rule-based-ui-context"></a>Kural tabanlı u-i bağlamı oluşturma
 Yalnızca *.config* uzantılı dosyalar için geçerli olan bir menü komutu sunan TestPackage adlı bir uzantınolduğunu varsayalım. VS2015'ten önce, en iyi seçenek, UI Bağlamı etkinleştirildiğinde <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> TestPaketi'ni yüklemekti. Yüklenen çözüm *bir .config* dosyası bile içermediğinden, TestPackage'ı bu şekilde yüklemek verimli değildir. Bu adımlar, kural tabanlı UI Bağlamı'nın yalnızca *.config* uzantılı bir dosya seçildiğinde ui bağlamı etkinleştirmek için nasıl kullanılabileceğini ve bu UI Bağlamı etkinleştirildiğinde Test Paketini yükleyeceğini gösterir.

1. Yeni bir UIContext GUID tanımlayın ve <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>VSPackage sınıfına ekleyin ve.

    Örneğin, yeni bir UIContext "UIContextGuid" eklenecek varsayalım. Oluşturulan GUID **(Araçlar** > **Oluşturma GUID'e**tıklayarak bir GUID oluşturabilirsiniz) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"dir. Daha sonra paket sınıfınızın içine aşağıdaki bildirimi eklersiniz:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Öznitelikler için aşağıdaki değerleri ekleyin: (Bu özniteliklerin ayrıntıları daha sonra açıklanacaktır)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Bu meta veriler yeni UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terim, "DotConfig" atıfta bir ifade tanımlar. "DotConfig" terimi, etkin hiyerarşideki geçerli seçimin normal ifade deseni "\\.config$" *(.config*ile biter) ile eşleşen bir adı olduğunda doğru olarak değerlendirir. (Varsayılan) değeri hata ayıklama için yararlı kural için isteğe bağlı bir ad tanımlar.

    Öznitelik değerleri, daha sonra yapı süresi içinde oluşturulan pkgdef'e eklenir.

2. TestPackage komutları için VSCT dosyasında, ilgili komutlara "DynamicVisibility" bayrağını ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT'nin Görünürlükler bölümünde, uygun komutları #1 tanımlanan yeni UIContext GUID'e bağlayın:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde, UIContext tanımını ekleyin:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Şimdi, * \*.config* dosyalarının bağlam menüsü komutları yalnızca çözüm gezgininde seçili öğe *bir .config* dosyası olduğunda görünür ve bu komutlardan biri seçilene kadar paket yüklenmez.

   Ardından, paketin yalnızca beklediğiniz zaman yüklendiğinde niçin yüklendiğinden emin olmak için bir hata ayıklama kullanın. TestPaketini hata ayıklamak için:

5. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Yöntemde bir kesme noktası ayarlayın.

6. TestPaketini oluşturun ve hata ayıklamaya başlayın.

7. Bir proje oluşturun veya açın.

8. *.config*dışında uzantılı herhangi bir dosya seçin. Kırılma noktası vurulmamalıdır.

9. *App.Config* dosyasını seçin.

   TestPackage, kesme noktasında yükler ve durur.

## <a name="add-more-rules-for-ui-context"></a>UI Bağlamı için daha fazla kural ekleme
 UI Bağlam kuralları Boolean ifadeleri olduğundan, bir UI Bağlamı için daha sınırlı kurallar ekleyebilirsiniz. Örneğin, yukarıdaki Kullanıcı Arabirimi Bağlamında, kuralın yalnızca projeiçeren bir çözüm yüklendiğinde geçerli olduğunu belirtebilirsiniz. Bu şekilde, *bir .config* dosyasını projenin parçası olarak değil, bağımsız bir dosya olarak açarsanız komutlar gösterilmez.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Şimdi ifade üç terimbaşvuruyor. İlk iki terim, "SingleProject" ve "MultipleProjects", diğer tanınmış UI Bağlamları (GUID'lerine göre) bakın. Üçüncü terim, "DotConfig" bu makalede daha önce tanımlanan kural tabanlı UI Bağlamıdır.

## <a name="delayed-activation"></a>Gecikmeli etkinleştirme
 Kurallar isteğe bağlı bir "Gecikme" olabilir. Gecikme milisaniye cinsinden belirtilir. Varsa, gecikme bir Kuralın UI Bağlamının etkinleştirilmesine veya devre dışı bırakılmasının bu zaman aralığına kadar gecikmesine neden olur. Kural gecikme aralığından önce değişirse, hiçbir şey olmaz. Bu mekanizma , zamanlayıcılara güvenmeden veya boşta bildirimler için kaydolmadan özellikle tek seferlik başlatma adımlarını "stagger" başlatma adımlarını "stagger" etmek için kullanılabilir.

 Örneğin, test yükü kuralınızı 100 milisaniye gecikmeiçin belirtebilirsiniz:

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

|Sözleşme Dönemi|Açıklama|
|-|-|
|{nnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn|GUID bir UI Bağlamı'nı ifade eder. Terim, UI Bağlamı etkin ve yanlış olduğunda geçerli olacaktır.|
|HierSingleSelectionName:\<desen>|Etkin hiyerarşideki seçim tek bir öğe olduğunda ve seçili öğenin adı "desen" tarafından verilen .Net normal ifadesiyle eşleştiğinde terim geçerli olacaktır.|
|UserSettingsStoreQuery:\<sorgu>|"sorgu", sıfır olmayan bir değere değer biçmesi gereken kullanıcı ayarları deposuna giden tam bir yolu temsil eder. Sorgu, son kesikte bir "koleksiyon" ve "propertyName" olarak ikiye ayrılır.|
|ConfigSettingsStoreQuery:\<sorgu>|"sorgu", config ayarları deposuna giden ve sıfır olmayan bir değere göre değerlendirilmesi gereken tam bir yolu temsil eder. Sorgu, son kesikte bir "koleksiyon" ve "propertyName" olarak ikiye ayrılır.|
|ActiveProjectFlavor:\<projectTypeGuid>|Terim, şu anda seçilen proje aromalı (toplu) ve verilen proje türü GUID eşleşen bir lezzet olduğunda doğru olacaktır.|
|ActiveEditorContentType:\<contentType>|Seçili belge, verilen içerik türüne sahip bir metin düzenleyicisi olduğunda terim doğru olacaktır. Not: Seçili belge nin adı yeniden adlandırıldığınızda, dosya kapatıp yeniden açılana kadar bu terim yenilenmez.|
|ActiveProjectCapability:\<İfade>|Etkin proje yetenekleri sağlanan ifadeyle eşleştiğinde terim doğrudur. Bir ifade VB &#124; CSharp gibi bir şey olabilir.|
|SolutionHasProjectCapability:\<İfade>|Yukarıdakine benzer ancak çözüm ifadeyle eşleşen yüklü bir proje olduğunda terim doğrudur.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Bir çözüm aromalı (agregalı) ve verilen proje türü GUID eşleşen bir lezzet eki olduğunda terim doğru olacaktır.|
|ProjectAddedItem:\<desen>| "Desen" ile eşleşen bir dosya açılan soluiondaki bir projeye eklendiğinde terim doğrudur.|
|ActiveProjectOutputType:\<outputType>|Terim, etkin proje çıktı türü tam olarak eşleştiğinde geçerlidir.  OutputType bir tamsayı veya bir <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> tür olabilir.|
|ActiveProjectBuildProperty:\<buildProperty\<>= regex>|Etkin proje, sağlanan regex filtresiyle belirtilen yapı özelliği ve özellik değeri eşleşince terim geçerlidir. Yapı özellikleri hakkında daha fazla bilgi için [MSBuild Project Files'daki Kalıcı Verileri](internals/persisting-data-in-the-msbuild-project-file.md) inceleyin.|
|SolutionHasProjectBuildProperty:\<buildProperty\<>= regex>|Çözüm, sağlanan regex filtresiyle belirtilen yapı özelliği ve özellik değeri eşleşen yüklü bir projeye sahipse, terim doğrudur.|

## <a name="compatibility-with-cross-version-extension"></a>Çapraz sürüm uzantısı ile uyumluluk

Kural tabanlı UI Contexts Visual Studio 2015'in yeni bir özelliğidir ve önceki sürümlere taşımaz. Önceki sürümlere taşımamak, Visual Studio'nun birden çok sürümühedefleyen uzantılarla/paketlerde sorun yaratır. Bu sürümlerin Visual Studio 2013 ve daha önce otomatik olarak yüklenmesi gerekir, ancak Visual Studio 2015'te otomatik olarak yüklenmesini önlemek için kural tabanlı UI Bağlamlarından yararlanabilir.

Bu tür paketleri desteklemek için, kayıt defterindeki AutoLoadPackages girişleri artık değer alanında, girişin Visual Studio 2015 ve üzeri nde atlanınması gerektiğini belirten bir bayrak sağlayabilir. Bu, <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>bayrak seçeneği ekleyerek yapılabilir. VSPackages artık Visual Studio 2015 ve <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> üzeri girişin göz ardı edilmesi gerektiğini belirtmek için atakları için **SkipWhenUIContextRulesActive** seçeneğini ekleyebilir.
## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI Bağlam kuralları

Bazen, paketler statik UI Bağlam kurallarını kullanamaz. Örneğin, komut durumunun içe aktarılan MEF sağlayıcıları tarafından desteklenen düzenleyici türlerini temel alacak şekilde genişletilebilirliği destekleyen bir paketiniz olduğunu varsayalım. Geçerli edit türünü destekleyen bir uzantı varsa komut etkinleştirilir. Bu gibi durumlarda, terimler kullanılabilir MEF uzantılarına bağlı olarak değişeceği için paketin kendisi statik bir Ara Bilgi Bağlamı kuralını kullanamaz.

Bu tür paketleri desteklemek için kural tabanlı UI Bağlamları, or ile birlişeceğini aşağıdaki tüm terimleri gösteren sabit kodlu bir "*" ifadesini destekler. Bu, ana paketin bilinen kural tabanlı bir Kullanıcı Arabirimi Bağlamını tanımlamasına ve komut durumunu bu içeriğe bağlamasına olanak tanır. Daha sonra ana paket için hedeflenen herhangi bir MEF uzantısı, diğer terimleri veya ana ifadeyi etkilemeden desteklediği editörler için şartlarını ekleyebilir.

Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeler, genişletilebilir Ara Birimi Bağlam kuralları için sözdizimini gösterir.
