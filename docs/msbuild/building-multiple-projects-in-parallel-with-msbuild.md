---
title: MSBuild ile paralel olarak birden çok proje oluşturma | Microsoft Docs
description: Birden çok projeyi paralel olarak çalıştırarak daha hızlı bir şekilde oluşturmak için kullanabileceğiniz MSBuild ayarları hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: c8e90a649a11933e4281140299bf9ee1b564a212
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939636"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile paralel olarak birden çok proje oluşturun

MSBuild 'i paralel olarak çalıştırarak birden çok projeyi daha hızlı derlemek için kullanabilirsiniz. Yapıları paralel olarak çalıştırmak için, birden çok çekirdekli veya birden çok işlemci bilgisayarında aşağıdaki ayarları kullanın:

- `-maxcpucount`Komut isteminde anahtar.

- <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>MSBuild görevinde görev parametresi.

> [!NOTE]
> Bir komut satırındaki **-ayrıntı** (**-v**) anahtarı derleme performansını da etkileyebilir. Derleme günlüğü bilgilerinizin ayrıntı düzeyi ayrıntılı veya tanılama olarak ayarlandıysa, sorun giderme için kullanılan derleme performanslarınız azalabilir. Daha fazla bilgi için bkz. [Derleme günlüklerini](../msbuild/obtaining-build-logs-with-msbuild.md) ve [komut satırı başvurusunu](../msbuild/msbuild-command-line-reference.md)alma.

## <a name="-maxcpucount-switch"></a>-maxcpucount anahtarı

`-maxcpucount`Anahtarı kullanırsanız veya kısaca, MSBuild, `-m` paralel olarak çalıştırılabilen belirtilen *MSBuild.exe* işlem sayısını oluşturabilir. Bu süreçler "çalışan süreçler" olarak da bilinir. Her çalışan işlemi varsa ayrı bir çekirdek veya işlemciyi, varsa diğer kullanılabilir işlemcilerle aynı anda bir proje oluşturmak için kullanır. Örneğin, bu anahtarın "4" değerine ayarlanması, MSBuild 'in projeyi derlemek için dört çalışan işlem oluşturmasına neden olur.

`-maxcpucount`Anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır.

MSBuild 3,5 ' de tanıtılan bu anahtar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

Aşağıdaki örnek, MSBuild 'in üç çalışan işlemi kullanmasını söyler. Bu yapılandırmayı kullanırsanız, MSBuild aynı anda üç proje oluşturabilir.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>BuildInParallel görev parametresi

`BuildInParallel` , MSBuild görevinde isteğe bağlı bir Boole parametresidir. Ne zaman `BuildInParallel` `true` (varsayılan değer) olarak ayarlandığında `true` , mümkün olduğunca çok sayıda proje oluşturmak için birden fazla çalışan işlemi oluşturulur. Bunun düzgün çalışması için, `-maxcpucount` anahtarın 1 ' den büyük bir değere ayarlanması ve sistemin en az çift çekirdekli olması veya iki ya da daha fazla işlemcisi olması gerekir.

Aşağıda, parametresinin nasıl ayarlanacağı hakkında *Microsoft. Common. targets*'tan alınan bir örnek verilmiştir `BuildInParallel` .

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

- [Projeleri derlemek için birden çok işlemci kullanma](../msbuild/using-multiple-processors-to-build-projects.md)
- [Multi-Processor-Aware Günlükçüler yazma](../msbuild/writing-multi-processor-aware-loggers.md)
- [C++ derleme paralellik blogu ayarlama](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
