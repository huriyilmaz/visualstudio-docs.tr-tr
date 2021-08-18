---
title: SignFile Görev | Microsoft Docs
description: Belirtilen MSBuild imzalamak için SignFile görevini nasıl kullandığını öğrenin.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d65187b74dc17c9211a6b3ac8b750606c1c4ae3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136644"
---
# <a name="signfile-task"></a>SignFile görevi

Belirtilen sertifikayı kullanarak belirtilen dosyayı imzalar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `SignFile` almaktadır.

 SHA-256 sertifikalarına yalnızca .NET 4.5 ve üzerine sahip makinelerde izin verilir.

> [!WARNING]
> Güncelleştirme 3 Visual Studio 2013 den başlayarak, bu görev dosya için hedef çerçeve sürümünü belirtmenize olanak sağlayan yeni bir imzaya sahip. Yeni imzayı mümkün olduğunca kullanabilirsiniz çünkü MSBuild işlemi yalnızca hedef çerçeve .NET 4.5 veya daha yüksek olduğunda SHA-256 karmalarını kullanır. Hedef çerçeve .NET 4.0 veya altı ise SHA-256 karması kullanılmaz.

|Parametre|Açıklama|
|---------------|-----------------|
|`CertificateThumbprint`|Gerekli `String` parametre.<br /><br /> İmzalama için kullanmak üzere sertifikayı belirtir. Bu sertifika, geçerli kullanıcının kişisel mağazasında yer alalıdır.|
|`SigningTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Sertifikayla oturum açması gereken dosyaları, sertifika türü veya .exe .dll.|
|`TimestampUrl`|İsteğe `String` bağlı parametre.<br /><br /> Zaman damgası sunucusunun URL'sini belirtir.|
|`TargetFrameworkVersion`|Hedef için .NET Framework için kullanılan dosyanın sürümü.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak sınıfından parametreleri <xref:Microsoft.Build.Utilities.Task> devralıyor. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [Görev temel sınıfı.](../msbuild/task-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğe koleksiyonunda belirtilen dosyaları özelliği tarafından belirtilen sertifikayla `SignFile` `FilesToSign` imzalamak için görevini `CertificateThumbprint` kullanır.

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
> Sertifika parmak izi, sertifikanın SHA-1 karmasıdır. Daha fazla bilgi için [bkz. Güvenilen kök CA sertifikasının SHA-1 karması alma.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)) Sertifika ayrıntılarından parmak izini kopyalayıp yapıştırıyorsanız, sertifikayı bulmasını önleyen fazladan (3F) görünmez karakterini `SignFile` içermeyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)