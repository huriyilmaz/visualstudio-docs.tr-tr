---
title: SignFile görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08db6a5d22cacc348a9ef36fd9e9857d5b55642a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703731"
---
# <a name="signfile-task"></a>SignFile Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `SignFile` .  
  
 SHA-256 sertifikalarına yalnızca .NET 4,5 ve üzeri makinelerde izin verildiğini unutmayın.  
  
> [!WARNING]
> Visual Studio 2013 güncelleştirme 3 ' den başlayarak, bu görevin dosya için hedef Framework sürümünü belirtmenize izin veren yeni bir imzası vardır. MSBuild işlemi yalnızca hedef Framework .NET 4,5 veya üzeri olduğunda SHA-256 karmaları kullandığından, yeni imzayı mümkün olduğunda kullanmanız önerilir. Hedef çerçeve .NET 4,0 veya altındaysa, SHA-256 karması kullanılmaz.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`CertificateThumbprint`|Gerekli `String` parametre.<br /><br /> İmzalama için kullanılacak sertifikayı belirtir. Bu sertifika, geçerli kullanıcının kişisel deposunda olmalıdır.|  
|`SigningTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Sertifikayla imzalanacak dosyaları belirtir.|  
|`TimestampUrl`|İsteğe bağlı `String` parametre.<br /><br /> Zaman damgalama sunucusunun URL 'sini belirtir.|  
|`TargetFrameworkVersion`|Hedef için kullanılan .NET Framework sürümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından parametreleri devralır <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `SignFile` `FilesToSign` özelliği tarafından belirtilen sertifikayla öğe koleksiyonunda belirtilen dosyaları imzalamak için görevini kullanır `Certificate` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
> Sertifika parmak izi, sertifikanın SHA-1 karmasıdır. Daha fazla bilgi için bkz. [Güvenilen bir kök CA SERTIFIKASıNıN SHA-1 karmasını alma](https://msdn.microsoft.com/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Exec` `FilesToSign` özelliği tarafından belirtilen sertifikayla öğe koleksiyonunda belirtilen dosyaları imzalamak için görevini kullanır `Certificate` . Bunu, derleme işlemi sırasında Windows Installer dosyaları imzalamak için kullanabilirsiniz.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görevler](../msbuild/msbuild-tasks.md)
