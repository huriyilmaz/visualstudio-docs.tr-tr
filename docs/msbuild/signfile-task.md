---
title: SignFile görevi | Microsoft Docs
description: MSBuild 'in belirtilen sertifikayı kullanarak belirtilen dosyayı imzalamak için SignFile görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41fc320034ef5ea86006abf6f19079e8b0a45a82
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048290"
---
# <a name="signfile-task"></a>SignFile görevi

Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `SignFile` .

 SHA-256 sertifikalarına yalnızca .NET 4,5 ve üzeri makinelerde izin verildiğini unutmayın.

> [!WARNING]
> Visual Studio 2013 güncelleştirme 3 ' den başlayarak, bu görevin dosya için hedef Framework sürümünü belirtmenize izin veren yeni bir imzası vardır. MSBuild işlemi yalnızca hedef Framework .NET 4,5 veya üzeri olduğunda SHA-256 karmaları kullandığından, yeni imzayı mümkün olduğunda kullanmanız önerilir. Hedef çerçeve .NET 4,0 veya altındaysa, SHA-256 karması kullanılmaz.

|Parametre|Açıklama|
|---------------|-----------------|
|`CertificateThumbprint`|Gerekli `String` parametre.<br /><br /> İmzalama için kullanılacak sertifikayı belirtir. Bu sertifika, geçerli kullanıcının kişisel deposunda olmalıdır.|
|`SigningTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> . Exe veya. dll ' nin sertifikasıyla imzalanacak dosyaları belirtir.|
|`TimestampUrl`|İsteğe bağlı `String` parametre.<br /><br /> Zaman damgalama sunucusunun URL 'sini belirtir.|
|`TargetFrameworkVersion`|Hedef için kullanılan .NET Framework sürümü.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından parametreleri devralır <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `SignFile` `FilesToSign` özelliği tarafından belirtilen sertifikayla öğe koleksiyonunda belirtilen dosyaları imzalamak için görevini kullanır `CertificateThumbprint` .

```xml
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
> Sertifika parmak izi, sertifikanın SHA-1 karmasıdır. Daha fazla bilgi için bkz. [Güvenilen bir kök CA SERTIFIKASıNıN SHA-1 karmasını alma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Parmak izini sertifika ayrıntılarından kopyalayıp yapıştırırsanız, sertifikayı bulmayı engelleyebilen fazladan (3F) görünmez bir karakter dahil ettiğinizden emin olun `SignFile` .

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)