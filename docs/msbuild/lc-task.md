---
title: LC görevi | Microsoft Docs
description: MSBuild 'in bir. licx dosyasından bir. License dosyası oluşturan LC.exe kaydırmak için LC görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 70c996d5a8d1d4bf296a395bfb64ead6eba1bb01
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903580"
---
# <a name="lc-task"></a>LC görevi

. *Licx* dosyasından bir *. license* dosyası oluşturan *LC.exe* kaydırır. *LC.exe* hakkında daha fazla bilgi için bkz. [Lc.exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `LC` .

|Parametre|Açıklama|
|---------------|-----------------|
|`LicenseTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> *. Lisans* dosyalarının oluşturulduğu yürütülebilir dosyayı belirtir.|
|`NoLogo`|İsteğe bağlı `Boolean` parametre.<br /><br /> Microsoft başlangıç başlığı görüntüsünü bastırır.|
|`OutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Çıkış *. Lisans* dosyalarının yerleştirileceği dizini belirtir.|
|`OutputLicense`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> *. Lisanslar* dosyasının adını belirtir. Bir ad belirtmezseniz, *. licx* dosyasının adı kullanılır ve *. lisanslar* dosyası *. licx* dosyasını içeren dizine yerleştirilir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> *. License* dosyası oluşturulurken yüklenecek olan başvurulan bileşenleri belirtir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> *resgen.exe* gibi SDK araçlarının yolunu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> *. Lisanslar* dosyasına dahil edilecek lisanslı bileşenleri içeren öğeleri belirtir. Daha fazla bilgi için `/complist` [Lc.exe (lisans derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler)içindeki anahtara yönelik belgelere bakın.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `LC` lisansları derlemek için görevini kullanır.

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
