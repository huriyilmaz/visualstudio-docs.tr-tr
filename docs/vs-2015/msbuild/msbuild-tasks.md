---
title: MSBuild görevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 756c19da1aeb8878c2d045f4ee471d8449d2a954
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154809"
---
# <a name="msbuild-tasks"></a>MSBuild Görevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derleme platformunun, derleme işlemi sırasında herhangi bir sayıda eylemi yürütme yeteneği olması gerekir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bu eylemleri gerçekleştirmek için *görevleri* kullanır. Görev, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] atomik derleme işlemleri gerçekleştirmek için tarafından kullanılan yürütülebilir kod birimidir.  
  
## <a name="task-logic"></a>Görev mantığı  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]XML proje dosyası biçimi, derleme işlemlerini kendi kendine tamamen yürütemiyor, bu nedenle görev mantığı proje dosyasının dışında uygulanmalıdır.  
  
 Bir görevin yürütme mantığı, <xref:Microsoft.Build.Framework.ITask> ad alanında tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır <xref:Microsoft.Build.Framework> .  
  
 Görev sınıfı ayrıca proje dosyasındaki görevin kullanabildiği giriş ve çıkış parametrelerini de tanımlar. Görev sınıfı tarafından sunulan tüm ortak ayarlanabilir statik olmayan Özet olmayan özelliklere, [görev](../msbuild/task-element-msbuild.md) öğesinde aynı ada sahip karşılık gelen bir özniteliği yerleştirerek proje dosyasında erişilebilir.  
  
 Arabirimini uygulayan yönetilen bir sınıf yazarak kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> . Daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Proje dosyasından bir görevi yürütme  
 Proje dosyanızda bir görevi yürütmeden önce, ilk olarak görevi bir görev adına uygulayan derleme içindeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesiyle eşlemeniz gerekir. Bu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , proje dosyanızda bulduğunda görevin yürütme mantığını nerede bulacağını öğrenmenizi sağlar.  
  
 Bir proje dosyasında bir görevi yürütmek için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bir öğenin alt öğesi olarak görevin adında bir öğe oluşturun `Target` . Bir görev parametreleri kabul ediyorsa, bunlar öğesinin öznitelikleri olarak geçirilir.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] öğe listeleri ve Özellikler parametre olarak kullanılabilir. Örneğin, aşağıdaki kod `MakeDir` görevi çağırır ve `Directories` nesnenin özelliğinin değerini, `MakeDir` `BuildDir` Önceki örnekte belirtilen özelliğin değerine eşit olarak ayarlar.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Görevler Ayrıca, daha sonra kullanılmak üzere öğeler veya özelliklerde depolanabilecek proje dosyasına bilgi döndürebilir. Örneğin, aşağıdaki kod `Copy` görevi çağırır ve bilgileri `CopiedFiles` öğe listesindeki çıkış özelliğinden depolar `SuccessfullyCopiedFiles` .  
  
```  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Dahil edilen görevler  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)][, dosyaları](../msbuild/makedir-task.md)kopyalayan ve kaynak kodu dosyalarını derleyen, dizin oluşturan ve [CSC](../msbuild/csc-task.md)adlı, [kopyalama](../msbuild/copy-task.md)gibi birçok görevle birlikte gelir [!INCLUDE[csprcs](../includes/csprcs-md.md)] . Kullanılabilir görevlerin ve kullanım bilgilerinin tüm listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Geçersiz kılınan görevler  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] birkaç konumdaki görevleri arar. İlk konum uzantılı dosyalardır. .NET Framework dizinlerinde depolanan OverrideTasks. Bu dosyalardaki görevler, proje dosyasındaki görevler de dahil olmak üzere, aynı ada sahip diğer tüm görevleri geçersiz kılar. İkinci konum uzantılı dosyalardır. .NET Framework dizinlerindeki görevler. Görev bu konumlardan birinde bulunmazsa, proje dosyasındaki görev kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBUILD](msbuild.md)   
 [Görev yazma](../msbuild/task-writing.md)   
 [Satır içi görevler](../msbuild/msbuild-inline-tasks.md)
