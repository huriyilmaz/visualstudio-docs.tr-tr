---
title: MSBuild Toplu Işleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799402"
---
# <a name="msbuild-batching"></a>MSBuild Toplu İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listelerini, öğe meta verilerine göre farklı kategorilere veya toplu işlemlere bölebilir ve her Batch ile bir kez hedef veya görev çalıştırabilir.  
  
## <a name="task-batching"></a>Görev toplu Işleme  
 Görev toplu işleme, öğe listelerini farklı toplu işlemlere bölmek ve bu toplu işlerin her birini ayrı bir göreve geçirmek için bir yol sağlayarak Proje dosyalarınızı basitleştirmenize olanak tanır. Bu, bir proje dosyasının, birkaç kez çalıştırılabilse de, yalnızca görevin ve özniteliklerinin bir kez bildirilmesine ihtiyaç duyacağı anlamına gelir.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Görev özniteliklerinden birindeki%(*ItemMetaDataName*) gösterimini kullanarak bir görevle toplu işlem gerçekleştirmek istediğinizi belirtirsiniz. Aşağıdaki örnek, öğe `Example` listesini `Color` öğe meta veri değerine göre toplu işlemlere böler ve toplu işlerin her birini `MyTask` göreve ayrı geçirir.  
  
> [!NOTE]
> Görev özniteliklerinin başka bir yerinde öğe listesine başvurmayın veya meta veri adı belirsiz olabilir, toplu işleme için kullanılacak öğe meta verileri değerini tamamen nitelemek için%(*ItemCollection. ItemMetaDataName*) gösterimini kullanabilirsiniz.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Daha özel toplu işlem örnekleri için bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Hedef toplu Işleme  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Hedefin giriş ve çıkışları hedefi çalıştırmadan önce güncel olup olmadığını denetler. Hem giriş hem de çıkış güncel ise, hedef atlanır. Bir hedefin içindeki bir görev toplu işlem kullanıyorsa, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] her öğe için giriş ve çıktıların güncel olup olmadığını belirlemesi gerekir. Aksi takdirde, hedef her isabet edildiğinde yürütülür.  
  
 Aşağıdaki örnek, `Target` `Outputs` %(*ItemMetaDataName*) gösterimiyle bir özniteliği içeren bir öğesini gösterir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listesini, `Example` öğe meta verileri temelinde toplu işlemlere böler `Color` ve her toplu iş için çıkış dosyalarının zaman damgalarını analiz eder. Bir toplu işteki çıktılar güncel değilse, hedef çalıştırılır. Aksi takdirde, hedef atlanır.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Hedef toplu işleme bir örnek için bkz. [hedef toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Meta verileri kullanan özellik Işlevleri  
 Toplu işlem, meta veri içeren özellik işlevleri tarafından denetlenebilir. Örneğin,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 <xref:System.IO.Path.Combine%2A>bir kök klasör yolunu derleme öğesi yoluyla birleştirmek için kullanır.  
  
 Özellik işlevleri, meta veri değerleri içinde görünmeyebilir.  Örneğin,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 izin verilmiyor.  
  
 Özellik işlevleri hakkında daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
