---
title: Yapıda Çevre Değişkenlerini Kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afc679f9b782b8bc9ed3e04a2b8fb684cdbc1a20
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633791"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Nasıl kullanılır: Yapıda ortam değişkenlerini kullanma

Proje oluştururken, genellikle proje dosyasında olmayan bilgileri veya projenizi oluşturan dosyaları kullanarak yapı seçenekleri ayarlamak gerekir. Bu bilgiler genellikle ortam değişkenlerinde depolanır.

## <a name="reference-environment-variables"></a>Referans ortamı değişkenleri

 Tüm ortam değişkenleri Microsoft Build Engine (MSBuild) proje dosyasında özellik olarak kullanılabilir.

> [!NOTE]
> Proje dosyası, çevre değişkeni ile aynı ada sahip bir özelliğin açık bir tanımını içeriyorsa, proje dosyasındaki özellik ortam değişkeninin değerini geçersiz kılar.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>MSBuild projesinde ortam değişkeni kullanmak için

- Proje dosyanızda bildirilen bir değişkenle aynı şekilde ortam değişkenine başvurun. Örneğin, aşağıdaki kod BIN_PATH ortamı değişkenine başvurur:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Ortam değişkeni `Condition` ayarlanmadıysa, bir özellik için varsayılan değer sağlamak için bir öznitelik kullanabilirsiniz.

#### <a name="to-provide-a-default-value-for-a-property"></a>Bir özellik için varsayılan değer sağlamak için

- Yalnızca `Condition` özelliğin değeri yoksa değeri ayarlamak için özellik üzerinde bir öznitelik kullanın. Örneğin, aşağıdaki kod `ToolsPath` özelliği yalnızca ortam değişkeni `ToolsPath` ayarlı değilse *c:\tools* olarak ayarlar:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Özellik adları büyük/küçük harf `$(ToolsPath)` `$(TOOLSPATH)` duyarlı değildir, bu nedenle her ikisi de ve aynı özellik veya ortam değişkenine başvurur.

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

- [Msbuild](../msbuild/msbuild.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Nasıl yapılı: Farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
