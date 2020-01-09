---
title: "&#39;MSBuild 15 ' te yenilikler | Microsoft Docs"
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 49e248ee0e5537ae54957695ca698b041fc1ce8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567286"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15 ' teki yenilikler

MSBuild artık [.NET Core SDK](https://www.microsoft.com/net/download/core) bir parçası olarak kullanılabilir ve Windows, MacOS ve Linux 'Ta .NET Core projeleri oluşturabilir.

## <a name="changed-path"></a>Değiştirilen yol

 MSBuild, Visual Studio 'nun her bir sürümünde bir klasöre yüklenmiştir. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell)' i bulmak Için aşağıdaki PowerShell modülünü de kullanabilirsiniz.

 MSBuild artık genel derleme önbelleğinde yüklü değil. Programlı olarak MSBuild 'e başvurmak için NuGet paketlerini kullanın. Daha fazla bilgi için bkz. [MSBuild 15,0 için mevcut bir uygulamayı güncelleştirme](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Değiştirilen özellikler

 Yeni sürüm numarası nedeniyle aşağıdaki MSBuild özellikleri güncelleştirildi.

- araçların bu sürümü için `MSBuildToolsVersion` 15,0 ' dir. Derleme sürümü 15.1.0.0 ' dir.

- `MSBuildToolsPath` artık sabit bir konuma sahip değil. Varsayılan olarak, Visual Studio yükleme konumuna göre *Msbuild\15.0\Bin* klasöründe bulunur, ancak Visual Studio yükleme konumu yükleme sırasında değiştirilebilir.

- `ToolsVersion` değerleri artık kayıt defterinde ayarlı değil.

- `SDK35ToolsPath` ve `SDK40ToolsPath` özellikleri, Visual Studio 'nun bu sürümüyle paketlenmiş .NET Framework SDK 'ya işaret noktasıdır (örneğin, 4. X araçları için 10.0 A).

## <a name="updates"></a>Güncelleştirmeler
- [Proje öğesinin](../msbuild/project-element-msbuild.md) yeni bir `SDK` özniteliği vardır. Ayrıca `Xmlns` özniteliği artık isteğe bağlıdır. `SDK` özniteliği hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild proje SDK](../msbuild/how-to-use-project-sdk.md)'larını, [paketleri, metapaketleri ve çerçeveleri](/dotnet/core/packages) ve [eklemeleri .NET Core için csproj biçiminde](/dotnet/core/tools/csproj)kullanma.
- Hedeflerin dışında [öğe öğesi](../msbuild/item-element-msbuild.md) yeni bir `Update` özniteliğine sahiptir. Ayrıca, `Remove` özniteliği üzerinde kısıtlama ortadan kaldırılmıştır.
- *Directory. Build. props* , bir dizin altındaki projelere özelleştirmeler sağlayan Kullanıcı tanımlı bir dosyadır. Özellik `ImportDirectoryBuildTargets` **false**olarak ayarlanmadığı takdirde bu dosya *Microsoft. Common. props* öğesinden otomatik olarak içeri aktarılır. *Directory. Build. targets* , *Microsoft. Common. targets*tarafından içeri aktarılır.
- Geçerli öznitelik listesiyle çakışmayan bir ada sahip tüm meta veriler, isteğe bağlı olarak bir öznitelik olarak ifade edilebilir. Daha fazla bilgi için bkz. [öğe öğesi](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Yeni özellik işlevleri

- `EnsureTrailingSlash`, bir yol zaten yoksa bir yola sonuna eğik çizgi ekler.
- `NormalizePath`, yol öğelerini birleştirir ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `NormalizeDirectory` yol öğelerini birleştirir, sonunda eğik çizgi sağlar ve çıkış dizesinin geçerli işletim sistemi için doğru dizin ayırıcı karakterlerine sahip olmasını sağlar.
- `GetPathOfFileAbove` dosyanın yolunu hemen önceki bir şekilde döndürür. Arama için işlevsel olarak eşdeğerdir `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild](../msbuild/msbuild.md)
