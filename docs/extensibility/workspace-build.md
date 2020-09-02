---
title: Visual Studio 'da çalışma alanı derlemesi | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553334"
---
# <a name="workspace-build"></a>Çalışma alanı derlemesi

[Açık klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) senaryolarında derleme desteği, [çalışma alanı](workspaces.md)için [dizinli](workspace-indexing.md) ve [Dosya bağlamı](workspace-file-contexts.md) verilerinin yanı sıra çalıştırılacak derleme eyleminin sağlaması için bir genişletici gerektirir.

Uzantınızın ihtiyacı olacak bir ana hat aşağıda verilmiştir.

## <a name="build-file-context"></a>Derleme dosya bağlamı

- Sağlayıcı fabrikası
  - `ExportFileContextProviderAttribute``supportedContextTypeGuids`tüm geçerli sabitleri olan özniteliği `string``BuildContextTypes`
  - Uygular `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dosya bağlamı sağlayıcısı
    - `FileContext`Her derleme işlemi için bir döndür ve desteklenen yapılandırma
      - `contextType` Kaynak <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` , <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> `Configuration` yapı yapılandırması olarak özelliği ile uygular (örneğin,, `"Debug|x86"` `"ret"` veya `null` geçerli değilse). Alternatif olarak, bir örneğini kullanın <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> . Yapılandırma değeri, dizinli dosya veri değeri **yapılandırmasıyla eşleşmelidir.**

## <a name="indexed-build-file-data-value"></a>Dizinli derleme dosyası veri değeri

- Sağlayıcı fabrikası
  - `ExportFileScannerAttribute``IReadOnlyCollection<FileDataValue>`desteklenen tür olarak özniteliği
  - Uygular `IWorkspaceProviderFactory<IFileScanner>`
- Dosya tarayıcısı açık `ScanContentAsync<T>`
  - `FileScannerTypeConstants.FileDataValuesType`Tür bağımsız değişkeni olduğunda verileri döndürür
  - İle oluşturulan her yapılandırma için bir dosya veri değeri döndürür:
    - `type` gerektiği `BuildConfigurationContext.ContextTypeGuid`
    - `context` derleme yapılandırmanız (örneğin, `"Debug|x86"` `"ret"` veya `null` yoksa) olarak. Bu değer, dosya bağlamındaki **yapılandırmayla eşleşmelidir.**

## <a name="build-file-context-action"></a>Derleme dosya bağlamı eylemi

- Sağlayıcı fabrikası
  - `ExportFileContextActionProvider``supportedContextTypeGuids`tüm geçerli sabitleri olan özniteliği `string``BuildContextTypes`
  - Uygular `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Eylem sağlayıcısı açık `IFileContextActionProvider.GetActionsAsync`
  - `IFileContextAction`Verilen değerle eşleşen bir değer döndürür `FileContext.ContextType`
- Dosya bağlamı eylemi
  - `IFileContextAction`Ve uygular<xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Özellik dönüşleri `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId``0x1000`derleme, `0x1010` yeniden oluşturma veya `0x1020` Temizleme için

>[!NOTE]
>`FileDataValue`Dizin oluşturulması gerektiğinden, çalışma alanının açılması ve dosyanın tam yapı işlevselliği için tarandığı nokta arasında bir süre olacaktır. Daha önce önbelleğe alınmış bir dizin olmadığından, gecikme bir klasörün ilk açılışından görünür.

## <a name="reporting-messages-from-a-build"></a>Bir derlemeden rapor iletileri

Yapı, kullanıcılara iki şekilde bilgi, uyarı ve hata iletileri yüzeysel olabilir. Basit yolu, <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> ve gibi bir sağlamak için <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> ' yi kullanmaktır:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` ve `BuildMessage.LogMessage` bilgilerin kullanıcıya sunulma davranışını kontrol edin. Dışında herhangi bir `BuildMessage.TaskType` değer `None` , verilen ayrıntılara sahip bir **hata listesi** girişi üretir. `LogMessage`**çıktı** araç penceresinin **Build** bölmesinde her zaman çıkış olur.

Alternatif olarak, uzantılar **hata listesi** veya **Yapı** bölmesiyle doğrudan etkileşime geçebilir. Visual Studio 2017 sürüm 15,7 ' den önceki sürümlerde, `pszProjectUniqueName` bağımsız değişkeninin <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> yok sayıldığı bir hata var.

>[!WARNING]
>' De çağıranlar `IFileContextAction.ExecuteAsync` bağımsız değişken için rastgele temel uygulamalar sağlayabilir `IProgress<IFileContextActionProgressUpdate>` . Hiçbir şekilde `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` doğrudan çağırmayın. Şu anda bu bağımsız değişkeni kullanmaya yönelik genel bir kılavuz yoktur, ancak bu yönergeler değişebilir.

## <a name="build-related-apis"></a>Derleme ilgili API 'Leri

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> derleme yapılandırma ayrıntılarını sağlar.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService><xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>kullanıcıları gösterir.

## <a name="tasksvsjson-and-launchvsjson"></a>Üzerinde tasks.vs.jsve launch.vs.js

Dosya launch.vs.jsüzerinde tasks.vs.jsyazma hakkında bilgi için, bkz. [Yapı ve hata ayıklama görevlerini özelleştirme](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Sonraki adımlar

* [Dil sunucusu protokolü](language-server-protocol.md) -dil sunucularını Visual Studio ile tümleştirmeyi öğrenin.