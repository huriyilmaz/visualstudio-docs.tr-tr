---
title: IDE içinden derleme başlatma | Microsoft Docs
description: Özel proje sistemleri için yapıları başlatmak üzere Microsoft. VisualStudio. Shell. Interop. IVsBuildManagerAccessor kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e8c13ca9d8c5cbbb42e11ca9c17d4c5b1381dcba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093638"
---
# <a name="start-a-build-from-within-the-ide"></a>IDE içinden derleme başlatma

Özel proje sistemleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> yapıları başlatmak için kullanılmalıdır. Bu makalede, bu gereksinimin nedenleri açıklanmaktadır ve yordam özetlenmektedir.

## <a name="parallel-builds-and-threads"></a>Paralel derlemeler ve iş parçacıkları

 Visual Studio, genel kaynaklara erişim için ortam gerektiren paralel derlemelere izin verir. Project sistemler derlemeleri zaman uyumsuz olarak çalıştırabilir, ancak bu tür sistemler, çağrı geri göndermeler içerisinden derleme işlevlerini çağırmamalıdır.

 Proje sistemi ortam değişkenlerini değiştirirse, derleme için Nodebenzeşimini OutOfProc olarak ayarlaması gerekir. Bu gereksinim, işlem içi düğümü gerektirdiğinden ana bilgisayar nesnelerini kullanamayacağı anlamına gelir.

## <a name="use-ivsbuildmanageraccessor"></a>IVsBuildManagerAccessor kullanın

 Aşağıdaki kod, bir proje sisteminin bir derlemeyi başlatmak için kullanabileceği bir yöntemi özetler:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```
