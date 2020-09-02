---
title: Hedef toplu Işleme içindeki öğe meta verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dd6c297e00a305fbd1b13cf0fe0bd4a4f151f6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192867"
---
# <a name="item-metadata-in-target-batching"></a>Toplu Hedef İşlemede Öğe Meta Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bir derleme hedefinin girdileri ve çıkışları üzerinde bağımlılık Analizi gerçekleştirme olanağına sahiptir. Hedefin giriş veya çıkış çıkışları güncel olduğunu tespit ederseniz, hedef atlanır ve derleme devam eder. `Target` öğeler, `Inputs` `Outputs` bağımlılık analizi sırasında incelenecek öğeleri belirtmek için ve özniteliklerini kullanır.  
  
 Bir hedef, giriş veya çıkış olarak toplanmış öğeleri kullanan bir görev içeriyorsa, `Target` hedef öğenin, zaten güncel olan `Inputs` `Outputs` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğelerin toplu işlerini atlamasını sağlamak için veya özniteliklerinde toplu işlem kullanması gerekir.  
  
## <a name="batching-targets"></a>Toplu işleme hedefleri  
 Aşağıdaki örnek, `Res` öğe meta verilerine bağlı olarak iki toplu işlem içine bölünen adlı bir öğe listesi içerir `Culture` . Bu toplu işlerin her biri `AL` göreve geçirilir ve bu, her toplu iş için bir çıkış derlemesi oluşturur. `Outputs`Öğesinin özniteliğinde toplu `Target` işlem kullanarak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hedefi çalıştırmadan önce her bir toplu iş öğesinin güncel olup olmadığını belirleyebilir. Hedef toplu işlem kullanılmadan, her iki öğe de hedef her yürütüldüğünde görev tarafından çalıştırılır.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md)   
 [İşlem](../msbuild/msbuild-batching.md)   
 [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Görev toplu işlem içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md)
