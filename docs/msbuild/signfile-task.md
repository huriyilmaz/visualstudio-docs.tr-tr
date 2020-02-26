---
title: SignFile görevi | Microsoft Docs
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
ms.openlocfilehash: 397366a7dac601cd11dc1c70efc352edf303a92e
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579574"
---
# <a name="signfile-task"></a>SignFile görevi

Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `SignFile` görevinin parametreleri açıklanmaktadır.

 SHA-256 sertifikalarına yalnızca .NET 4,5 ve üzeri makinelerde izin verildiğini unutmayın.

> [!WARNING]
> Visual Studio 2013 güncelleştirme 3 ' den başlayarak, bu görevin dosya için hedef Framework sürümünü belirtmenize izin veren yeni bir imzası vardır. MSBuild işlemi yalnızca hedef Framework .NET 4,5 veya üzeri olduğunda SHA-256 karmaları kullandığından, yeni imzayı mümkün olduğunda kullanmanız önerilir. Hedef çerçeve .NET 4,0 veya altındaysa, SHA-256 karması kullanılmaz.

|Parametre|Açıklama|
|---------------|-----------------|
|`CertificateThumbprint`|Gerekli `String` parametresi.<br /><br /> İmzalama için kullanılacak sertifikayı belirtir. Bu sertifika, geçerli kullanıcının kişisel deposunda olmalıdır.|
|`SigningTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Sertifikayla imzalanacak dosyaları belirtir.|
|`TimestampUrl`|İsteğe bağlı `String` parametresi.<br /><br /> Zaman damgalama sunucusunun URL 'sini belirtir.|
|`TargetFrameworkVersion`|Hedef için kullanılan .NET Framework sürümü.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev <xref:Microsoft.Build.Utilities.Task> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Certificate` özelliği tarafından belirtilen sertifikayla `FilesToSign` öğesi koleksiyonunda belirtilen dosyaları imzalamak için `SignFile` görevini kullanır.

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
> Sertifika parmak izi, sertifikanın SHA-1 karmasıdır. Daha fazla bilgi için bkz. [Güvenilen bir kök CA SERTIFIKASıNıN SHA-1 karmasını alma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Parmak izini sertifika ayrıntılarından kopyalayıp yapıştırırsanız, `SignFile` sertifikayı bulmasını engelleyebilen fazladan (3F) görünmez bir karakter dahil ettiğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)