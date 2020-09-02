---
title: 'Nasıl yapılır: bir derlemede ortam değişkenlerini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 72d810f998b111aa2ec08a5874498ed8ee23a3be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793691"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Nasıl Yapılır: Derlemede Ortam Değişkenlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeleri oluştururken, genellikle proje dosyasında veya projenizi oluşturan dosyalarda olmayan bilgileri kullanarak yapı seçeneklerini ayarlamak gerekir. Bu bilgiler genellikle ortam değişkenlerinde depolanır.  
  
## <a name="referencing-environment-variables"></a>Ortam değişkenlerine başvurma  
 Tüm ortam değişkenleri, [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) proje dosyasında özellik olarak kullanılabilir.  
  
> [!NOTE]
> Proje dosyası bir ortam değişkeniyle aynı ada sahip bir özelliğin açık tanımını içeriyorsa, proje dosyasındaki özelliği ortam değişkeninin değerini geçersiz kılar.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>MSBuild projesinde ortam değişkenini kullanmak için  
  
- Ortam değişkenine, proje dosyanızda bildirildiği bir değişkenle aynı şekilde başvurun. Örneğin, aşağıdaki kod BIN_PATH ortam değişkenine başvurur:  
  
   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
  `Condition`Ortam değişkeni ayarlanmamışsa bir özellik için varsayılan değer sağlamak üzere bir özniteliği kullanabilirsiniz.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Bir özellik için varsayılan değer sağlamak için  
  
- `Condition`Yalnızca özelliğin değeri yoksa değeri ayarlamak için özellik üzerinde bir öznitelik kullanın. Örneğin, aşağıdaki kod, `ToolsPath` özelliği yalnızca ortam değişkeni ayarlanmamışsa c:\Tools olarak ayarlar `ToolsPath` :  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    > Özellik adları büyük/küçük harfe duyarlı değildir `$(ToolsPath)` ve `$(TOOLSPATH)` aynı özelliğe veya ortam değişkenine başvurur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki proje dosyası dizinlerin konumunu belirtmek için ortam değişkenlerini kullanır.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  

[MSBUILD](msbuild.md)

[MSBuild özellikleri](../msbuild/msbuild-properties1.md)

[Nasıl Yapılır: Farklı Seçeneklerle Aynı Kaynak Dosyaları Derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
