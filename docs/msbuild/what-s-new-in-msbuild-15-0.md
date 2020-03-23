---
title: MSBuild 15'te&#39;Yeni | Microsoft Dokümanlar
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 2503040e074a62422d4c7c904f5ad3a2bd84d6c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631035"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15'teki yenilikler

MSBuild artık [.NET Core SDK'nın](https://www.microsoft.com/net/download/core) bir parçası olarak kullanılabilir ve Windows, macOS ve Linux'ta .NET Core projeleri oluşturabilir.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild artık Visual Studio'nun her sürümü altında bir klasöre yüklenmiş durumda. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Ayrıca MSBuild bulmak için aşağıdaki PowerShell modüllerini kullanabilirsiniz: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild artık Genel Montaj Önbelleğinde yüklü değildir. MSBuild'e programlı olarak başvurmak için NuGet paketlerini kullanın. Daha fazla bilgi [için, MSBuild 15.0 için varolan bir uygulamayı güncelleştirme](../msbuild/updating-an-existing-application.md)ye bakın.

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild özellikleri yeni sürüm numarası nedeniyle güncelleştirildi.

- `MSBuildToolsVersion`araçların bu sürümü için 15.0 olduğunu. Derleme sürümü 15.1.0.0'dır.

- `MSBuildToolsPath`artık sabit bir konuma sahip değildir. Varsayılan olarak, Visual Studio yükleme konumuna göre *MSBuild\15.0\Bin* klasöründe bulunur, ancak Visual Studio yükleme konumu yükleme sırasında değiştirilebilir.

- `ToolsVersion`değerler artık kayıt defterinde ayarlı değildir.

- Ve `SDK35ToolsPath` `SDK40ToolsPath` özellikleri Visual Studio bu sürümü ile paketlenmiş .NET Framework SDK işaret (örneğin, 4.X araçları için 10.0A).

## <a name="updates"></a>Güncelleştirmeler

- [Proje öğesi](../msbuild/project-element-msbuild.md) nin `SDK` yeni bir özniteliği vardır. `Xmlns` Ayrıca öznitelik artık isteğe bağlıdır. `SDK` Öznitelik hakkında daha fazla bilgi için [bkz: MSBuild proje SDK'larını, Paketlerini,](../msbuild/how-to-use-project-sdk.md) [meta paketlerini ve çerçeveleri](/dotnet/core/packages) ve [.NET Core için csproj formatına eklemeleri](/dotnet/core/tools/csproj)kullanın.
- Hedef dışındaki [öğe öğesinin](../msbuild/item-element-msbuild.md) yeni `Update` bir özniteliği vardır. Ayrıca, öznitelik `Remove` üzerindeki kısıtlama ortadan kaldırılmış.
- *Directory.Build.props,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır. Özellik **yanlış**olarak ayarlmadığı sürece `ImportDirectoryBuildTargets` bu dosya *Microsoft.Common.props'tan* otomatik olarak alınır. *Directory.Build.targets* *Microsoft.Common.targets*tarafından aktarılır.
- Geçerli öznitelik listesiyle çakışmayan bir ada sahip herhangi bir meta veri isteğe bağlı olarak bir öznitelik olarak ifade edilebilir. Daha fazla bilgi için [Öğe öğesine](../msbuild/item-element-msbuild.md)bakın.

## <a name="new-property-functions"></a>Yeni özellik işlevleri

- `EnsureTrailingSlash`zaten yoksa, bir yola bir çizgi ekler.
- `NormalizePath`yol öğelerini birleştirir ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `NormalizeDirectory`yol öğelerini birleştirir, bir çizgi yitirmesini sağlar ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `GetPathOfFileAbove`dosyanın yolunu hemen bundan önce döndürür. İşlevsel olarak aramaya eşdeğerdir`<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)
