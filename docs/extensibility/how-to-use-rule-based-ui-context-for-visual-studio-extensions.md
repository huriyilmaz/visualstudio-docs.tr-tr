---
title: 'Nasıl yapılır: Visual Studio uzantıları için kural tabanlı kullanıcı arabirimi bağlamını kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: 2abe9938d4c3212f29b8591727d731e99e47929c
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904013"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Nasıl yapılır: Visual Studio uzantıları için kural tabanlı kullanıcı arabirimi bağlamını kullanma

Visual Studio VSPackages belirli zaman yüklenmesini sağlayan iyi bilinen <xref:Microsoft.VisualStudio.Shell.UIContext>s etkinleşir. Ancak, bu UI bağlamları, uzantı yazarlarını hiçbir seçim yapmadan, ancak VSPackage 'ın yüklenmesini gerçekten istedikleri noktadan önce etkinleştiren kullanılabilir bir kullanıcı arabirimi bağlamını seçmeyen hassas değildir. İyi bilinen UI bağlamı bir listesi için bkz. <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Paketlerin yüklenmesi bir performans etkisine sahip olabilir ve bu uygulamaların gerekenden daha kısa bir şekilde yüklenmesi en iyi uygulamadır. Visual Studio 2015, uzantı yazarlarının bir UI bağlamı etkinleştirildiği ve ilişkili VSPackages 'nin yüklendiği kesin koşulları tanımlamasına imkan tanıyan bir mekanizma olan kural tabanlı UI bağlamları kavramını sunmuştur.

## <a name="rule-based-ui-context"></a>Kural tabanlı UI bağlamı

Bir "kural" Yeni kullanıcı Arabirimi bağlamında (GUID) oluşur ve bir veya daha fazla "Terms" başvuran bir Boole ifadesi mantıksal birlikte "ve", "veya", "not" işlemleri. "Terimler", çalışma zamanında dinamik olarak değerlendirilir ve koşullarından herhangi biri değiştiğinde ifade yeniden değerlendirilir. İfade doğru olarak değerlendirildiğinde, ilişkili UI bağlamı etkinleştirildi. Aksi takdirde kullanıcı Arabirimi de-activated bağlamıdır.

Kural tabanlı kullanıcı arabirimi bağlamı çeşitli yollarla kullanılabilir:

1. Görünürlük kısıtlamaları komutları ve araç pencerelerini belirtin. UI bağlamı kural karşılanana kadar bu komutları/tools windows gizleyebilirsiniz.

2. Otomatik yükleme kısıtlamaları olarak: yalnızca kural karşılandığında paketleri otomatik yükle.

3. Geciktirilen bir görev: belirtilen bir Aralık geçene ve kural hala karşılanana kadar yükleme gecikmesi.

   Mekanizması herhangi bir Visual Studio uzantısı tarafından kullanılıyor olabilir.

## <a name="create-a-rule-based-ui-context"></a>Kural tabanlı kullanıcı arabirimi bağlamı oluşturma
 Yalnızca *. config* uzantılı dosyalar için geçerli olan bir menü komutu sunan testpackage adlı bir uzantıya sahip olduğunuzu varsayalım. VS2015 önce TestPackage yüklemek için en iyi seçenek olduğu zaman <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI bağlamı etkinleştirilmediği. Bu şekilde TestPackage yüklemesi etkili değildir, çünkü yüklenen çözüm bir *. config* dosyası içeremez. Bu adımlarda, kural tabanlı kullanıcı arabirimi bağlamının yalnızca *. config* uzantılı bir dosya SEÇILDIĞINDE bir UI bağlamını etkinleştirmek ve bu kullanıcı arabirimi bağlamı etkinleştirildiğinde testpackage 'i yüklemek için nasıl kullanılabileceği gösterilmektedir.

1. Yeni bir Uıcontext GUID tanımlayın ve VSPackage sınıfa eklemek <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ve <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Örneğin, yeni bir UIContext "Uıcontextguid" ekleneceğini varsayalım. Oluşturulan GUID ( **Araçlar** oluşturmak > **GUID**' ye tıklayarak bir GUID oluşturabilirsiniz) "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Ardından, paket sınıfınızın içine aşağıdaki bildirimi eklersiniz:

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

    Bu meta veriler, yeni Uıcontext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) ve tek bir terimi, "DotConfig" başvuran bir ifade tanımlayın. Etkin hiyerarşideki geçerli seçimin "\\. config $" normal ifade düzeniyle eşleşen bir adı olduğunda "DotConfig" terimi true olarak değerlendirilir ( *. config*ile biter). Hata ayıklama için yararlı kuralı için isteğe bağlı bir ad (varsayılan) değerini tanımlar.

    Öznitelik değerleri daha sonra derleme zamanında oluşturulan pkgdef eklenir.

2. TestPackage komutları için VSCT dosyasında, uygun komutlara "DynamicVisibility" bayrağını ekleyin:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT görünürlüklerini kısmında yeni Uıcontext #1'de tanımlanan GUID için uygun komutları bağlayın:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Semboller bölümünde Uıcontext tanımını ekleyin:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Artık, *\*. config* dosyaları için bağlam menüsü komutları yalnızca Çözüm Gezgini 'ndeki seçili öğe bir *. config* dosyası olduğunda ve bu komutlardan biri seçilene kadar paket yüklenemeyecek şekilde görünür.

   Daha sonra, paketin yalnızca bunu beklediğinde yüklediğini doğrulamak için bir hata ayıklayıcı kullanın. TestPackage hata ayıklamak için:

5. Bir kesim noktası <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.

6. TestPackage oluşturun ve hata ayıklamaya başlayın.

7. Bir proje oluşturun veya açın.

8. Uzantısı *. config*dışında herhangi bir dosya seçin. Kesme noktası isabet ettirilmemelidir.

9. *App. config* dosyasını seçin.

   TestPackage yükler ve kesme noktasında durur.

## <a name="add-more-rules-for-ui-context"></a>UI bağlamı için daha fazla kural ekleyin
 UI bağlamı kuralları Boolean ifadeler olduğundan, bir kullanıcı Arabirimi içeriği için daha kısıtlı kuralları ekleyebilirsiniz. Örneğin, yukarıdaki UI bağlamında, kural yalnızca bir proje içeren bir çözüm ne zaman yüklendi geçerli olduğunu belirtebilirsiniz. Bu şekilde, bir *. config* dosyasını bir projenin parçası olarak değil tek başına bir dosya olarak açarsanız komutlar gösterilmez.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Artık üç şartları ifade başvuruyor. İlk iki terimin "SingleProject" ve "MultipleProjects" (GUID'ler tarafından) iyi bilinen diğer UI bağlamları bakın. "DotConfig" üçüncü terimi, bu makalede daha önce tanımlanan kural tabanlı kullanıcı arabirimi bağlamıdır.

## <a name="delayed-activation"></a>Gecikmeli etkinleştirme
 Kurallar, isteğe bağlı bir "gecikmesi" olabilir. Gecikme süresini milisaniye cinsinden belirtilir. Varsa, o zaman aralığına göre geciktirileceği bir kuralın UI bağlamı devre dışı bırakma ve etkinleştirme gecikme neden olur. Kural değişikliklerini önce gecikme aralığı yedeklerseniz, hiçbir şey olmaz. Bu mekanizma "başlatma adımlar - üzerinde zamanlayıcılar güvenmek veya boşta bildirimlere kaydolma olmadan özellikle tek seferlik başlatma basamaklandırmak için" kullanılabilir.

 Örneğin, 100 milisaniye gecikme için test yük kuralınızı belirtebilirsiniz:

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

Terim desteklenen çeşitli türleri şunlardır:

|Terim|Açıklama|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID, bir kullanıcı Arabirimi bağlamına başvuruyor. Terimi, UI bağlamı etkin ve false Aksi durumda olduğunda true olur.|
|HierSingleSelectionName:\<deseni >|Terim Seçimi etkin hiyerarşideki tek bir öğedir ve seçilen öğenin adı "deseni" tarafından verilen .net normal ifadeyle eşleşen olduğunda true olur.|
|UserSettingsStoreQuery:\<sorgu >|"sorgu", sıfır olmayan bir değer olarak değerlendirilmesi gereken Kullanıcı ayarları deposunun tam yolunu temsil eder. Sorgu, "koleksiyonu" ve "propertyName" en son eğik çizgi ayrılır.|
|ConfigSettingsStoreQuery:\<sorgu >|"sorgu", sıfır olmayan bir değere değerlendirilmesi gereken yapılandırma ayarları deposunun tam yolunu temsil eder. Sorgu, "koleksiyonu" ve "propertyName" en son eğik çizgi ayrılır.|
|ActiveProjectFlavor:\<projectTypeGuid >|Seçili olan projeye markdown'lar her terimi true (toplu olarak) ve GUID belirli proje türüyle eşleşen bir özellik vardır.|
|ActiveEditorContentType:\<contentType >|Seçili belgeyi belirtilen içerik türü metin düzenleyiciyle olduğunda terimi true olur. Not: Seçilen belge yeniden adlandırıldığında, Dosya kapatılıp yeniden açılıncaya kadar bu terim yenilenmez.|
|ActiveProjectCapability:\<ifadesi >|Etkin proje özellikleri, belirtilen ifadeyle eşleşiyorsa, terim true olur. Bir ifade VB &#124; CSharp gibi bir şey olabilir.|
|SolutionHasProjectCapability:\<ifadesi >|Yukarıdaki benzer; ancak terimi olduğunda true ifade ile eşleşen tüm yüklenen proje çözümü vardır.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Her bir çözüm (toplu) özellikli proje varsa ve GUID belirli proje türüyle eşleşen bir özellik terimi true olur.|
|Projectaddedıtem:\<model >| "Model" ile eşleşen bir dosya, açılan bir projede bir projeye eklendiğinde true olur.|
|ActiveProjectOutputType:\<outputType >|Etkin projenin çıkış türü tam olarak eşleştiğinde terim true olur.  OutputType bir tamsayı veya <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> türü olabilir.|
|ActiveProjectBuildProperty:\<buildProperty > =\<Regex >|Etkin proje belirtilen derleme özelliğine sahip olduğunda ve değeri, Regex filtresiyle eşleşen özellik değeri ile eşleştiğinde, bu koşul doğrudur. Derleme özellikleri hakkında daha fazla bilgi için [MSBuild proje dosyalarındaki kalıcı verilere](internals/persisting-data-in-the-msbuild-project-file.md) bakın.|
|SolutionHasProjectBuildProperty:\<buildProperty > =\<Regex >|Çözümde belirtilen derleme özelliğine sahip yüklü bir proje olduğunda ve özellik değeri, Regex filtresi ile eşleştiğinde terim true olur.|

## <a name="compatibility-with-cross-version-extension"></a>Sürümler arası uzantısı ile uyumluluk

Kural tabanlı kullanıcı arabirimi bağlamları, Visual Studio 2015 ' deki yeni bir özelliktir ve önceki sürümlere verilmez. Önceki sürümlere taşıma, Visual Studio 'nun birden çok sürümünü hedefleyen uzantılar/paketlerle ilgili bir sorun oluşturur. Bu sürümlerin Visual Studio 2013 ve önceki sürümlerde otomatik olarak yüklenmesi gerekir, ancak Visual Studio 2015 ' de otomatik olarak yüklenmesini engellemek için kural tabanlı kullanıcı arabirimi bağlamlarından faydalanabilir.

Gibi paketlerin desteklemek için AutoLoadPackages girişleri kayıt defterinde girişi Visual Studio 2015'te ve üstünde olarak atlanması gerektiğini belirtmek için değer alanında bir bayrak şimdi sağlayabilirsiniz. Bu bayrak seçeneğine ekleyerek yapılabilir <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackage artık ekleyebilirsiniz **SkipWhenUIContextRulesActive** seçeneğini kendi <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> giriş yoksayılan Visual Studio 2015'te ve yukarıdaki belirtmek için özniteliği.
## <a name="extensible-ui-context-rules"></a>Genişletilebilir UI bağlam kuralları

Bazı durumlarda, paketleri statik UI bağlamı kurallarını kullanamazsınız. Örneğin, komut durumu, içeri aktarılan MEF sağlayıcıları tarafından desteklenen Düzenleyicisi türlere göre olacak şekilde genişletilebilirlik destekleyen bir paket olduğunu varsayalım. Komut geçerli düzen türünü destekleyen bir uzantısı varsa etkindir. Bu gibi durumlarda, şartlar hangi MEF uzantılarının kullanılabilir olduğuna bağlı olarak değişecağından, paketin kendisi statik bir UI bağlamı kuralı kullanamaz.

Bu tür paketleri desteklemek için, kural tabanlı kullanıcı arabirimi bağlamları, aşağıdaki tüm koşulların veya ile birleştirildiğini gösteren "*" sabit kodlanmış ifadesini destekler. Bu, ana paketin bilinen kural tabanlı bir kullanıcı arabirimi bağlamını tanımlamasına ve komut durumunu bu bağlama bağlamasına olanak sağlar. Daha sonra ana paket için hedeflenen herhangi bir MEF uzantısına şartlarının başka koşullar veya ana ifade etkilemeden destekler düzenleyiciler için ekleyebilirsiniz.

Oluşturucu <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> belgeleri Genişletilebilir UI bağlamı kuralları sözdizimi gösterilmektedir.
