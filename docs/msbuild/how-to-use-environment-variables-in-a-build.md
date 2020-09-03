---
title: 'Nasıl yapılır: bir derlemede ortam değişkenlerini kullanma | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633791"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Nasıl yapılır: bir derlemede ortam değişkenlerini kullanma

Projeleri oluştururken, genellikle proje dosyasında veya projenizi oluşturan dosyalarda olmayan bilgileri kullanarak yapı seçeneklerini ayarlamak gerekir. Bu bilgiler genellikle ortam değişkenlerinde depolanır.

## <a name="reference-environment-variables"></a>Başvuru ortamı değişkenleri

 Tüm ortam değişkenleri, özellikler olarak Microsoft Build Engine (MSBuild) proje dosyasında kullanılabilir.

> [!NOTE]
> Proje dosyası bir ortam değişkeniyle aynı ada sahip bir özelliğin açık tanımını içeriyorsa, proje dosyasındaki özelliği ortam değişkeninin değerini geçersiz kılar.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>MSBuild projesinde ortam değişkenini kullanmak için

- Ortam değişkenine, proje dosyanızda bildirildiği bir değişkenle aynı şekilde başvurun. Örneğin, aşağıdaki kod BIN_PATH ortam değişkenine başvurur:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  `Condition`Ortam değişkeni ayarlanmamışsa bir özellik için varsayılan değer sağlamak üzere bir özniteliği kullanabilirsiniz.

#### <a name="to-provide-a-default-value-for-a-property"></a>Bir özellik için varsayılan değer sağlamak için

- `Condition`Yalnızca özelliğin değeri yoksa değeri ayarlamak için özellik üzerinde bir öznitelik kullanın. Örneğin, aşağıdaki kod, `ToolsPath` özelliği yalnızca ortam değişkeni ayarlanmamışsa *c:\Tools* olarak ayarlar `ToolsPath` :

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Özellik adları büyük/küçük harfe duyarlı değildir `$(ToolsPath)` ve `$(TOOLSPATH)` aynı özelliğe veya ortam değişkenine başvurur.

## <a name="example"></a>Örnek

 Aşağıdaki proje dosyası dizinlerin konumunu belirtmek için ortam değişkenlerini kullanır.

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

- [MSBUILD](../msbuild/msbuild.md)
- [MSBuild özellikleri](../msbuild/msbuild-properties.md)
- [Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
