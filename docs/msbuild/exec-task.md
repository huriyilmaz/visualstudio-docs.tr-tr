---
title: Exec görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aef20a322ad3743ed1cb89955654456dff670e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591456"
---
# <a name="exec-task"></a>Yürütme görevi
Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırır.

## <a name="parameters"></a>Parametreler
Aşağıdaki tabloda `Exec` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Command`|Gerekli `String` parametresi.<br /><br /> Çalıştırılacak komut (lar). Bunlar, attrib gibi sistem komutları veya *program. exe*, *runprogram. bat*veya *Setup. msi*gibi yürütülebilir bir dosya olabilir.<br /><br /> Bu parametre, birden çok komut satırı içerebilir. Alternatif olarak, birden fazla komutu bir toplu iş dosyasına yerleştirebilir ve bu parametreyi kullanarak çalıştırabilirsiniz.|
|`ConsoleOutput`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Her öğe çıktısı, araç tarafından yayılan standart çıkış veya standart hata akışından alınan bir satırdır. Bu yalnızca `ConsoleToMsBuild` `true`olarak ayarlanırsa yakalanır.|
|`ConsoleToMsBuild`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev standart hata ve aracın standart çıkışını yakalar ve bunları `ConsoleOutput` çıkış parametresinde kullanılabilir hale getirir.<br /><br />Varsayılan: `false`.|
|`CustomErrorRegularExpression`|İsteğe bağlı `String` parametresi.<br /><br /> Araç çıkışında hata çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`CustomWarningRegularExpression`|İsteğe bağlı `String` parametresi.<br /><br /> Araç çıkışında uyarı çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`EchoOff`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev, genişletilmiş `Command` biçimini MSBuild günlüğüne yaymaz.<br /><br />Varsayılan: `false`.|
|`ExitCode`|İsteğe bağlı `Int32` çıkışı salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir.|
|`IgnoreExitCode`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev yürütülen komut tarafından belirtilen çıkış kodunu yoksayar. Aksi takdirde, yürütülen komut sıfır olmayan bir çıkış kodu döndürürse görev `false` döndürür.<br /><br />Varsayılan: `false`.|
|`IgnoreStandardErrorWarningFormat`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `false`, çıkışta standart hata/uyarı biçimiyle eşleşen satırları seçer ve bunları hata/uyarı olarak günlüğe kaydeder. `true`, bu davranışı devre dışı bırakın.<br /><br />Varsayılan: `false`.|
|`Outputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Görevden çıkış öğelerini içerir. `Exec` görev bunları kendisi yapmaz. Bunun yerine, daha sonra projede kullanılabilmesi için bunları ayarlamış gibi sağlayabilirsiniz.|
|`StdErrEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`StdOutEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`WorkingDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Komutun çalıştırılacağı dizini belirtir.<br /><br />Varsayılan: projenin geçerli çalışma dizini.|

## <a name="remarks"></a>Açıklamalar
Bu görev, gerçekleştirmek istediğiniz iş için belirli bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görevi kullanılabilir olmadığında yararlıdır. Ancak, daha belirli bir görevden farklı olarak `Exec` görevi, çalıştığı aracın veya komutun sonucuna göre ek işlem veya koşullu işlemler yapılamaz.

`Exec` görevi, doğrudan bir işlemi çağırmak yerine *cmd. exe* ' yi çağırır.

Bu belgede listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.ToolTask> sınıfından devralan <xref:Microsoft.Build.Tasks.ToolTaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [ToolTaskExtension temel sınıfı](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Örnek
Aşağıdaki örnek, bir komutu çalıştırmak için `Exec` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
