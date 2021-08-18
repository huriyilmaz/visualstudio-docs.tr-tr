---
title: MSBuild 15 sürümündeki yenilikler | Microsoft Docs
description: .NET Core SDK için sunulan ve Windows, macos ve Linux 'ta .net Core projeleri oluşturmak için MSBuild 15 ' in değiştirilmiş, güncelleştirilmiş ve yeni özelliklerine bakın.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132034"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15 sürümündeki yenilikler

MSBuild artık [.NET Core SDK](https://www.microsoft.com/net/download/core) bir parçası olarak kullanılabilir ve Windows, macos ve Linux 'ta .net Core projeleri oluşturabilir.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio her bir sürümünde bir klasöre yüklenmiştir. örneğin, *C:\Program Files (x86) \ Microsoft Visual Studio \ 2017 \ Enterprise \ MSBuild*. MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

 MSBuild artık genel derleme önbelleğinde yüklü değil. programlı olarak MSBuild başvurmak için NuGet paketlerini kullanın. daha fazla bilgi için bkz. [MSBuild 15,0 için mevcut bir uygulamayı güncelleştirme](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Değiştirilen özellikler

 yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- `MSBuildToolsVersion` araçların bu sürümü için 15,0. Derleme sürümü 15.1.0.0 ' dir.

- `MSBuildToolsPath` Artık sabit bir konuma sahip değildir. varsayılan olarak, Visual Studio yükleme konumuna göre *MSBuild \15.0\bin* klasöründe bulunur, ancak Visual Studio yükleme konumu yükleme sırasında değiştirilebilir.

- `ToolsVersion` değerler kayıt defterinde artık ayarlı değil.

- `SDK35ToolsPath`ve `SDK40ToolsPath` özellikleri, bu Visual Studio (örneğin, 4. X araçları için 10.0 a) ile paketlenmiş .NET Framework SDK 'ye işaret noktasıdır.

## <a name="updates"></a>Güncelleştirmeler

- [Project öğesinin](../msbuild/project-element-msbuild.md) yeni bir `SDK` özniteliği vardır. Ayrıca, `Xmlns` özniteliği artık isteğe bağlıdır. özniteliği hakkında daha fazla bilgi için `SDK` bkz. [nasıl yapılır: MSBuild projesi sdk](../msbuild/how-to-use-project-sdk.md)'larını, [paketleri, metapaketleri ve çerçeveleri](/dotnet/core/packages) ve [eklemeleri .net Core için csproj biçiminde](/dotnet/core/tools/csproj)kullanma.
- Hedeflerin dışında [öğe öğesi](../msbuild/item-element-msbuild.md) yeni bir `Update` özniteliğe sahiptir. Ayrıca, öznitelik üzerindeki kısıtlama `Remove` ortadan kaldırılmıştır.
- *Directory. Build. props* , bir dizin altındaki projelere özelleştirmeler sağlayan Kullanıcı tanımlı bir dosyadır. Bu dosya, özelliği false olarak ayarlanmadığı takdirde *Microsoft. Common. props* öğesinden otomatik olarak içeri aktarılır `ImportDirectoryBuildTargets` .  *Directory. Build. targets* , *Microsoft. Common. targets* tarafından içeri aktarılır.
- Geçerli öznitelik listesiyle çakışmayan bir ada sahip tüm meta veriler, isteğe bağlı olarak bir öznitelik olarak ifade edilebilir. Daha fazla bilgi için bkz. [öğe öğesi](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Yeni özellik işlevleri

- `EnsureTrailingSlash` bir yol yoksa bir yola sondaki eğik çizgi ekler.
- `NormalizePath` yol öğelerini birleştirir ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `NormalizeDirectory` yol öğelerini birleştirir, sonunda eğik çizgi sağlar ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `GetPathOfFileAbove` dosyanın yolunu hemen önceki bir şekilde döndürür. Çağırmak için işlevsel olarak eşdeğerdir `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
