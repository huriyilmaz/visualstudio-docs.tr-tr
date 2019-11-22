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
ms.openlocfilehash: 2d9efcd218b887187709b38b5f8bcae12c53de59
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300410"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>MSBuild ile Paralel Olarak Birden Çok Proje Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild 'i paralel olarak çalıştırarak birden çok projeyi daha hızlı derlemek için kullanabilirsiniz. Yapıları paralel olarak çalıştırmak için, birden çok çekirdekli veya birden çok işlemci bilgisayarında aşağıdaki ayarları kullanın:  
  
- Bir komut isteminde `/maxcpucount` anahtarı.  
  
- MSBuild görevinde <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> Task parametresi.  
  
> [!NOTE]
> Bir komut satırındaki **/ayrıntı** ( **/v**) anahtarı derleme performansını da etkileyebilir. Derleme günlüğü bilgilerinizin ayrıntı düzeyi ayrıntılı veya tanılama olarak ayarlandıysa, sorun giderme için kullanılan derleme performanslarınız azalabilir. Daha fazla bilgi için bkz. [derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)alma.  
  
## <a name="maxcpucount-switch"></a>/maxcpucount Anahtarı  
 `/maxcpucount` anahtarını kullanırsanız veya Short için `/m`, MSBuild, paralel olarak çalıştırılabilecek belirtilen sayıda MSBuild. exe işlemi oluşturabilir. Bu süreçler "çalışan süreçler" olarak da bilinir. Her çalışan işlemi varsa ayrı bir çekirdek veya işlemciyi, varsa diğer kullanılabilir işlemcilerle aynı anda bir proje oluşturmak için kullanır. Örneğin, bu anahtarın "4" değerine ayarlanması, MSBuild 'in projeyi derlemek için dört çalışan işlem oluşturmasına neden olur.  
  
 `/maxcpucount` anahtarını bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır.  
  
 MSBuild 3,5 ' de tanıtılan bu anahtar hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki örnek, MSBuild 'in üç çalışan işlemi kullanmasını söyler. Bu yapılandırmayı kullanırsanız, MSBuild aynı anda üç proje oluşturabilir.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>BuildInParallel Görev Parametresi  
 `BuildInParallel`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevinde isteğe bağlı bir Boolean parametredir. `BuildInParallel` `true` (varsayılan değeri) olarak ayarlandığında, mümkün olduğunca fazla proje oluşturmak için birden çok çalışan işlemi oluşturulur. Bunun düzgün çalışması için `/maxcpucount` anahtarı 1 ' den büyük bir değere ayarlanmalıdır ve sistem en az çift çekirdekli ya da iki veya daha fazla işlemciye sahip olmalıdır.  
  
 Aşağıda, `BuildInParallel` parametresinin nasıl ayarlanacağı hakkında Microsoft. Common. targets 'tan alınan bir örnek verilmiştir.  
  
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
 [Projeleri derlemek Için birden çok Işlemci kullanma](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Çok işlemcili, oturum defterleri yazma](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Derleme C++ paralelliği blogu ayarlama](https://go.microsoft.com/fwlink/?LinkId=251457)
