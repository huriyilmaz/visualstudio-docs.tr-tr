---
title: Exec Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: f588ae1b32b8b8d47d6323ee32d02c9053a3de32
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634220"
---
# <a name="exec-task"></a>Yürütme görevi

Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görev parametreleri `Exec` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Command`|Gerekli `String` parametre.<br /><br /> Çalıştırmak için komut(lar). Bunlar attrib veya *program.exe,* *runprogram.bat*veya *setup.msi*gibi yürütülebilir sistem komutları olabilir.<br /><br /> Bu parametre birden çok komut satırı içerebilir. Alternatif olarak, bir toplu iş dosyasına birden çok komut koyup bu parametreyi kullanarak çalıştırabilirsiniz.|
|`ConsoleOutput`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Her madde çıkışı, araç tarafından yayılan standart çıktı veya standart hata akışından bir satırdır. Bu yalnızca ' `ConsoleToMsBuild` olarak `true`ayarlanırsa yakalanır.|
|`ConsoleToMsBuild`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`görev aracın standart hata ve standart çıktı sını yakalar `ConsoleOutput` ve çıktı parametresinde kullanılabilir hale getirir.<br /><br />Varsayılan: `false`.|
|`CustomErrorRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışındaki hata satırlarını noktalamak için kullanılan normal bir ifade belirtir. Bu, olağandışı biçimlendirilmiş çıktı üreten araçlar için yararlıdır.<br /><br />Varsayılan: `null` (özel işleme yok).|
|`CustomWarningRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışındaki uyarı çizgilerini noktalamak için kullanılan normal bir ifade belirtir. Bu, olağandışı biçimlendirilmiş çıktı üreten araçlar için yararlıdır.<br /><br />Varsayılan: `null` (özel işleme yok).|
|`EchoOff`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`görev MSBuild `Command` günlüğüne genişletilmiş formu yatmayacak.<br /><br />Varsayılan: `false`.|
|`ExitCode`|İsteğe bağlı `Int32` çıktı salt okunur parametresi.<br /><br /> Çalıştırılan komut tarafından sağlanan çıkış kodunu belirtir.|
|`IgnoreExitCode`|İsteğe bağlı `Boolean` parametre.<br /><br /> If `true`, görev, yürütülen komut tarafından sağlanan çıkış kodunu yoksa. Aksi takdirde, `false` çalıştırılan komut sıfır olmayan bir çıkış kodu döndürürse görev döndürür.<br /><br />Varsayılan: `false`.|
|`IgnoreStandardErrorWarningFormat`|İsteğe bağlı `Boolean` parametre.<br /><br /> , `false`çıktıda standart hata/uyarı biçimiyle eşleşen satırları seçer ve bunları hata/uyarı olarak kaydeder. Eğer `true`, bu davranışı devre dışı.<br /><br />Varsayılan: `false`.|
|`Outputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Görevden çıktı öğelerini içerir. Görev `Exec` bunları kendisi ayarlamaz. Bunun yerine, onları ayarlanmış gibi sağlayabilir, böylece daha sonra projede kullanılabilir.|
|`StdErrEncoding`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlayıcısını belirtir. Varsayılan, geçerli konsol çıktıkodlamasidir.|
|`StdOutEncoding`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Yakalanan görev standart çıktı akışının kodlanması belirtir. Varsayılan, geçerli konsol çıktıkodlamasidir.|
|`WorkingDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Komutun çalışacağı dizini belirtir.<br /><br />Varsayılan: Projenin geçerli çalışma dizini.|

## <a name="remarks"></a>Açıklamalar

Bu görev, gerçekleştirmek istediğiniz iş için belirli bir MSBuild görevi kullanılamadığında yararlıdır. Ancak, `Exec` görev, daha belirli bir görevin aksine, çalıştırdığı aracın veya komutun sonucuna göre ek işleme veya koşullu işlemler yapamaz.

Görev, `Exec` doğrudan bir işlemi çağırmak yerine *cmd.exe* çağırır.

Bu belgede listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.ToolTaskExtension> <xref:Microsoft.Build.Utilities.ToolTask> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [ToolTaskExtension taban sınıfına](../msbuild/tooltaskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `Exec` bir komutçalıştırmak için görev kullanır.

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
