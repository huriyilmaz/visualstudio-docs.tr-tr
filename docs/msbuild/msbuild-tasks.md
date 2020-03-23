---
title: MSBuild Görevleri | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633141"
---
# <a name="msbuild-tasks"></a>MSBuild görevleri

Bir yapı platformu, yapı işlemi sırasında herhangi bir sayıda eylemi yürütmek için gereken yeteneği gerekir. MSBuild bu eylemleri gerçekleştirmek için *görevleri* kullanır. Görev, MSBuild tarafından atomik yapı işlemlerini gerçekleştirmek için kullanılan yürütülebilir kod birimidir.

## <a name="task-logic"></a>Görev mantığı

 MSBuild XML proje dosyası biçimi yapı işlemlerini tam olarak yürütemez, bu nedenle görev mantığı proje dosyasının dışında uygulanmalıdır.

 Bir görevin yürütme mantığı, <xref:Microsoft.Build.Framework.ITask> <xref:Microsoft.Build.Framework> ad alanında tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.

 Görev sınıfı, proje dosyasındaki göreviçin kullanılabilir giriş ve çıktı parametrelerini de tanımlar. Görev sınıfı tarafından açığa çıkarılan tüm genel ayarlanan statik olmayan soyut olmayan özellikler, [Görev](../msbuild/task-element-msbuild.md) öğesine aynı ada sahip karşılık gelen bir öznitelik yerleştirerek ve değerini bu makalede daha sonraki örneklerde gösterildiği gibi ayarlayarak proje dosyasında değerler verilebilir.

 <xref:Microsoft.Build.Framework.ITask> Arabirimi uygulayan yönetilen bir sınıf yazarak kendi görevinizi yazabilirsiniz. Daha fazla bilgi için [Görev yazısına](../msbuild/task-writing.md)bakın.

## <a name="execute-a-task-from-a-project-file"></a>Proje dosyasından görev yürütme

 Proje dosyanızda bir görev yürütmeden önce, önce görevi uygulayan derlemedeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi yle görev adına eşlemeniz gerekir. Bu, MSBuild'in proje dosyanızda bulduğunda görevin yürütme mantığını nerede arayacağını bilmesini sağlar.

 MSBuild proje dosyasındaki bir görevi yürütmek için, bir `Target` öğenin alt öğesi olarak görevin adını içeren bir öğe oluşturun. Bir görev parametreleri kabul ederse, bunlar öğenin öznitelikleri olarak geçirilir.

 MSBuild madde listeleri ve özellikleri parametre olarak kullanılabilir. Örneğin, aşağıdaki `MakeDir` kod görevi çağırır ve `Directories` `MakeDir` nesnenin özelliğinin değerini `BuildDir` özelliğin değerine eşit ayarlar:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Görevler, bilgileri, daha sonra kullanılmak üzere öğelerde veya özelliklerde depolanabilecek proje dosyasına da döndürebilir. Örneğin, aşağıdaki kod `Copy` görevi çağırır ve `CopiedFiles` çıktı özelliğindeki bilgileri `SuccessfullyCopiedFiles` madde listesinde depolar.

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

 MSBuild, dosyaları kopyalayan [Kopya,](../msbuild/copy-task.md)Dizinler oluşturan [MakeDir](../msbuild/makedir-task.md)ve C# kaynak kod dosyalarını derleyen [Csc](../msbuild/csc-task.md)gibi birçok görevi içeren gemileroluşturur. Kullanılabilir görevlerin ve kullanım bilgilerinin tam listesi için [Görev başvurusuna](../msbuild/msbuild-task-reference.md)bakın.

## <a name="overridden-tasks"></a>Geçersiz kılınan görevler

 MSBuild çeşitli konumlardaki görevleri arar. İlk konum uzantılı dosyalarda. * *.NET Framework dizinlerinde depolanan OverrideGörevleri. Bu dosyalardaki görevler, proje dosyasındaki görevler de dahil olmak üzere aynı adlarla diğer görevleri geçersiz kılar. İkinci konum uzantısı ile dosyalarda. * *.NET Framework dizinlerinde görevler. Görev bu konumlardan herhangi birinde bulunmazsa, proje dosyasındaki görev kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Satır İçi görevler](../msbuild/msbuild-inline-tasks.md)
