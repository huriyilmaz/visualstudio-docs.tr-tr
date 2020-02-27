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
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633141"
---
# <a name="msbuild-tasks"></a>MSBuild görevleri

Derleme platformunun, derleme işlemi sırasında herhangi bir sayıda eylemi yürütme yeteneği olması gerekir. MSBuild, bu eylemleri gerçekleştirmek için *Görevler* kullanır. Bir görev, atomik derleme işlemleri gerçekleştirmek için MSBuild tarafından kullanılan yürütülebilir kod birimidir.

## <a name="task-logic"></a>Görev mantığı

 MSBuild XML proje dosyası biçimi, derleme işlemlerini kendi kendine tamamen yürütemiyor, bu nedenle görev mantığı proje dosyasının dışında uygulanmalıdır.

 Bir görevin yürütme mantığı, <xref:Microsoft.Build.Framework> ad alanında tanımlanan <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir .NET sınıfı olarak uygulanır.

 Görev sınıfı ayrıca proje dosyasındaki görevin kullanabildiği giriş ve çıkış parametrelerini de tanımlar. Görev sınıfı tarafından kullanıma sunulan tüm ortak ayarlanabilir statik olmayan özellik, [görev](../msbuild/task-element-msbuild.md) öğesinde aynı ada sahip karşılık gelen bir özniteliği yerleştirerek proje dosyasındaki değerler verilebilir ve bu makalede daha sonra örneklerde gösterildiği gibi değeri ayarlayabilirsiniz.

 <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan yönetilen bir sınıf yazarak kendi görevinizi yazabilirsiniz. Daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Proje dosyasından bir görev yürütme

 Proje dosyanızda bir görevi yürütmeden önce, ilk olarak görevi bir görev adına uygulayan derleme içindeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesiyle eşlemeniz gerekir. Bu, MSBuild 'in, proje dosyanızda bulduğunda görevin yürütme mantığını nerede arayacağı hakkında bilgi verir.

 Bir MSBuild proje dosyasında bir görevi yürütmek için, bir `Target` öğesinin alt öğesi olarak görevin adında bir öğe oluşturun. Bir görev parametreleri kabul ediyorsa, bunlar öğesinin öznitelikleri olarak geçirilir.

 MSBuild öğe listeleri ve özellikleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod `MakeDir` görevini çağırır ve `BuildDir` özelliğinin değerine eşit `MakeDir` nesnesinin `Directories` özelliğinin değerini ayarlar:

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

 MSBuild, [Copy](../msbuild/copy-task.md), dosyaları kopyalayan, dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve kaynak kodu dosyalarını derlenen C# [CSC](../msbuild/csc-task.md)gibi birçok görevle birlikte gönderilir. Kullanılabilir görevlerin ve kullanım bilgilerinin tüm listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Geçersiz kılınan görevler

 MSBuild, çeşitli konumlarda görevler arar. İlk konum uzantılı dosyalardır *.* .NET Framework dizinlerinde depolanan OverrideTasks. Bu dosyalardaki görevler, proje dosyasındaki görevler de dahil olmak üzere, aynı ada sahip diğer tüm görevleri geçersiz kılar. İkinci konum uzantılı dosyalardır *.* .NET Framework dizinlerindeki görevler. Görev bu konumlardan birinde bulunmazsa, proje dosyasındaki görev kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Satır içi görevler](../msbuild/msbuild-inline-tasks.md)
