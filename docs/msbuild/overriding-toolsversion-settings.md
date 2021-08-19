---
title: Ayarlar araçları geçersiz kılma sürümü | Microsoft Docs
description: projeler ve çözümler için MSBuild araç takımının değerini değiştirmek veya geçersiz kılmak için kullanabileceğiniz çeşitli yollar hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108439"
---
# <a name="override-toolsversion-settings"></a>Araçları sürüm ayarlarını geçersiz kıl

Proje ve çözümlerin araç takımını üç şekilde değiştirebilirsiniz:

1. Bir `-ToolsVersion` `-tv` komut satırından proje veya çözüm oluştururken anahtarı (veya kısaca) kullanarak.

2. `ToolsVersion`MSBuild görevde parametresini ayarlayarak.

3. `$(ProjectToolsVersion)`Bir çözüm içindeki bir projede özelliğini ayarlayarak. Bu, diğer projelerden farklı bir araç takımı sürümüne sahip bir çözümde proje oluşturmanıza olanak sağlar.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Komut satırı derlemelerindeki projelerin ve çözümlerin araçları sürüm ayarlarını geçersiz kılın

 Visual Studio projeleri genellikle proje dosyasında belirtilen bir araçları sürümü ile derlense de, `-ToolsVersion` `-tv` bu değeri geçersiz kılmak ve projeleri ve proje-proje bağımlılıklarını farklı bir araç kümesiyle derlemek için komut satırındaki (veya) anahtarını kullanabilirsiniz. Örnek:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 Bu örnekte, tüm projeler, araçları sürüm 12,0 kullanılarak oluşturulmuştur. (Ancak, bu konunun ilerleyen kısımlarında yer alarak [öncelik sırası](#order-of-precedence) bölümüne bakın.)

 `-tv`Komut satırında anahtarı kullanırken, isteğe bağlı olarak bu `$(ProjectToolsVersion)` özelliği, çözümdeki diğer projelerden farklı bir bir bir bir

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild görevinin araçları sürümü parametresini kullanarak, araçları sürüm ayarlarını geçersiz kılın

 MSBuild görev, bir projenin başka bir projenin derlenmesi anlamına gelir. MSBuild görevinin, projede belirtilenden farklı bir araçları sürümüne sahip bir proje oluşturmasını sağlamak için, adlı isteğe bağlı bir görev parametresi sağlar `ToolsVersion` . Aşağıdaki örnek, bu parametrenin nasıl kullanılacağını gösterir:

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

4. Aşağıdaki çıktı görüntülenir. İçin `projectA` , `-toolsversion:3.5` komut satırındaki ayarı `ToolsVersion=12.0` etiketindeki ayarı geçersiz kılar `Project` .

     `ProjectB` , içinde bir görev tarafından çağırılır `projectA` . Bu görev `ToolsVersion=2.0` , için diğer ayarları geçersiz kılar `ToolsVersion` `projectB` .

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

 Öncelik sırası, en yüksekten en düşüğe, şu olduğunu tespit etmek için kullanılır `ToolsVersion` :

1. `ToolsVersion`MSBuild görevinde, varsa, projeyi derlemek için kullanılan öznitelik.

2. `-toolsversion` `-tv` Varsa, msbuild.exe komutunda kullanılan (veya) anahtarı.

3. Ortam değişkeni `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` ayarlandıysa, geçerli öğesini kullanın `ToolsVersion` .

4. Ortam değişkeni `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ayarlandıysa ve `ToolsVersion` Proje dosyasında tanımlı değeri geçerli olandan büyükse `ToolsVersion` , geçerli ' i kullanın `ToolsVersion` .

5. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlandıysa veya `ToolsVersion` ayarlanmamışsa, aşağıdaki adımlar kullanılır:

    1. `ToolsVersion`proje dosyasının [Project](../msbuild/project-element-msbuild.md) öğesinin özniteliği. Bu öznitelik yoksa, geçerli sürüm olduğu varsayılır.

    2. *MSBuild.exe.config* dosyasındaki varsayılan Araçlar sürümü.

    3. Kayıt defterindeki varsayılan Araçlar sürümü. Daha fazla bilgi için bkz. [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).

6. Ortam değişkeni `MSBUILDLEGACYDEFAULTTOOLSVERSION` ayarlanmamışsa, aşağıdaki adımlar kullanılır:

    1. Ortam değişkeni `MSBUILDDEFAULTTOOLSVERSION` bir `ToolsVersion` varsa, bunu kullanın.

    2. `DefaultOverrideToolsVersion` *MSBuild.exe.config*' de ayarlanırsa, onu kullanın.

    3. `DefaultOverrideToolsVersion`Kayıt defterinde ayarlandıysa, onu kullanın.

    4. Aksi takdirde, geçerli öğesini kullanın `ToolsVersion` .

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Araç Takımı (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)
