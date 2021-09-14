---
title: 15 MSBuild'daki | Microsoft Docs
description: .NET Core SDK, macOS ve Linux'ta .NET Windows Core projeleri oluşturmak için kullanılabilen MSBuild 15'in değiştirilmiş, güncelleştirilmiş ve yeni özelliklerine bakın.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: bcf84506f44e6aab30e0d5ce10e19f05a4a87c09
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726850"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15'MSBuild

MSBuild artık .NET Core SDK kapsamında kullanılabilir [ve Windows,](https://www.microsoft.com/net/download/core) macOS ve Linux'ta .NET Core projeleri derlemeye devam ediyor.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild artık her bir sürüm altındaki bir klasöre Visual Studio. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. Aşağıdaki PowerShell modülünü kullanarak da MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild artık Genel Derleme Önbelleği'nde yüklü değil. Program aracılığıyla MSBuild için NuGet kullanın. Daha fazla bilgi için [bkz. MSBuild 15.0 için mevcut bir uygulamayı güncelleştirme.](../msbuild/updating-an-existing-application.md)

## <a name="changed-properties"></a>Değiştirilen özellikler

 Aşağıdaki MSBuild sürüm numarası nedeniyle güncelleştirilmiştir.

- `MSBuildToolsVersion` araçların bu sürümü için 15.0'dır. Derleme sürümü 15.1.0.0'dır.

- `MSBuildToolsPath` artık sabit bir konuma sahip değil. Varsayılan olarak, *MSBuild\15.0\Bin* klasöründe, Visual Studio yükleme konumunda bulunur, ancak Visual Studio yükleme konumu yükleme zamanında değiştirilebilir.

- `ToolsVersion` değerleri artık kayıt defterinde ayar değil.

- ve `SDK35ToolsPath` `SDK40ToolsPath` özellikleri, Visual Studio (örneğin, 4.X araçları için 10.0A) ile paketlenmiş .NET Framework SDK'sı'nın işaret ediyor.

## <a name="updates"></a>Güncelleştirmeler

- [Project yeni](../msbuild/project-element-msbuild.md) bir özniteliği `SDK` var. Ayrıca özniteliği `Xmlns` artık isteğe bağlıdır. özniteliği hakkında daha fazla bilgi için bkz. .NET Core MSBuild csproj biçimine eklemeler, paketler, meta paketler ve çerçeveler için MSBuild proje `SDK` [SDK'larını](../msbuild/how-to-use-project-sdk.md) [kullanma.](/dotnet/core/tools/csproj) [](/dotnet/core/packages)
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
