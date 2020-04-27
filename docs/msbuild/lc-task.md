---
title: LC görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865167b9182ca1f2264900a3e71ddeb4983e25ef
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167403"
---
# <a name="lc-task"></a>LC görevi

. *Licx* dosyasından bir *. License* dosyası üreten *LC. exe*' yi kaydırır. *LC. exe*hakkında daha fazla bilgi için bkz. [LC. exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, `LC` görevi için parametreler açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`LicenseTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> *. Lisans* dosyalarının oluşturulduğu yürütülebilir dosyayı belirtir.|
|`NoLogo`|İsteğe `Boolean` bağlı parametre.<br /><br /> Microsoft başlangıç başlığı görüntüsünü bastırır.|
|`OutputDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Çıkış *. Lisans* dosyalarının yerleştirileceği dizini belirtir.|
|`OutputLicense`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı çıkış parametresi.<br /><br /> *. Lisanslar* dosyasının adını belirtir. Bir ad belirtmezseniz, *. licx* dosyasının adı kullanılır ve *. lisanslar* dosyası *. licx* dosyasını içeren dizine yerleştirilir.|
|`ReferencedAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> *. License* dosyası oluşturulurken yüklenecek olan başvurulan bileşenleri belirtir.|
|`SdkToolsPath`|İsteğe `String` bağlı parametre.<br /><br /> *Resgen. exe*gibi SDK araçlarının yolunu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> *. Lisanslar* dosyasına dahil edilecek lisanslı bileşenleri içeren öğeleri belirtir. Daha fazla bilgi için, `/complist` [LC. exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler)içindeki anahtara yönelik belgelere bakın.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, lisansları derlemek `LC` için görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
