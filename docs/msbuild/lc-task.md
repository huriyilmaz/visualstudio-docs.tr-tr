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
ms.openlocfilehash: 86525b2c4ddcf36ca85feee31f89f0003f1f9775
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590832"
---
# <a name="lc-task"></a>LC görevi
. *Licx* dosyasından bir *. License* dosyası üreten *LC. exe*' yi kaydırır. *LC. exe*hakkında daha fazla bilgi için bkz. [LC. exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `LC` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`LicenseTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> *. Lisans* dosyalarının oluşturulduğu yürütülebilir dosyayı belirtir.|
|`NoLogo`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Microsoft başlangıç başlığı görüntüsünü bastırır.|
|`OutputDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Çıkış *. Lisans* dosyalarının yerleştirileceği dizini belirtir.|
|`OutputLicense`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> *. Lisanslar* dosyasının adını belirtir. Bir ad belirtmezseniz, *. licx* dosyasının adı kullanılır ve *. lisanslar* dosyası *. licx* dosyasını içeren dizine yerleştirilir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> *. License* dosyası oluşturulurken yüklenecek olan başvurulan bileşenleri belirtir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametresi.<br /><br /> *Resgen. exe*gibi SDK araçlarının yolunu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> *. Lisanslar* dosyasına dahil edilecek lisanslı bileşenleri içeren öğeleri belirtir. Daha fazla bilgi için, [LC. exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler)içindeki `/complist` anahtarına yönelik belgelere bakın.|

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, lisansları derlemek için `LC` görevini kullanır.

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
