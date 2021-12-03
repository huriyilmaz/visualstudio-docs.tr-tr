---
title: Exec görevi | Microsoft Docs
description: belirtilen bağımsız değişkenleri kullanarak belirtilen program veya komutu çalıştırmak için MSBuild Exec görevini kullanmayı öğrenin.
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
ms.openlocfilehash: 7bc000fdac61e6f3f1ef55cf64f3bbe689f2e197
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514317"
---
# <a name="exec-task"></a>Yürütme görevi

Belirtilen bağımsız değişkenleri kullanarak belirtilen programı veya komutu çalıştırır.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, görevi için parametreler açıklanmaktadır `Exec` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Command`|Gerekli `String` parametre.<br /><br /> Çalıştırılacak komut (lar). Bunlar, attrib gibi sistem komutları veya *program.exe*, *runprogram.bat* veya *setup.msi* gibi yürütülebilir bir dosya olabilir.<br /><br /> Bu parametre, birden çok komut satırı içerebilir. Alternatif olarak, birden fazla komutu bir toplu iş dosyasına yerleştirebilir ve bu parametreyi kullanarak çalıştırabilirsiniz.|
|`ConsoleOutput`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Her öğe çıktısı, araç tarafından yayılan standart çıkış veya standart hata akışından alınan bir satırdır. Bu yalnızca `ConsoleToMsBuild` olarak ayarlanırsa yakalanır `true` .|
|`ConsoleToMsBuild`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Bu görev, aracının standart hatasını ve standart çıkışını yakalayıp çıkış parametresinde kullanılabilir hale getirir `ConsoleOutput` .<br /><br />Varsayılan: `false`.|
|`CustomErrorRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışında hata çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`CustomWarningRegularExpression`|İsteğe bağlı `String` parametre.<br /><br /> Araç çıkışında uyarı çizgilerini belirlemek için kullanılan bir normal ifade belirtir. Bu, olağandışı biçimli çıkış üreten araçlar için kullanışlıdır.<br /><br />Varsayılan: `null` (özel işlem yok).|
|`EchoOff`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`bu görev, genişletilmiş biçimini `Command` MSBuild günlüğüne yaymaz.<br /><br />Varsayılan: `false`.|
|`ExitCode`|İsteğe bağlı `Int32` Çıkış salt okunurdur parametresi.<br /><br /> Görev herhangi bir hata günlüğe kaydedildiğinde, ancak işlem 0 ' dan (başarılı),-1 ' e ayarlandığında yürütülen komutla birlikte sunulan çıkış kodunu belirtir `ExitCode` .|
|`IgnoreExitCode`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev yürütülen komutu tarafından belirtilen çıkış kodunu yoksayar. Aksi takdirde, `false` çalıştırılan komutun sıfır olmayan bir çıkış kodu döndürmesi durumunda görev döndürülür.<br /><br />Varsayılan: `false`.|
|`IgnoreStandardErrorWarningFormat`|İsteğe bağlı `Boolean` parametre.<br /><br /> `false`, Çıkışta standart hata/uyarı biçimiyle eşleşen satırları seçer ve bunları hata/uyarı olarak günlüğe kaydeder. Varsa `true` , bu davranışı devre dışı bırakın.<br /><br />Varsayılan: `false`.|
|`Outputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Görevden çıkış öğelerini içerir. `Exec`Görev bunları kendisi yapmaz. Bunun yerine, daha sonra projede kullanılabilmesi için bunları ayarlamış gibi sağlayabilirsiniz.|
|`StdErrEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart hata akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`StdOutEncoding`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yakalanan görev standart çıkış akışının kodlamasını belirtir. Varsayılan değer geçerli konsol çıkış kodlamasında bulunur.|
|`UseUtf8Encoding`|İsteğe bağlı `String` parametre.<br /><br /> Yürütülen komutlar için komut satırını işlerken UTF8 kod sayfasının kullanılıp kullanılmayacağını belirtir. Geçerli değerler `Always` , `Never` , veya `Detect` . Varsayılan değer `Detect` olarak, yalnızca ANSI olmayan karakterler mevcut olduğunda UTF8 Code sayfasını kullanın.|
|`WorkingDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Komutun çalıştırılacağı dizini belirtir.<br /><br />Varsayılan: projenin geçerli çalışma dizini.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Açıklamalar

bu görev, gerçekleştirmek istediğiniz iş için belirli bir MSBuild görevi kullanılabilir olmadığında yararlıdır. Ancak, `Exec` daha belirli bir görevin aksine görev, çalıştığı aracın veya komutun sonucuna göre ek işlem veya koşullu işlemler yapılamaz.

`Exec`Görev, doğrudan bir işlemi çağırmak yerine *cmd.exe* çağırır.

Parametreler `IgnoreExitCode` ve `IgnoreStandardErrorWarningFormat` görevin döndürdüğü koşulları `false` bir hata belirterek etkiler. Varsayılan ayarlarla ( `false` her ikisi için), çalıştırılabilir dosyanın `Exec` `false` sıfır olmayan bir çıkış kodu varsa veya yürütülebilir dosyanın standart hata akışında bir tanılama iletisi bulunursa, görev bir hata olduğunu gösterir (döndürür). Yalnızca `Exec` yürütülebilir dosya sıfır olmayan bir çıkış kodu döndürürse hata göstermek istiyorsanız `IgnoreStandardErrorWarningFormat` olarak ayarlayın `true` .

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Exec` bir komutu çalıştırmak için görevini kullanır.

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
