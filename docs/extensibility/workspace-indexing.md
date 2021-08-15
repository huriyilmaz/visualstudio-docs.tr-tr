---
title: Visual Studio |'de çalışma alanı dizini oluşturma Microsoft Docs
description: Açık Klasör çalışma alanı için zengin IDE özelliklerini desteklemek için verilerin toplanması ve kalıcı olarak depolanması olan çalışma alanı dizini oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 57342120ccd8a2305bad83eb237e41b28065a102919d8a99dee0dd827aff58cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234232"
---
# <a name="workspace-indexing"></a>Çalışma alanı dizini oluşturma

Bir çözümde proje sistemleri derleme, hata ayıklama, **GoTo** sembol arama ve daha fazlası için işlevsellik sağlamaktan sorumludur. Project sistemleri proje içindeki dosyaların ilişkisini ve özelliklerini anları için bu işi yapabiliriz. Klasör [Aç çalışma](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) alanının zengin IDE özellikleri sağlamak için de aynı içgörüye sahip olması gerekir. Bu verilerin toplanması ve kalıcı olarak depolanması, çalışma alanı dizini oluşturma olarak adlandırılan bir işlemdir. Dizine bu veriler bir dizi zaman uyumsuz API aracılığıyla sorgu olabilir. Genişleticiler, belirli dosya türlerini işlemeyi biliyor olan s sağlayarak <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> dizin oluşturma sürecine katılabilir.

## <a name="types-of-indexed-data"></a>Dizine veri türleri

Dizine üç tür veri vardır. Dosya tarayıcılarından beklenen türün dizinden kaldırılan türden farklı olduğunu unutmayın.

|Veriler|Dosya tarayıcı türü|Dizin sorgusu sonuç türü|İlgili türler|
|--|--|--|--|
|Başvurular|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simgeleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> sorgular için yerine `IIndexWorkspaceService` kullanılmalıdır|
|Veri değerleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Dizine veri sorgulama

Kalıcı verilere erişmek için kullanılabilen iki zaman uyumsuz tür vardır. İlki <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> aracılığıyladır. Tek bir dosyanın ve verilere temel erişim `FileReferenceResult` `FileDataResult` sağlar ve sonuçları önbelleğe verir. İkincisi, <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> önbelleğe almayı kullanmayan ancak daha fazla sorgulama özelliğine olanak sağlayan özelliğidir.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Dizin oluşturmaya katılma

Çalışma alanı dizini oluşturma kabaca aşağıdaki sırayı izler:

1. Çalışma alanında dosya sistemi varlıklarını bulma ve kalıcılık (yalnızca ilk açma taramalarında).
1. Dosya başına, en yüksek önceliğe sahip eşleşen sağlayıcıdan s taraması `FileReferenceInfo` istenmektedir.
1. Dosya başına, en yüksek önceliğe sahip eşleşen sağlayıcıdan s taraması `SymbolDefinition` istenmektedir.
1. Dosya başına tüm sağlayıcılardan s `FileDataValue` istenmektedir.

Uzantılar ile türü uygulayarak ve `IWorkspaceProviderFactory<IFileScanner>` dışarı aktararak bir tarayıcıyı dışarı aktar <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> olabilir. öznitelik `SupportedTypes` bağımsız değişkeni, bir veya daha fazla değerine sahip <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> olmalı. Örnek bir tarayıcı için VS SDK örneğine [bakın.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)

> [!WARNING]
> Türünü destekleyen bir dosya tarayıcısını dışarı `FileScannerTypeConstants.FileScannerContentType` aktarın. Yalnızca Microsoft iç amaçları için kullanılır.

Gelişmiş durumlarda, uzantı rastgele bir dosya türleri kümesine dinamik olarak destek olabilir. DıŞARı MEF dışarı aktarma yerine `IWorkspaceProviderFactory<IFileScanner>` bir uzantı dışarı `IWorkspaceProviderFactory<IFileScannerProvider>` aktarabilirsiniz. Dizin oluşturma başladığında, bu fabrika türü içe aktarılır, örnek alınır ve yöntemi <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> çağrılır. `IFileScanner` yalnızca semboller değil, herhangi bir değeri `FileScannerTpeConstants` destekleyen örnekler de kabul olur.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanları ve dil hizmetleri](workspace-language-services.md) - Dil hizmetlerini Açık Klasör çalışma alanıyla nasıl tümleştirebilirsiniz?
* [Çalışma alanı derlemesi](workspace-build.md) - Klasör Aç, dosya oluşturma MSBuild derleme sistemlerini destekler.