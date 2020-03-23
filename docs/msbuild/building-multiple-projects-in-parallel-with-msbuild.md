---
title: MSBuild ile Paralel Olarak Birden Fazla Proje Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1723fba810450fe5e31a43d63f3704ab74f455f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634506"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile paralel olarak birden fazla proje oluşturun

MSBuild'i, birden çok projeyi paralel olarak çalıştırarak daha hızlı oluşturmak için kullanabilirsiniz. Yapıları paralel olarak çalıştırmak için, çok çekirdekli veya birden çok işlemcili bilgisayarda aşağıdaki ayarları kullanırsınız:

- Komut `-maxcpucount` istemindeki anahtar.

- MSBuild <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> görevindegörev parametresi.

> [!NOTE]
> Komut satırındaki **-ayrıntılı (** **-v**) anahtarı da yapı performansını etkileyebilir. Yapı günlüğü bilgilerinizin ayrıntılı veya tanısal olarak ayarlandığı ve sorun giderme için kullanıldığında yapı performansınız düşebilir. Daha fazla bilgi için [bkz.](../msbuild/obtaining-build-logs-with-msbuild.md) [Command-line reference](../msbuild/msbuild-command-line-reference.md)

## <a name="-maxcpucount-switch"></a>-maxcpucount Anahtarı

`-maxcpucount` Anahtarı kullanırsanız veya `-m` kısaca MSBuild, paralel olarak çalıştırılabilecek belirtilen sayıda *MSBuild.exe* işlemi oluşturabilir. Bu işlemler "alt işlemler" olarak da bilinir. Her alt işlem, varsa, diğer kullanılabilir işlemciler diğer projeler oluşturmak olabilir aynı anda bir proje oluşturmak için ayrı bir çekirdek veya işlemci kullanır. Örneğin, bu anahtarı "4" değerine ayarlamak, MSBuild'in projeyi oluşturmak için dört alt işlem oluşturmasına neden olur.

`-maxcpucount` Bir değer belirtmeden anahtarı eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır.

MSBuild 3.5'te tanıtılan bu anahtar hakkında daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

Aşağıdaki örnek, MSBuild'e üç alt işlem kullanmasını bildirir. Bu yapılandırmayı kullanırsanız, MSBuild aynı anda üç proje oluşturabilir.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>YapıParalel görev parametresi

`BuildInParallel`MSBuild görevinde isteğe bağlı bir boolean parametresitir. (Varsayılan değeri) `BuildInParallel` `true` `true`ayarlandığında, mümkün olduğunca çok proje oluşturmak için birden çok alt işlem oluşturulur. Bunun doğru çalışması için `-maxcpucount` anahtarın 1'den büyük bir değere ayarlanabilmesi ve sistemin en az çift çekirdekli olması veya iki veya daha fazla işlemciye sahip olması gerekir.

Aşağıda, parametrenin nasıl ayarlanıla ilgili *microsoft.common.targets*adresinden `BuildInParallel` alınan bir örnek verilmiştir.

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

- [Projeler oluşturmak için birden çok işlemci kullanın](../msbuild/using-multiple-processors-to-build-projects.md)
- [Çok işlemcili bilgine duyarlı kaydediciler yazma](../msbuild/writing-multi-processor-aware-loggers.md)
- [Tuning C++ paralellik blogu oluşturmak](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
