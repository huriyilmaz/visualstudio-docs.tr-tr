---
title: 'Nasıl kullanılır: Derleme Ortamında Ortam Değişkenlerini | Microsoft Docs'
description: Proje dosyalarında ortam değişkenlerine MSBuild ve proje dosyasını değiştirmeden derleme seçeneklerini ayarlamak için ortam değişkenlerini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1a56d81586fa855552eb5d400c43ddd03e39098b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625682"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Nasıl kullanılır: Derlemede ortam değişkenlerini kullanma

Projeleri derlemek için genellikle proje dosyasında veya projenizi oluşturan dosyalarda yer alan bilgileri kullanarak derleme seçenekleri ayarlamak gerekir. Bu bilgiler genellikle ortam değişkenlerde depolanır.

## <a name="reference-environment-variables"></a>Başvuru ortam değişkenleri

 Tüm ortam değişkenleri, Microsoft Build Engine (MSBuild) proje dosyasında özellikler olarak kullanılabilir.

> [!NOTE]
> Proje dosyası, ortam değişkeniyle aynı adı içeren bir özelliğin açık tanımını içeriyorsa, proje dosyasındaki özelliği ortam değişkeninin değerini geçersiz kılar.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Bir ortam projesinde ortam değişkeni MSBuild için

- Ortam değişkenine, proje dosyanıza bildirilen bir değişkenle aynı şekilde başvurabilirsiniz. Örneğin, aşağıdaki kod aşağıdaki ortam değişkenine BIN_PATH başvurur:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Ortam değişkeni `Condition` ayarlanmazsa, bir özelliğin varsayılan değerini sağlamak için özniteliğini kullanabilirsiniz.

#### <a name="to-provide-a-default-value-for-a-property"></a>Bir özellik için varsayılan değer sağlamak için

- Yalnızca `Condition` özelliğin değeri yoksa, değeri ayarlamak için bir özellikte özniteliği kullanın. Örneğin, aşağıdaki kod özelliğini yalnızca ortam değişkeni ayarlanmazsa `ToolsPath` *c:\tools* `ToolsPath` olarak ayarlar:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Özellik adları büyük/büyük/büyük harfe duyarlı değildir, `$(ToolsPath)` bu nedenle ve aynı özellik veya ortam `$(TOOLSPATH)` değişkenine başvurur.

## <a name="example"></a>Örnek

 Aşağıdaki proje dosyası, dizinlerin konumunu belirtmek için ortam değişkenlerini kullanır.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Nasıl kullanılır: Farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
