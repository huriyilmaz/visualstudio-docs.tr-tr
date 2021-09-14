---
title: ToolsVersion Ayarlar |'i geçersiz kılma Microsoft Docs
description: Projeler ve çözümler için MSBuild Araç Kümesi'nin değerini değiştirme veya geçersiz kılmanın çeşitli yollarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8bcb1307714b33e87a886cef18dd97e3d6000e0c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628418"
---
# <a name="override-toolsversion-settings"></a>ToolsVersion ayarlarını geçersiz kılma

Projeler ve çözümler için Araç Kümesi'nin üç farklı yolu vardır:

1. Proje veya `-ToolsVersion` çözümü komut satırdan derlemek için anahtarını `-tv` (veya kısaca ) kullanarak.

2. Bu görev `ToolsVersion` için parametresini MSBuild.

3. Bir çözüm `$(ProjectToolsVersion)` içindeki bir proje üzerinde özelliğini ayarerek. Bu, diğer projelerden farklı bir Araç Kümesi sürümüne sahip bir çözümde proje derlemenizi sağlar.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Komut satırı derlemelerinde projelerin ve çözümlerin ToolsVersion ayarlarını geçersiz kılma

 Proje Visual Studio genellikle proje dosyasında belirtilen ToolsVersion ile derleme yapmakla birlikte, bu değeri geçersiz kılmak ve tüm projeleri ve projeden projeye bağımlılıklarını farklı bir Araç Kümesi ile derlemek için komut satırı anahtarını `-ToolsVersion` `-tv` kullanabilirsiniz. Örnek:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 Bu örnekte tüm projeler ToolsVersion 12.0 kullanılarak hazır edilmiştir. (Ancak, bu konunun [ilerleyen kısımlarında Yer alan](#order-of-precedence) Öncelik sırası bölümüne bakın.)

 Komut satırı anahtarını kullanırken, isteğe bağlı olarak tek tek projelerde özelliğini kullanarak bunları çözümde yer alan diğer projelerden farklı `-tv` `$(ProjectToolsVersion)` bir ToolsVersion değeriyle derlemek için kullanabilirsiniz.

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild görevinin ToolsVersion parametresini kullanarak ToolsVersion MSBuild geçersiz kılın

 Bu MSBuild, bir projenin başka bir proje oluşturması için birincil yol olarak görevdir. Bir MSBuild projesinde belirtilenden farklı ToolsVersion değerine sahip bir proje derlemesini sağlamak için, adlı isteğe bağlı bir görev parametresi `ToolsVersion` sağlar. Aşağıdaki örnek, bu parametrenin nasıl kullanılageldi:

1. *projectA.proj* adlı ve aşağıdaki kodu içeren bir dosya oluşturun:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go" >
            <Message Text="projectA.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />

            <MSBuild Projects="projectB.proj"
                ToolsVersion="2.0"
                Targets="go" />
        </Target>
    </Project>
    ```

2. *projectB.proj* adlı ve aşağıdaki kodu içeren başka bir dosya oluşturun:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go">
            <Message Text="projectB.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />
        </Target>
    </Project>
    ```

3. Komut istemine aşağıdaki komutu girin:

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. Aşağıdaki çıkış görüntülenir. `projectA`için, `-toolsversion:3.5` komut satırı ayarı etiketinde ayarı `ToolsVersion=12.0` geçersiz `Project` kılar.

     `ProjectB` içinde bir görev tarafından `projectA` çağrılır. Bu görev, `ToolsVersion=2.0` için diğer ayarları geçersiz `ToolsVersion` kılan `projectB` içerir.

    ```
    Output:
      projectA.proj
      MSBuildToolsVersion: 3.5
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5

      projectB.proj
      MSBuildToolsVersion: 2.0
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727
    ```

## <a name="order-of-precedence"></a>Öncelik sırası

 Öncelik sırası (en yüksekten en düşüke) belirlemek için `ToolsVersion` kullanılır:

1. Varsa, `ToolsVersion` MSBuild oluşturmak için kullanılan bir görev olan MSBuild özniteliği.

2. Varsa, msbuild.exe komutunda `-toolsversion` `-tv` kullanılan (veya ) anahtarı.

3. Ortam değişkeni `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlanmışsa geçerli değerini `ToolsVersion` kullanın.

4. Ortam değişkeni ayarlanmışsa ve proje dosyasında tanımlanan değeri geçerli olandan `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` `ToolsVersion` büyükse `ToolsVersion` geçerli değerini `ToolsVersion` kullanın.

5. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmışsa veya `ToolsVersion` ayarlanmazsa aşağıdaki adımlar kullanılır:

    1. Proje `ToolsVersion` dosyasının [Project](../msbuild/project-element-msbuild.md) özniteliği. Bu öznitelik yoksa, geçerli sürüm olduğu varsayılır.

    2. MSBuild.exe.config *dosyasındaki varsayılanMSBuild.exe.config* sürümü.

    3. Kayıt defterindeki varsayılan araçlar sürümü. Daha fazla bilgi için [bkz. Standart ve özel Araç Kümesi yapılandırmaları.](../msbuild/standard-and-custom-toolset-configurations.md)

6. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmazsa aşağıdaki adımlar kullanılır:

    1. Ortam değişkeni mevcut `MSBUILDDEFAULTTOOLSVERSION` bir `ToolsVersion` değişkene ayarlanırsa, bunu kullanın.

    2. içinde `DefaultOverrideToolsVersion` *ayarlanmışsaMSBuild.exe.config* kullanın.

    3. Kayıt `DefaultOverrideToolsVersion` defterinde ayarlanmışsa bunu kullanın.

    4. Aksi takdirde, geçerli `ToolsVersion` kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standart ve özel Araç Kümesi yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)
