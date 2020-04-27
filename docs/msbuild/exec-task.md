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
ms.openlocfilehash: 634916d9ab4ef0ce3119fcb5695301598992f38c
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167312"
---
# <a name="exec-task"></a>Yürütme görevi

Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırır.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, `Exec` görevi için parametreler açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Command`|Gerekli `String` parametre.<br /><br /> Çalıştırılacak komut (lar). Bunlar, attrib gibi sistem komutları veya *program. exe*, *runprogram. bat*veya *Setup. msi*gibi yürütülebilir bir dosya olabilir.<br /><br /> Bu parametre, birden çok komut satırı içerebilir. Alternatif olarak, birden fazla komutu bir toplu iş dosyasına yerleştirebilir ve bu parametreyi kullanarak çalıştırabilirsiniz.|
|`ConsoleOutput`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Her öğe çıktısı, araç tarafından yayılan standart çıkış veya standart hata akışından alınan bir satırdır. Bu yalnızca olarak `true`ayarlanırsa yakalanır `ConsoleToMsBuild` .|
|`ConsoleToMsBuild`|İsteğe `Boolean` bağlı parametre.<br /><br /> Bu `true`görev, aracının standart hatasını ve standart çıkışını yakalayıp `ConsoleOutput` çıkış parametresinde kullanılabilir hale getirir.<br /><br />Varsayılan: `false`.|
|`CustomErrorRegularExpression`|İsteğe `String` bağlı parametre.<br /><br /> Araç çıkışında hata çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`CustomWarningRegularExpression`|İsteğe `String` bağlı parametre.<br /><br /> Araç çıkışında uyarı çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`EchoOff`|İsteğe `Boolean` bağlı parametre.<br /><br /> Eğer `true`görev, genişletilmiş formunu `Command` MSBuild günlüğüne göstermeyecektir.<br /><br />Varsayılan: `false`.|
|`ExitCode`|İsteğe `Int32` bağlı çıkış salt okunurdur parametresi.<br /><br /> Yürütülen komut tarafından belirtilen çıkış kodunu belirtir.|
|`IgnoreExitCode`|İsteğe `Boolean` bağlı parametre.<br /><br /> İse `true`, görev yürütülen komutu tarafından belirtilen çıkış kodunu yoksayar. Aksi takdirde, çalıştırılan komutun `false` sıfır olmayan bir çıkış kodu döndürmesi durumunda görev döndürülür.<br /><br />Varsayılan: `false`.|
|`IgnoreStandardErrorWarningFormat`|İsteğe `Boolean` bağlı parametre.<br /><br /> `false`, Çıkışta standart hata/uyarı biçimiyle eşleşen satırları seçer ve bunları hata/uyarı olarak günlüğe kaydeder. Varsa `true`, bu davranışı devre dışı bırakın.<br /><br />Varsayılan: `false`.|
|`Outputs`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Görevden çıkış öğelerini içerir. `Exec` Görev bunları kendisi yapmaz. Bunun yerine, daha sonra projede kullanılabilmesi için bunları ayarlamış gibi sağlayabilirsiniz.|
|`StdErrEncoding`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`StdOutEncoding`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`WorkingDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Komutun çalıştırılacağı dizini belirtir.<br /><br />Varsayılan: projenin geçerli çalışma dizini.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Açıklamalar

Bu görev, gerçekleştirmek istediğiniz iş için belirli bir MSBuild görevi kullanılabilir olmadığında yararlıdır. Ancak, daha `Exec` belirli bir görevin aksine görev, çalıştığı aracın veya komutun sonucuna göre ek işlem veya koşullu işlemler yapılamaz.

Görev `Exec` , doğrudan bir işlem çağırmak yerine *cmd. exe* ' yi çağırır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir komutu `Exec` çalıştırmak için görevini kullanır.

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
