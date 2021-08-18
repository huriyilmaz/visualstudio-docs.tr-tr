---
title: MSBuild | ile Paralel Olarak Birden Çok Proje MSBuild | Microsoft Docs
description: Birden çok MSBuild daha hızlı derlemek için bunları paralel olarak çalıştırarak kullanabileceğiniz uygulama ayarları hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b6bdbb3efdf836f29307bdf97b21c5a910ef908f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109012"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile paralel olarak birden çok proje MSBuild

Birden çok MSBuild paralel olarak çalıştırarak daha hızlı derlemek için MSBuild'i kullanabilirsiniz. Derlemeleri paralel olarak çalıştırmak için, çok çekirdekli veya birden çok işlemcili bilgisayarda aşağıdaki ayarları kullanırsınız:

- Komut `-maxcpucount` isteminde anahtarı.

- Bir <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> görev üzerinde görev MSBuild.

> [!NOTE]
> Komut **satırına yönelik -verbosity** (**-v**) anahtarı da derleme performansını etkileyebilir. Derleme günlüğü bilginizin ayrıntılılığı sorun giderme için kullanılan ayrıntılı veya tanılama olarak ayarlanırsa derleme performansınız düşebilir. Daha fazla bilgi için [bkz. Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md) [ve Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="-maxcpucount-switch"></a>-maxcpucount Anahtarı

Anahtarını kullanırsanız veya kısaca MSBuild paralel olarakMSBuild.exeişlem sayısını `-maxcpucount` `-m` oluşturabilirsiniz.  Bu işlemler "çalışan işlemleri" olarak da bilinir. Her çalışan işlemi, diğer kullanılabilir işlemciler başka projeler derlemekle aynı anda bir proje oluşturmak için varsa ayrı bir çekirdek veya işlemci kullanır. Örneğin, bu anahtarın "4" değerine ayar MSBuild projeyi derlemek için dört çalışan işlemi oluşturması gerekir.

Anahtarı bir değer belirtmeden dahil ediyorsanız MSBuild işlemci sayısına `-maxcpucount` kadar kullanırsınız.

bu anahtar hakkında daha fazla bilgi için, MSBuild 3.5'te tanıtıldı, [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

Aşağıdaki örnek, MSBuild üç çalışan işlemini kullanma talimatı vemektedir. Bu yapılandırmayı kullanırsanız, MSBuild aynı anda üç proje derlemeniz gerekir.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>BuildInParallel görev parametresi

`BuildInParallel`, bir görev üzerinde isteğe bağlı bir MSBuild parametresidir. değeri `BuildInParallel` olarak (varsayılan `true` değeridir) ayarlanırsa, mümkün olduğunca çok proje oluşturmak için `true` birden çok çalışan işlemi oluşturulur. Bunun doğru çalışması için anahtarın 1'den büyük bir değere ayarlanmış olması ve sistemin en az çift çekirdekli olması veya iki veya daha fazla işlemciye sahip `-maxcpucount` olması gerekir.

Aşağıda, parametresinin nasıl ayarlanmak üzere *microsoft.common.targets* tarafından alınarak bir örnek ve bir örnek `BuildInParallel` ve ardından ve ve ardından alın almaktadır.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje derlemek için birden çok işlemci kullanma](../msbuild/using-multiple-processors-to-build-projects.md)
- [Çok işlemcili günlükleyiciler yazma](../msbuild/writing-multi-processor-aware-loggers.md)
- [C++ derleme paralelliği blog'larını ayarlama](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
