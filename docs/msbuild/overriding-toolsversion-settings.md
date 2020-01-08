---
title: Araçları sürüm ayarlarını geçersiz kılma | Microsoft Docs
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
ms.openlocfilehash: 1706d0e82139da5962fbb43610cdecd6b1477ad1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590494"
---
# <a name="override-toolsversion-settings"></a>Araçları sürüm ayarlarını geçersiz kıl
Proje ve çözümlerin araç takımını üç şekilde değiştirebilirsiniz:

1. Komut satırından proje veya çözüm oluştururken `-ToolsVersion` anahtarını (veya Short için `-tv`) kullanarak.

2. MSBuild görevinde `ToolsVersion` parametresini ayarlayarak.

3. Çözüm içindeki bir projede `$(ProjectToolsVersion)` özelliğini ayarlayarak. Bu, diğer projelerden farklı bir araç takımı sürümüne sahip bir çözümde proje oluşturmanıza olanak sağlar.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Komut satırı derlemelerindeki projelerin ve çözümlerin araçları sürüm ayarlarını geçersiz kılın
 Visual Studio projeleri genellikle proje dosyasında belirtilen bir araçları sürümü ile derlense de, bu değeri geçersiz kılmak ve projeleri ve proje-proje bağımlılıklarını farklı bir araç kümesiyle oluşturmak için komut satırında `-ToolsVersion` (veya `-tv`) anahtarını kullanabilirsiniz. Örneğin:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 Bu örnekte, tüm projeler, araçları sürüm 12,0 kullanılarak oluşturulmuştur. (Ancak, bu konunun ilerleyen kısımlarında yer alarak [öncelik sırası](#order-of-precedence) bölümüne bakın.)

 Komut satırında `-tv` anahtarını kullanırken, isteğe bağlı `$(ProjectToolsVersion)` olarak, çözümdeki diğer projelerden farklı bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir bir araçları sürümü değeri ile oluşturmak için

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild görevinin araçları sürümü parametresini kullanarak, araçları sürüm ayarlarını geçersiz kılın
 MSBuild görevi, bir projenin başka bir proje oluşturması için birincil anlamına gelir. MSBuild görevini, projede belirtilenden farklı bir araçları sürümüne sahip bir proje oluşturmak üzere etkinleştirmek için, `ToolsVersion`adlı isteğe bağlı bir görev parametresi sağlar. Aşağıdaki örnek, bu parametrenin nasıl kullanılacağını gösterir:

1. *ProjectA. proj* adlı ve aşağıdaki kodu içeren bir dosya oluşturun:

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

2. *ProjectB. proj* adlı ve aşağıdaki kodu içeren başka bir dosya oluşturun:

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

4. Aşağıdaki çıktı görüntülenir. `projectA`için, komut satırındaki `-toolsversion:3.5` ayarı `Project` etiketindeki `ToolsVersion=12.0` ayarını geçersiz kılar.

     `ProjectB`, `projectA`bir görev tarafından çağırılır. Bu görevde, `projectB`için diğer `ToolsVersion` ayarları geçersiz kılan `ToolsVersion=2.0`vardır.

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
 `ToolsVersion` belirlenmesi için kullanılan en yüksekten en düşüğe öncelik sırası:

1. MSBuild görevinde, varsa, projeyi oluşturmak için kullanılan `ToolsVersion` özniteliği.

2. Varsa, MSBuild. exe komutunda kullanılan `-toolsversion` (veya `-tv`) anahtarı.

3. Ortam değişkeni `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlandıysa, geçerli `ToolsVersion`kullanın.

4. Ortam değişkeni `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ayarlandıysa ve proje dosyasında tanımlanan `ToolsVersion` geçerli `ToolsVersion`büyükse, geçerli `ToolsVersion`kullanın.

5. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlandıysa veya `ToolsVersion` ayarlanmamışsa, aşağıdaki adımlar kullanılır:

    1. Proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinin `ToolsVersion` özniteliği. Bu öznitelik yoksa, geçerli sürüm olduğu varsayılır.

    2. *MSBuild. exe. config* dosyasındaki varsayılan Araçlar sürümü.

    3. Kayıt defterindeki varsayılan Araçlar sürümü. Daha fazla bilgi için bkz. [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).

6. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmamışsa, aşağıdaki adımlar kullanılır:

    1. Ortam değişkeni `MSBUILDDEFAULTTOOLSVERSION` var olan bir `ToolsVersion` ayarlandıysa, bunu kullanın.

    2. *MSBuild. exe. config*içinde `DefaultOverrideToolsVersion` ayarlandıysa onu kullanın.

    3. Kayıt defterinde `DefaultOverrideToolsVersion` ayarlandıysa, onu kullanın.

    4. Aksi takdirde, geçerli `ToolsVersion`kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)
