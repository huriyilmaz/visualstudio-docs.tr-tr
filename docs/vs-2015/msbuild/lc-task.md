---
title: LC görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bbc6463247142ecde20fb2d054d9bd59304c4ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694108"
---
# <a name="lc-task"></a>LC Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

. Licx dosyasından bir. License dosyası oluşturan LC.exe kaydırır. LC.exe hakkında daha fazla bilgi için bkz. [Lc.exe (lisans derleyicisi)](https://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `LC` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`LicenseTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> . Lisans dosyalarının oluşturulduğu yürütülebilir dosyayı belirtir.|  
|`NoLogo`|İsteğe bağlı `Boolean` parametre.<br /><br /> Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|`OutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Çıkış. lisans dosyalarının yerleştirileceği dizini belirtir.|  
|`OutputLicense`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> . Lisanslar dosyasının adını belirtir. Bir ad belirtmezseniz,. licx dosyasının adı kullanılır ve. lisanslar dosyası. licx dosyasını içeren dizine yerleştirilir.|  
|`ReferencedAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> . License dosyası oluşturulurken yüklenecek olan başvurulan bileşenleri belirtir.|  
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> resgen.exe gibi SDK araçlarının yolunu belirtir.|  
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> . Lisanslar dosyasına dahil edilecek lisanslı bileşenleri içeren öğeleri belirtir. Daha fazla bilgi için `/complist` [Lc.exe (lisans derleyicisi)](https://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460)içindeki anahtara yönelik belgelere bakın.|  
  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `LC` lisansları derlemek için görevini kullanır.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
