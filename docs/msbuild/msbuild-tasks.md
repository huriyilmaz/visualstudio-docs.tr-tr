---
title: MSBuild görevleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a6bc01ee1f692a4da0cf1921de757236651a177
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593817"
---
# <a name="msbuild-tasks"></a>MSBuild görevleri
Derleme platformunun, derleme işlemi sırasında herhangi bir sayıda eylemi yürütme yeteneği olması gerekir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bu eylemleri gerçekleştirmek için *görevleri* kullanır. Görev, atomik derleme işlemleri gerçekleştirmek için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından kullanılan çalıştırılabilir kod birimidir.

## <a name="task-logic"></a>Görev mantığı
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] XML proje dosyası biçimi kendi kendine derleme işlemlerini tamamen yürütemiyor, bu nedenle görev mantığının proje dosyası dışında uygulanması gerekir.

 Bir görevin yürütme mantığı, <xref:Microsoft.Build.Framework> ad alanında tanımlanan <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir .NET sınıfı olarak uygulanır.

 Görev sınıfı ayrıca proje dosyasındaki görevin kullanabildiği giriş ve çıkış parametrelerini de tanımlar. Görev sınıfı tarafından sunulan tüm ortak ayarlanabilir statik olmayan Özet olmayan özelliklere, [görev](../msbuild/task-element-msbuild.md) öğesinde aynı ada sahip karşılık gelen bir özniteliği yerleştirerek proje dosyasında erişilebilir.

 <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan yönetilen bir sınıf yazarak kendi görevinizi yazabilirsiniz. Daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Proje dosyasından bir görev yürütme
 Proje dosyanızda bir görevi yürütmeden önce, ilk olarak görevi bir görev adına uygulayan derleme içindeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesiyle eşlemeniz gerekir. Bu, proje dosyanızda bulduğunda görevin yürütme mantığını nerede arayacağı [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bilmesini sağlar.

 Bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasında bir görevi yürütmek için, bir `Target` öğesinin alt öğesi olarak görevin adında bir öğe oluşturun. Bir görev parametreleri kabul ediyorsa, bunlar öğesinin öznitelikleri olarak geçirilir.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] öğe listeleri ve Özellikler parametre olarak kullanılabilir. Örneğin, aşağıdaki kod `MakeDir` görevini çağırır ve `MakeDir` nesnesinin `Directories` özelliğinin değerini, önceki örnekte belirtilen `BuildDir` özelliğinin değerine eşit olarak ayarlar.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Görevler Ayrıca, daha sonra kullanılmak üzere öğeler veya özelliklerde depolanabilecek proje dosyasına bilgi döndürebilir. Örneğin, aşağıdaki kod `Copy` görevini çağırır ve bilgileri `SuccessfullyCopiedFiles` öğesi listesindeki `CopiedFiles` output özelliğinden depolar.

```xml
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
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], [Copy](../msbuild/copy-task.md), dosyaları kopyalayan, dizin oluşturan [makedir](../msbuild/makedir-task.md)ve [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kaynak kodu dosyalarını derlenen [CSC](../msbuild/csc-task.md)gibi birçok görevle birlikte gönderilir. Kullanılabilir görevlerin ve kullanım bilgilerinin tüm listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Geçersiz kılınan görevler
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] birkaç konumdaki görevleri arar. İlk konum uzantılı dosyalardır *.* .NET Framework dizinlerinde depolanan OverrideTasks. Bu dosyalardaki görevler, proje dosyasındaki görevler de dahil olmak üzere, aynı ada sahip diğer tüm görevleri geçersiz kılar. İkinci konum uzantılı dosyalardır *.* .NET Framework dizinlerindeki görevler. Görev bu konumlardan birinde bulunmazsa, proje dosyasındaki görev kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Satır içi görevler](../msbuild/msbuild-inline-tasks.md)
