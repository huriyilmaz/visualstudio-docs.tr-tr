---
title: MSBuild ile paralel olarak birden çok proje oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f80f0898167de133d78d27d26f97d0ab8ced0b31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843947"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile Paralel Olarak Birden Çok Proje Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild 'i paralel olarak çalıştırarak birden çok projeyi daha hızlı derlemek için kullanabilirsiniz. Yapıları paralel olarak çalıştırmak için, birden çok çekirdekli veya birden çok işlemci bilgisayarında aşağıdaki ayarları kullanın:  
  
- `/maxcpucount`Komut isteminde anahtar.  
  
- <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>MSBuild görevinde görev parametresi.  
  
> [!NOTE]
> Bir komut satırındaki **/ayrıntı** (**/v**) anahtarı derleme performansını da etkileyebilir. Derleme günlüğü bilgilerinizin ayrıntı düzeyi ayrıntılı veya tanılama olarak ayarlandıysa, sorun giderme için kullanılan derleme performanslarınız azalabilir. Daha fazla bilgi için bkz. [derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)alma.  
  
## <a name="maxcpucount-switch"></a>/maxcpucount Anahtarı  
 `/maxcpucount`Anahtarı kullanırsanız veya kısaca, MSBuild, `/m` paralel olarak çalıştırılabilen belirtilen MSBuild.exe işlem sayısını oluşturabilir. Bu süreçler "çalışan süreçler" olarak da bilinir. Her çalışan işlemi varsa ayrı bir çekirdek veya işlemciyi, varsa diğer kullanılabilir işlemcilerle aynı anda bir proje oluşturmak için kullanır. Örneğin, bu anahtarın "4" değerine ayarlanması, MSBuild 'in projeyi derlemek için dört çalışan işlem oluşturmasına neden olur.  
  
 `/maxcpucount`Anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır.  
  
 MSBuild 3,5 ' de tanıtılan bu anahtar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki örnek, MSBuild 'in üç çalışan işlemi kullanmasını söyler. Bu yapılandırmayı kullanırsanız, MSBuild aynı anda üç proje oluşturabilir.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>BuildInParallel Görev Parametresi  
 `BuildInParallel` , bir görevde isteğe bağlı bir Boole parametresidir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . , `BuildInParallel` `true` (Varsayılan değeri) olarak ayarlandığında, mümkün olduğunca fazla proje oluşturmak için birden çok çalışan işlemi oluşturulur. Bunun düzgün çalışması için, `/maxcpucount` anahtarın 1 ' den büyük bir değere ayarlanması ve sistemin en az çift çekirdekli olması veya iki ya da daha fazla işlemcisi olması gerekir.  
  
 Aşağıda, parametresinin nasıl ayarlanacağı hakkında Microsoft. Common. targets 'tan alınan bir örnek verilmiştir `BuildInParallel` .  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeleri derlemek için birden çok Işlemci kullanma](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Çok Işlemcili oturum defterleri yazma](../msbuild/writing-multi-processor-aware-loggers.md)   
 [C++ derleme paralellik blogu ayarlama](https://blogs.msdn.com/b/visualstudio/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)
