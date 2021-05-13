---
title: MSBuild 15 ' teki yenilikler | Microsoft Docs
description: .NET Core SDK ve Windows, macOS ve Linux 'ta .NET Core projeleri oluşturmak için kullanılabilen MSBuild 15 ' in değiştirilmiş, güncelleştirilmiş ve yeni özelliklerine bakın.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: e0fe78e781af4f2fafa52a230036bc20b657fd8e
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848272"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15 ' teki yenilikler

MSBuild artık [.NET Core SDK](https://www.microsoft.com/net/download/core) bir parçası olarak kullanılabilir ve Windows, MacOS ve Linux 'Ta .NET Core projeleri oluşturabilir.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio 'nun her bir sürümünde bir klasöre yüklenmiştir. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak Için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

 MSBuild artık genel derleme önbelleğinde yüklü değil. Programlı olarak MSBuild 'e başvurmak için NuGet paketlerini kullanın. Daha fazla bilgi için bkz. [MSBuild 15,0 için mevcut bir uygulamayı güncelleştirme](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Değiştirilen özellikler

 Yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- `MSBuildToolsVersion` araçların bu sürümü için 15,0. Derleme sürümü 15.1.0.0 ' dir.

- `MSBuildToolsPath` Artık sabit bir konuma sahip değildir. Varsayılan olarak, Visual Studio yükleme konumuna göre *Msbuild\15.0\Bin* klasöründe bulunur, ancak Visual Studio yükleme konumu yükleme sırasında değiştirilebilir.

- `ToolsVersion` değerler kayıt defterinde artık ayarlı değil.

- `SDK35ToolsPath`Ve `SDK40ToolsPath` Özellikleri, Visual Studio 'nun bu sürümüyle PAKETLENMIŞ .NET Framework SDK 'ye işaret noktasıdır (örneğin, 4. X araçları Için 10.0 a).

## <a name="updates"></a>Güncelleştirmeler

- [Proje öğesinin](../msbuild/project-element-msbuild.md) yeni bir `SDK` özniteliği vardır. Ayrıca özniteliği `Xmlns` artık isteğe bağlıdır. özniteliği hakkında daha fazla bilgi için `SDK` [bkz. MsBuild proje SDK'larını,](../msbuild/how-to-use-project-sdk.md) [Paketlerini, meta](/dotnet/core/packages) paketlerini ve çerçevelerini kullanma ve [.NET Core için csproj](/dotnet/core/tools/csproj)biçimine eklemeler.
- [Hedeflerin](../msbuild/item-element-msbuild.md) dışındaki öğe öğesi yeni bir `Update` özniteliğine sahip. Ayrıca, özniteliğiyle `Remove` ilgili kısıtlama ortadan kaldırılmış.
- *Directory.Build.props,* bir dizin altındaki projelere özelleştirmeler sağlayan kullanıcı tanımlı bir dosyadır. Özelliği false olarak ayarlanmadıkça bu dosya *Microsoft.Common.props'tan* `ImportDirectoryBuildTargets` otomatik olarak içe **aktarılır.** *Directory.Build.targets,* *Microsoft.Common.targets tarafından içe aktarılır.*
- Geçerli öznitelik listesiyle çakışmamış bir adı olan meta veriler isteğe bağlı olarak bir öznitelik olarak ifade olabilir. Daha fazla bilgi için [bkz. Öğe öğesi.](../msbuild/item-element-msbuild.md)

## <a name="new-property-functions"></a>Yeni özellik işlevleri

- `EnsureTrailingSlash` henüz yoksa yola sonda eğik çizgi ekler.
- `NormalizePath` , yol öğelerini birleştirir ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olduğunu sağlar.
- `NormalizeDirectory` yol öğelerini birleştirir, sondaki eğik çizgiyi sağlar ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olduğunu sağlar.
- `GetPathOfFileAbove` , dosyanın bu dosyadan hemen önceki yolunu döndürür. İşlevsel olarak çağrısına eşdeğerdir `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
