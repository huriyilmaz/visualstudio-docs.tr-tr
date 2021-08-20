---
title: MSBuild Görevler | Microsoft Docs
description: oluşturma işlemi sırasında MSBuild görevleri veya atomik derleme işlemlerini gerçekleştiren yürütülebilir kod birimlerini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 949429136da49e562f6c7f24cb78391a0ceb021e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108622"
---
# <a name="msbuild-tasks"></a>MSBuild görevleri

Derleme platformunun, derleme işlemi sırasında herhangi bir sayıda eylemi yürütme yeteneği olması gerekir. MSBuild, bu eylemleri gerçekleştirmek için *görevleri* kullanır. görev, atomik derleme işlemleri gerçekleştirmek için MSBuild tarafından kullanılan çalıştırılabilir kod birimidir.

## <a name="task-logic"></a>Görev mantığı

 MSBuild XML proje dosyası biçimi kendi kendine derleme işlemlerini tamamen yürütemiyor, bu nedenle görev mantığının proje dosyası dışında uygulanması gerekir.

 Bir görevin yürütme mantığı, <xref:Microsoft.Build.Framework.ITask> ad alanında tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır <xref:Microsoft.Build.Framework> .

 Görev sınıfı ayrıca proje dosyasındaki görevin kullanabildiği giriş ve çıkış parametrelerini de tanımlar. Görev sınıfı tarafından kullanıma sunulan tüm ortak ayarlanabilir statik olmayan özellik, [görev](../msbuild/task-element-msbuild.md) öğesinde aynı ada sahip karşılık gelen bir özniteliği yerleştirerek proje dosyasındaki değerler verilebilir ve bu makalede daha sonra örneklerde gösterildiği gibi değeri ayarlayabilirsiniz.

 Arabirimini uygulayan yönetilen bir sınıf yazarak kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> . Daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Proje dosyasından bir görev yürütme

 Proje dosyanızda bir görevi yürütmeden önce, ilk olarak görevi bir görev adına uygulayan derleme içindeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesiyle eşlemeniz gerekir. bu, proje dosyanızda bulduğunda görevin yürütme mantığını nerede arayacağı MSBuild bilmesini sağlar.

 bir MSBuild proje dosyasında bir görevi yürütmek için, bir öğenin alt öğesi olarak görevin adında bir öğe oluşturun `Target` . Bir görev parametreleri kabul ediyorsa, bunlar öğesinin öznitelikleri olarak geçirilir.

 MSBuild öğe listeleri ve özellikler parametre olarak kullanılabilir. Örneğin, aşağıdaki kod `MakeDir` görevi çağırır ve `Directories` nesnenin özelliğinin değerini `MakeDir` özelliğin değerine eşit olarak ayarlar `BuildDir` :

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Görevler Ayrıca, daha sonra kullanılmak üzere öğeler veya özelliklerde depolanabilecek proje dosyasına bilgi döndürebilir. Örneğin, aşağıdaki kod `Copy` görevi çağırır ve bilgileri `CopiedFiles` öğe listesindeki çıkış özelliğinden depolar `SuccessfullyCopiedFiles` .

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

 MSBuild, [Copy](../msbuild/copy-task.md), dosyaları kopyalayan, dizin oluşturan [makedir](../msbuild/makedir-task.md)ve C# kaynak kodu dosyalarını derlenen [Csc](../msbuild/csc-task.md)gibi birçok görevle birlikte gönderilir. Kullanılabilir görevlerin ve kullanım bilgilerinin tüm listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Geçersiz kılınan görevler

 MSBuild birkaç konumdaki görevleri arar. İlk konum uzantılı dosyalardır *.*.NET Framework dizinlerinde depolanan overridetasks. Bu dosyalardaki görevler, proje dosyasındaki görevler de dahil olmak üzere, aynı ada sahip diğer tüm görevleri geçersiz kılar. İkinci konum uzantılı dosyalardır *.*.NET Framework dizinlerindeki görevler. Görev bu konumlardan birinde bulunmazsa, proje dosyasındaki görev kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Satır içi görevleri](../msbuild/msbuild-inline-tasks.md)
