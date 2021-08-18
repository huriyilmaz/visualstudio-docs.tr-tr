---
title: Visual Studio çalışma alanları | Microsoft Docs
description: Visual Studio çalışma alanı sağlayıcıları ve hizmetleri de dahil olmak üzere açık klasördeki dosya koleksiyonunu temsil etmek için bir çalışma alanı nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 95b2df98d3a06e4a2e2b667b8158c310a07d2c27dfe3bf33c9869ec5b138f45f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447603"
---
# <a name="workspaces"></a>Çalışma Alanları

çalışma alanı, Visual Studio [açık klasördeki](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)herhangi bir dosya koleksiyonunu temsil eder ve bu tür tarafından temsil edilir <xref:Microsoft.VisualStudio.Workspace.IWorkspace> . , Çalışma alanı, klasörü içindeki dosyalarla ilgili içeriği veya özellikleri anlamaz. Bunun yerine, Özellikler ve uzantılar için başkalarının üzerinde hareket ettikleri verileri oluşturma ve kullanma hakkında genel bir API kümesi sağlar. üreticileri, çeşitli dışarı aktarma öznitelikleri kullanılarak [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) ile oluşturulur.

## <a name="workspace-providers-and-services"></a>Çalışma alanı sağlayıcıları ve Hizmetleri

Çalışma alanı sağlayıcıları ve Hizmetleri, çalışma alanının içeriğine tepki vermek için verileri ve işlevleri sağlar. Bu kişiler bağlamsal dosya bilgileri, kaynak dosyalardaki semboller veya derleme işlevselliği sağlayabilir.

Her iki kavram de bir [fabrika kalıbı](https://en.wikipedia.org/wiki/Factory_method_pattern) kullanır ve çalışma alanı tarafından mef aracılığıyla içeri aktarılır. Tüm dışa aktarma öznitelikleri `IProviderMetadataBase` veya uygular `IWorkspaceServiceFactoryMetadata` , ancak uzantıların dışarı aktarılmış türler için kullanması gereken somut türler vardır.

Sağlayıcılar ve hizmetler arasındaki bir farklılık, çalışma alanıyla ilişkili. Bir çalışma alanı, belirli bir türden birçok sağlayıcıya sahip olabilir, ancak her çalışma alanı için yalnızca bir hizmet belirli bir türde oluşturulur. Örneğin, bir çalışma alanı birçok dosya tarayıcısı sağlayıcısına sahiptir, ancak çalışma alanı başına yalnızca bir dizin oluşturma hizmeti bulunur.

Diğer bir temel fark, sağlayıcılardan ve hizmetlerden verilerin tüketimidir. Çalışma alanı, birkaç nedenden dolayı sağlayıcılardan veri almak için giriş noktasıdır. İlk olarak, sağlayıcılar genellikle oluşturdukları bazı dar veri kümesine sahiptir. Veriler bir C# kaynak dosyası için semboller veya bir _CMakeLists.txt_ dosyası için derleme dosyası bağlamları olabilir. Çalışma alanı, bir tüketicinin meta verileri istekle hizalı olan sağlayıcılara yönelik isteğiyle eşleşir. İkinci olarak, bazı senaryolar çok sayıda sağlayıcının bir isteğe katkıda bulunmasına izin vererek diğer senaryolar sağlayıcıyı en yüksek önceliğe sahip olarak kullanır.

Buna karşılık, uzantılar örnekleri alabilir ve çalışma alanı hizmetleriyle doğrudan etkileşim kurabilir. üzerinde uzantı yöntemleri `IWorkspace` , Visual Studio tarafından sağlanan hizmetler için kullanılabilir <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Uzantınız, uzantınızın içindeki bileşenler için veya diğer uzantıların kullanması için bir çalışma alanı hizmeti sunabilir. Tüketiciler <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> , veya türünde sağladığınız bir genişletme yöntemini kullanmalıdır `IWorkspace` .

>[!WARNING]
> Visual Studio ile çakışan Hizmetleri yazmayın. Beklenmedik sorunlara yol açabilir.

## <a name="disposal-on-workspace-closure"></a>Çalışma alanı kapanışına bırakma

Bir çalışma alanının kapatılması sırasında, genişleticilerin zaman uyumsuz kodu atma, ancak çağrı yapması gerekebilir. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>Arabirim, bu kodun kolayca yazılmasını sağlamak için kullanılabilir.

## <a name="related-types"></a>İlgili türler

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> , açık bir çalışma alanı için açık bir klasör gibi merkezi varlıktır.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> oluşturulan çalışma alanı başına bir sağlayıcı oluşturur.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> oluşturulan çalışma alanı başına bir hizmet oluşturur.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> , elden çıkarma sırasında zaman uyumsuz kod çalıştırması gereken sağlayıcı ve hizmetlere uygulanmalıdır.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> iyi bilinen hizmetlere veya rastgele hizmetlere erişim için yardımcı yöntemler sağlar.

## <a name="workspace-settings"></a>Çalışma alanı ayarları

Çalışma alanları <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> , bir çalışma alanı üzerinde basit ancak güçlü denetime sahip bir hizmete sahiptir. Ayarlara temel bir genel bakış için bkz. [Yapı ve hata ayıklama görevlerini özelleştirme](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

çoğu tür için Ayarlar `SettingsType` , üzerinde _VSWorkspaceSettings.js_ ve _tasks.vs.js_ gibi _. json_ dosyalarıdır.

Çalışma alanı ayarlarının gücü, yalnızca çalışma alanı içindeki yollar olan "kapsamlar" etrafında ortalar. Bir tüketici çağırdığında <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , istenen yolu ve ayar türünü içeren tüm kapsamlar toplanır. Kapsam toplama önceliği aşağıdaki gibidir:

1. Genellikle çalışma alanı kökünün dizini olan "yerel ayarlar" `.vs` .
1. İstenen yolun kendisi.
1. İstenen yolun üst dizini.
1. Çalışma alanı kökünü içeren ve dahil diğer tüm üst dizinler.
1. Bir kullanıcı dizininde olan "Genel ayarlar".

Sonuç bir örneğidir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Bu nesne belirli bir tür için ayarları barındırır ve olarak depolanan anahtar adlarını ayarlamak için sorgulanabilir `string` . <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>Yöntemler ve <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> genişletme yöntemleri, çağıranın istenen ayar değerinin türünü bilmesini bekler. Çoğu ayar dosyası _. JSON_ dosyaları olarak kalıcı olduğundan, birçok çağırma `string` Bu türlerin,, `bool` `int` ve dizilerini kullanacaktır. Nesne türleri de desteklenir. Bu durumlarda, `IWorkspaceSettings` kendisini tür bağımsız değişkeni olarak kullanabilirsiniz. Örnek:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Bu ayarların kullanıcının _VSWorkspaceSettings.js_ olduğu varsayıldığında, verilere şu şekilde erişilebilir:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Bu ayarlar API 'Leri, ad alanında bulunan API 'Lerle ilişkili değildir `Microsoft.VisualStudio.Settings` . Çalışma alanı ayarları konağın bağımsızdır ve çalışma alanına özgü ayar dosyalarını veya dinamik ayar sağlayıcılarını kullanır.

### <a name="providing-dynamic-settings"></a>Dinamik ayarları sağlama

Uzantılar, s 'yi sağlayabilir <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . Bu bellek içi sağlayıcılar, uzantıların ayarları eklemesine veya diğerlerini geçersiz kılmasına izin verir.

Dışarı aktarma `IWorkspaceSettingsProvider` , diğer çalışma alanı sağlayıcılarından farklıdır. Fabrika değil `IWorkspaceProviderFactory` ve özel öznitelik türü yok. Bunun yerine, uygulayın <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> ve kullanın `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Döndüren yöntemleri uygularken `IWorkspaceSettingsSource` (gibi `IWorkspaceSettingsProvider.GetSingleSettings` ), yerine ' ın bir örneğini döndürün `IWorkspaceSettings` `IWorkspaceSettingsSource` . `IWorkspaceSettings` bazı ayarlar toplamaları sırasında yararlı olabilecek daha fazla bilgi sağlar.

### <a name="settings-related-apis"></a>Ayarlar ilgili apı 'ler

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> çalışma alanı için ayarları okur ve toplar.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A>`IWorkspaceSettingsManager`bir çalışma alanı için alır.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Tüm çakışan kapsamlar genelinde toplanan belirli bir kapsamın ayarlarını alır.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> belirli bir kapsamın ayarlarını içerir.

## <a name="workspace-suggested-practices"></a>Çalışma alanı önerilen uygulamalar

- `IWorkspaceProviderFactory.CreateProvider`Ya da oluşturma sırasında bağlamını hatırlayasağlayan benzer API 'lerden nesneleri döndürün `Workspace` . Bu nesnenin Oluşturulma sırasında tutulması beklenmekte olan sağlayıcı arabirimleri yazıldı.
- Çalışma alanına özgü önbellekleri veya ayarları, çalışma alanının "yerel ayarlar" yolu içinde kaydedin. `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`Visual Studio 2017 sürüm 15,6 veya sonraki sürümlerde kullanarak dosyanız için bir yol oluşturun. Sürüm 15,6 ' den önceki sürümler için aşağıdaki kod parçacığını kullanın:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Çözüm olayları ve paket otomatik yüklemesi

Yüklenen paketler uygulayabilir `IVsSolutionEvents7` ve çağırabilir `IVsSolution.AdviseSolutionEvents` . Visual Studio bir klasörü açma ve kapatma hakkında olay içerir.

Bir kullanıcı arabirimi bağlamı, paketinizi otomatik yüklemek için kullanılabilir. Bu durumda değer `4646B819-1AE0-4E79-97F4-8A8176FDD664` olur.

## <a name="troubleshooting"></a>Sorun giderme

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage paketi doğru şekilde yüklenmedi

Çalışma alanı genişletilebilirliği yoğun bir MEF tabanlıdır ve bileşim hataları, açık klasörün barındırıldığı paketin yüklenmesine neden olur. Örneğin, bir uzantı ile bir türü dışarı `ExportFileContextProviderAttribute` aktardığında ancak tür yalnızca uygularsa `IWorkspaceProviderFactory<IFileContextActionProvider>` , Visual Studio bir klasörü açmaya çalışırken bir hata oluşur.

::: moniker range="vs-2017"

Hata ayrıntıları, _%localappdata%\microsoft\visualstudio\ 15.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_ içinde bulunabilir. Uzantınızın uyguladığı türler için hataları çözün.

::: moniker-end

::: moniker range=">=vs-2019"

Hata ayrıntıları, _%localappdata%\microsoft\visualstudio\ 16.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_ içinde bulunabilir. Uzantınızın uyguladığı türler için hataları çözün.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

* [Dosya bağlamları](workspace-file-contexts.md) -dosya bağlamı sağlayıcıları, açık klasör çalışma alanları için kod zekası getirir.
* [Dizin oluşturma](workspace-indexing.md) -çalışma alanı dizin oluşturma, çalışma alanıyla ilgili bilgileri toplar ve sürdürür.
