---
title: Exec Task | Microsoft Docs
description: Belirtilen bağımsız değişkenleri kullanarak MSBuild programı veya komutu çalıştırmak için MSBuild Exec görevini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2fafde90853a14afa164aa8f8a2a7e616b83818c5bc627d64800515f0f7fbad4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428113"
---
# <a name="exec-task"></a>Yürütme görevi

Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırır.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `Exec` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Command`|Gerekli `String` parametre.<br /><br /> Çalıştıracak komutlar. Bunlar attrib gibi sistem komutları veyaprogram.exe, *runprogram.bat* veya *setup.msi.* **<br /><br /> Bu parametre birden çok komut satırı içerebilir. Alternatif olarak, bir toplu iş dosyasına birden çok komut koyabilirsiniz ve bu parametreyi kullanarak çalıştırabilirsiniz.|
|`ConsoleOutput`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Her öğe çıkışı, standart çıkıştan veya araç tarafından yayılan standart hata akışından bir satırdır. Bu yalnızca olarak `ConsoleToMsBuild` ayarlanırsa `true` yakalanır.|
|`ConsoleToMsBuild`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, görev aracın standart hatasını ve standart çıktısını yakalar ve bunları çıkış `true` parametresinde `ConsoleOutput` kullanılabilir hale gelir.<br /><br />Varsayılan: `false`.|
|`CustomErrorRegularExpression`|İsteğe `String` bağlı parametre.<br /><br /> Araç çıkışında hata satırlarını tespit etmek için kullanılan normal bir ifadeyi belirtir. Bu, olağan dışı biçimlendirilmiş çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işleme yok).|
|`CustomWarningRegularExpression`|İsteğe `String` bağlı parametre.<br /><br /> Araç çıkışında uyarı çizgilerini tespit etmek için kullanılan normal bir ifadeyi belirtir. Bu, olağan dışı biçimlendirilmiş çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işleme yok).|
|`EchoOff`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev genişletilmiş formunu günlük `Command` kaydına MSBuild.<br /><br />Varsayılan: `false`.|
|`ExitCode`|İsteğe `Int32` bağlı çıkış salt okunur parametresi.<br /><br /> Yürütülen komut tarafından sağlanan çıkış kodunu belirtir, ancak görevin herhangi bir hata günlüğe kaydederek işlemde çıkış kodu 0 (başarılı) olan `ExitCode` -1 olarak ayarlanmıştır.|
|`IgnoreExitCode`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev yürütülen komut tarafından sağlanan çıkış kodunu yoksayar. Aksi takdirde, yürütülen `false` komut sıfır olmayan bir çıkış kodu döndürürse görev döndürür.<br /><br />Varsayılan: `false`.|
|`IgnoreStandardErrorWarningFormat`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `false` çıkışta standart hata/uyarı biçimiyle eşan satırları seçer ve bunları hata/uyarı olarak günlüğe kaydeder. ise, `true` bu davranışı devre dışı bırak.<br /><br />Varsayılan: `false`.|
|`Outputs`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Görevdeki çıkış öğelerini içerir. Görev `Exec` bunları ayarlamaz. Bunun yerine, daha sonra projenin devamlarında kullanılamalarını sağlamak için bunları ayarladı gibi sebilirsiniz.|
|`StdErrEncoding`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlamasını belirtir. Varsayılan, geçerli konsol çıkış kodlamasıdır.|
|`StdOutEncoding`|İsteğe `String` bağlı çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışının kodlamasını belirtir. Varsayılan, geçerli konsol çıkış kodlamasıdır.|
|`UseUtf8Encoding`|İsteğe `String` bağlı parametre.<br /><br /> Yürütülen komutlar için komut satırı işülürken UTF8 kod sayfasının kullanıp kullanılamayca olmadığını belirtir. Geçerli değerler `Always` : , veya `Never` `Detect` . Varsayılan değer, UTF8 kod sayfasını yalnızca ANSI olmayan karakterler mevcut olduğunda kullanmak `Detect` anlamına gelir.|
|`WorkingDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Komutun çalıştır çalıştırıla dizini belirtir.<br /><br />Varsayılan: Projenin geçerli çalışma dizini.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Açıklamalar

Bu görev, gerçekleştirmek istediğiniz MSBuild belirli bir görev kullanılabilir durumda değilken kullanışlıdır. Ancak, görev daha belirli bir görevin aksine, aracın veya çalıştırmakta olduğu komutun sonucuna bağlı olarak `Exec` ek işlem veya koşullu işlemler çalıştıramaz.

`Exec`Görev, *cmd.exe* doğrudan çağrı yapmak yerine çağrıyı çağrılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, komutunu `Exec` çalıştırmak için görevini kullanır.

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
