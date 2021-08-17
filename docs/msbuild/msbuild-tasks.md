---
title: MSBuild Görevler | Microsoft Docs
description: Derleme işlemi MSBuild görevleri veya atomik derleme işlemleri gerçekleştiren yürütülebilir kod birimlerini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 0c32c693e7bbcede9764a7d186607c98a3951668918dc9e2063ecd208f78ca74
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397403"
---
# <a name="msbuild-tasks"></a>MSBuild görevleri

Derleme platformu, derleme işlemi sırasında herhangi bir sayıda eylemi yürütebilmeyi gerektirmektedir. MSBuild eylemleri *gerçekleştirmek* için görevleri kullanır. Görev, MSBuild tarafından atomik derleme işlemleri gerçekleştirmek için kullanılan yürütülebilir kod birimidir.

## <a name="task-logic"></a>Görev mantığı

 Bu MSBuild XML proje dosyası biçimi derleme işlemlerini kendi başına tam olarak yürüte çalışmayamaz, bu nedenle görev mantığının proje dosyasının dışında uygulanması gerekir.

 Bir görevin yürütme mantığı, ad alanı içinde tanımlanan arabirimini uygulayan bir .NET <xref:Microsoft.Build.Framework.ITask> sınıfı olarak <xref:Microsoft.Build.Framework> uygulanır.

 Görev sınıfı ayrıca proje dosyasındaki görev için kullanılabilir giriş ve çıkış parametrelerini tanımlar. Görev sınıfı tarafından gösterilen tüm genel ayarlanamayan statik olmayan soyut özelliklere, Görev öğesinde aynı adla [](../msbuild/task-element-msbuild.md) karşılık gelen bir öznitelik yerleştirerek ve değerini bu makaledeki örneklerde gösterildiği gibi ayararak proje dosyasında değerler verilmiştir.

 Arabirimi uygulayan bir yönetilen sınıf yazarak kendi görevinizi <xref:Microsoft.Build.Framework.ITask> yazabilirsiniz. Daha fazla bilgi için [bkz. Görev yazma.](../msbuild/task-writing.md)

## <a name="execute-a-task-from-a-project-file"></a>Proje dosyasından görev yürütme

 Proje dosyanıza bir görev yürütmeden önce, görevi uygulayan derlemedeki türü [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesiyle görev adıyla eşlemeniz gerekir. Bu MSBuild proje dosyanız içinde bulduğunda görevinizin yürütme mantığını nerede bulanları bilebilirsiniz.

 Bir görev bir proje MSBuild yürütmek için, bir öğenin alt öğesi olarak görevin adıyla bir öğe `Target` oluşturun. Bir görev parametreleri kabul ederse, bunlar öğenin öznitelikleri olarak geçir edilir.

 MSBuild listesi ve özellikleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod görevi `MakeDir` çağırarak nesnesinin `Directories` özelliğinin değerini `MakeDir` özelliğinin değerine eşit olarak `BuildDir` ayarlar:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Görevler, daha sonra kullanmak üzere öğelerde veya özelliklerde depolandırılamayacak şekilde proje dosyasına bilgi de iade ediyor olabilir. Örneğin, aşağıdaki kod görevi `Copy` çağırarak çıkış özelliğinden `CopiedFiles` alınan bilgileri öğe listesinde `SuccessfullyCopiedFiles` depolar.

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

 MSBuild dosyaları kopyalayıp dizin oluşturan [](../msbuild/copy-task.md) [MakeDir](../msbuild/makedir-task.md)ve C# kaynak kodu dosyalarını derleye [Csc](../msbuild/csc-task.md)gibi birçok görevle birlikte gelir. Kullanılabilir görevlerin ve kullanım bilgilerinin tam listesi için bkz. [Görev başvurusu.](../msbuild/msbuild-task-reference.md)

## <a name="overridden-tasks"></a>Geçersiz kılınan görevler

 MSBuild konumlarda görevlere bakabilirsiniz. İlk konum uzantısına sahip *dosyalardadır. .NET Framework* dizinlerde depolanan OverrideTasks. Bu dosyalarda yer alan görevler, proje dosyasındaki görevler de dahil olmak üzere aynı adlara sahip diğer görevleri geçersiz kılar. İkinci konum uzantısına sahip *dosyalardadır. .NET Framework* dizinleri. Görev bu konumlardan herhangi biri içinde bulunamazsa, proje dosyasındaki görev kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Görev yazma](../msbuild/task-writing.md)
- [Satır içi görevleri](../msbuild/msbuild-inline-tasks.md)
