---
title: LC Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 8cea0ca4e6562ccc626bf52ad74dfa75b4f118f9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633609"
---
# <a name="lc-task"></a>LC görevi

*Bir .licx* dosyasından *bir .license* dosyası oluşturan *LC.exe'yi*sarar. *LC.exe*hakkında daha fazla bilgi için bkz: [Lc.exe (Lisans Derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görev parametreleri `LC` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`LicenseTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> *.licenses* dosyalarının oluşturulduğu yürütülebilir leri belirtir.|
|`NoLogo`|İsteğe bağlı `Boolean` parametre.<br /><br /> Microsoft başlangıç başlığı görüntüsünü bastırır.|
|`OutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Çıktı *.lisans* dosyalarının yerleştirilen dizinini belirtir.|
|`OutputLicense`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıktı parametresi.<br /><br /> *.licenses* dosyasının adını belirtir. Bir ad belirtmezseniz, *.licx* dosyasının adı kullanılır ve *.licenses* dosyası *.licx* dosyasını içeren dizine yerleştirilir.|
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> *.license* dosyasını oluştururken yüklenmesi için başvurulan bileşenleri belirtir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> *Resgen.exe*gibi SDK araçlarına giden yolu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Lisanslı bileşenler içeren maddeleri *.licenses* dosyasına eklemek üzere belirtir. Daha fazla bilgi için `/complist` [Lc.exe (Lisans Derleyicisi)](/dotnet/framework/tools/lc-exe-license-compiler)adresindeki anahtar için belgelere bakın.|

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `LC` lisansları derlemek için görevi kullanır.

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
