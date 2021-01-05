---
title: Visual Studio 'da çalışma alanı dizini oluşturma | Microsoft Docs
description: Açık klasör çalışma alanı için zengin IDE özelliklerini desteklemeye yönelik verilerin toplanması ve kalıcı depolanması olan çalışma alanı dizin oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877058"
---
# <a name="workspace-indexing"></a>Çalışma alanı dizini oluşturma

Bir çözümde, proje sistemleri derleme, hata ayıklama, simge aramaya **Git** ve daha fazlası için işlevsellik sağlamaktan sorumludur. Proje sistemleri, bir proje içindeki dosyaların ilişkilerini ve yeteneklerini anladıkları için bu işi gerçekleştirebilir. [Açık bir klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) çalışma alanı, zengin IDE özellikleri de sağlamaya yönelik aynı öngörüye ihtiyaç duyuyor. Bu verilerin toplanması ve kalıcı depolanması, çalışma alanı dizin oluşturma adlı bir işlemdir. Bu dizine alınmış veriler, bir dizi zaman uyumsuz API 'Ler aracılığıyla sorgulanabilir. Extender 'lar, <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> bazı dosya türlerini nasıl işleyeceğinizi belirten s sağlayarak dizin oluşturma işlemine katılabilir.

## <a name="types-of-indexed-data"></a>Dizinli veri türleri

Dizine eklenen üç tür veri vardır. Dosya tarayıcılarından beklenen türün dizinden Serisi kaldırılan türden farklı olduğunu aklınızda yazın.

|Veriler|Dosya tarayıcı türü|Dizin sorgusu sonuç türü|İlgili türler|
|--|--|--|--|
|Başvurular|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simgeleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService>sorgular yerine kullanılmalıdır `IIndexWorkspaceService`|
|Veri değerleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Dizinli verileri sorgulama

Kalıcı verilere erişmek için kullanılabilecek iki zaman uyumsuz tür vardır. Birincisi <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Tek bir dosyanın ve verilerin temel erişimini sağlar `FileReferenceResult` `FileDataResult` ve sonuçları önbelleğe alır. İkincisi, <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> önbelleğe alma özelliğini kullanmaz, ancak daha fazla sorgulama özelliğine izin verir.

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

## <a name="participating-in-indexing"></a>Dizine katılma

Çalışma alanı dizin oluşturma kabaca aşağıdaki sırayı izler:

1. Dosya sistemi varlıklarının çalışma alanında bulunması ve kalıcı hale getirme (yalnızca ilk açılış taramasında).
1. Dosya başına, en yüksek önceliğe sahip eşleşen sağlayıcının s taraması istenir `FileReferenceInfo` .
1. Dosya başına, en yüksek önceliğe sahip eşleşen sağlayıcının s taraması istenir `SymbolDefinition` .
1. Her dosya için tüm sağlayıcılara sorulur `FileDataValue` .

Uzantılar `IWorkspaceProviderFactory<IFileScanner>` , ile türü uygulayarak ve dışarı aktararak bir tarayıcı dışarı aktarabilir <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`Öznitelik bağımsız değişkeni, öğesinden bir veya daha fazla değer olmalıdır <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Örnek bir tarayıcı için bkz. VS SDK [örneği](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Türü destekleyen bir dosya tarayıcısını dışarı aktarmayın `FileScannerTypeConstants.FileScannerContentType` . Yalnızca Microsoft iç amaçları için kullanılır.

Gelişmiş durumlarda, bir uzantı rastgele bir dosya türleri kümesini dinamik olarak destekleyebilir. MEF dışarı aktarma yerine `IWorkspaceProviderFactory<IFileScanner>` , bir uzantı dışarı aktarabilir `IWorkspaceProviderFactory<IFileScannerProvider>` . Dizin oluşturma başladığında, bu fabrika türü içeri aktarılır, örneklenmiştir ve <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> yönteminin çağrılması gerekir. `IFileScanner` Bunlardan herhangi bir değeri destekleyen örnekler `FileScannerTpeConstants` yalnızca semboller değil, kabul edilir.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanları ve dil Hizmetleri](workspace-language-services.md) -dil hizmetlerini bir açık klasör çalışma alanıyla tümleştirmeyi öğrenin.
* [Çalışma alanı derlemesi](workspace-build.md) -aç klasörü MSBuild ve makefiles gibi derleme sistemlerini destekler.