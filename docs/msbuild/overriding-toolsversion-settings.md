---
title: Geçersiz Kılma AraçlarıSürüm Ayarları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13c33f0ef43707390aa32d4c26c0380a8a32883e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633024"
---
# <a name="override-toolsversion-settings"></a>ToolsVersion ayarlarını geçersiz kıl

Projeler ve çözümler için Araç Kümesini üç şekilde değiştirebilirsiniz:

1. Komut satırından `-ToolsVersion` proje `-tv`yi veya çözümü oluştururken anahtarı (veya kısaca) kullanarak.

2. MSBuild `ToolsVersion` görevinde parametre ayarlayarak.

3. `$(ProjectToolsVersion)` Bir çözüm içinde bir proje üzerinde özellik ayarlayarak. Bu, diğer projelerden farklı bir Araç Kümesi sürümüyle bir çözümde proje oluşturmanıza olanak tanır.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Komut satırı oluştururdaki projelerin ve çözümlerin ToolsVersion ayarlarını geçersiz kılın

 Visual Studio projeleri genellikle proje dosyasında belirtilen ToolsVersion ile inşa `-ToolsVersion` edilse de, bu değeri geçersiz kılmak ve tüm projeleri ve projeden projeye bağımlılıklarını farklı bir Araç Kümesiyle oluşturmak için komut satırındaki (veya) `-tv`anahtarını kullanabilirsiniz. Örnek:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 Bu örnekte, tüm projeler ToolsVersion 12.0 kullanılarak oluşturulmuştür. (Ancak, bu konuda daha sonra [öncelik sırasına](#order-of-precedence) bakın.)

 Komut satırındaki `-tv` anahtarı kullanırken, özelliği tek `$(ProjectToolsVersion)` tek projelerde kullanarak çözümdeki diğer projelerden farklı bir ToolsVersion değeriyle oluşturabilirsiniz.

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild görevinin ToolsVersion parametresini kullanarak ToolsVersion ayarlarını geçersiz kılın

 MSBuild görevi, bir projenin başka bir proje oluşturması için birincil araçtır. MSBuild görevinin projede belirtilenden farklı bir ToolsVersion'a sahip bir proje oluşturmasını sağlamak `ToolsVersion`için, isteğe bağlı görev parametresi adı verilen bir görev parametresi sağlar. Aşağıdaki örnek, bu parametrenin nasıl kullanılacağını gösterir:

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

3. Komut isteminde aşağıdaki komutu girin:

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. Aşağıdaki çıktı görüntülenir. Çünkü, `projectA` `-toolsversion:3.5` komut satırındaki ayar `ToolsVersion=12.0` `Project` etiketteki ayarı geçersiz kılar.

     `ProjectB`bir görev tarafından `projectA`çağrılır. Bu `ToolsVersion=2.0`görev, diğer `ToolsVersion` ayarları geçersiz `projectB`kılar.

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

 Öncelik sırası, en yüksekten en düşük, belirlemek `ToolsVersion` için kullanılır:

1. `ToolsVersion` Varsa, projeyi oluşturmak için kullanılan MSBuild görevindeki öznitelik.

2. Msbuild.exe komutunda kullanılan `-toolsversion` (veya) `-tv`anahtarı, varsa.

3. Ortam değişkeni `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlanmışsa, akımı `ToolsVersion`kullanın.

4. Ortam değişkeni `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ayarlanmışsa `ToolsVersion` ve proje dosyasında tanımlanan `ToolsVersion`geçerliden büyükse, akımı `ToolsVersion`kullanın.

5. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmışsa `ToolsVersion` veya ayarlı değilse, aşağıdaki adımlar kullanılır:

    1. `ToolsVersion` Proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinin özniteliği. Bu öznitelik yoksa, geçerli sürümü olduğu varsayılır.

    2. *MSBuild.exe.config* dosyasındaki varsayılan araçlar sürümü.

    3. Kayıt defterindeki varsayılan araçlar sürümü. Daha fazla bilgi için [Standart ve özel Araç Seti yapılandırmalarına](../msbuild/standard-and-custom-toolset-configurations.md)bakın.

6. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlı değilse, aşağıdaki adımlar kullanılır:

    1. Ortam değişkeni `MSBUILDDEFAULTTOOLSVERSION` var olan `ToolsVersion` a olarak ayarlanmışsa, onu kullanın.

    2. `DefaultOverrideToolsVersion` *MSBuild.exe.config'de*ayarlanmışsa, kullanın.

    3. Kayıt `DefaultOverrideToolsVersion` defterinde ayarlanmışsa, kullanın.

    4. Aksi takdirde, `ToolsVersion`geçerli kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standart ve özel Araç Seti yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)
