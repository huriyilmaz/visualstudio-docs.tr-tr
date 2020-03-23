---
title: SignFile Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: ee018b42fc23b0a520b510235117cb74729fd4b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094525"
---
# <a name="signfile-task"></a>SignFile görevi

Belirtilen sertifikayı kullanarak belirtilen dosyayı işaretler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `SignFile` açıklanmaktadır.

 SHA-256 sertifikalarına yalnızca .NET 4.5 ve üzeri makinelerde izin verildiğini unutmayın.

> [!WARNING]
> Visual Studio 2013 Update 3'ten başlayarak, bu görevin dosyanın hedef çerçeve sürümünü belirtmenizi sağlayan yeni bir imzası vardır. MSBuild işlemi sha-256 hashes yalnızca hedef çerçeve .NET 4.5 veya daha yüksek olduğunda kullandığından, mümkün olan her yerde yeni imzayı kullanmanız için teşvik edilirsiniz. Hedef çerçeve .NET 4.0 veya altında ise SHA-256 karma kullanılmaz.

|Parametre|Açıklama|
|---------------|-----------------|
|`CertificateThumbprint`|Gerekli `String` parametre.<br /><br /> İmzalamak için kullanılacak sertifikayı belirtir. Bu sertifika geçerli kullanıcının kişisel deposunda olmalıdır.|
|`SigningTarget`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Sertifikayla imzalayacak dosyaları belirtir.|
|`TimestampUrl`|İsteğe bağlı `String` parametre.<br /><br /> Zaman damgalama sunucusunun URL'sini belirtir.|
|`TargetFrameworkVersion`|Hedef için kullanılan .NET Framework sürümü.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev <xref:Microsoft.Build.Utilities.Task> sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [Görev taban sınıfına](../msbuild/task-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `SignFile` `FilesToSign` `CertificateThumbprint` öğe koleksiyonunda belirtilen dosyaları özellik tarafından belirtilen sertifikayla imzalamak için görevi kullanır.

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
> Sertifika parmak izi, sertifikanın SHA-1 karmadır. Daha fazla bilgi için bkz: [Güvenilir bir kök CA sertifikasının SHA-1 karmasını edinin.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)) Sertifika ayrıntılarındaki parmak izini kopyalayıp yapıştırırsanız, sertifikayı bulmayı engelleyebilecek `SignFile` ekstra (3F) görünmez karakteri eklemediğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)