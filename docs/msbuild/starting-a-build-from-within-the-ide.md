---
title: IDE içinden Bir Yapı Başlatma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8c4792590565c027a316ed95abb067faa30f5dc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632127"
---
# <a name="start-a-build-from-within-the-ide"></a>IDE içinden bir yapı başlatın

Özel proje sistemleri, yapılar başlatmak için kullanmanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> gerekir. Bu makalede, bu gereksinimin nedenleri açıklanır ve yordamı özetler.

## <a name="parallel-builds-and-threads"></a>Paralel yapılar ve iş parçacıkları

 Visual Studio, ortak kaynaklara erişim için arabuluculuk gerektiren paralel yapılara izin verir. Proje sistemleri yapıları eş zamanlı olarak çalıştırabilir, ancak bu tür sistemler geri arama içinden yapı işlevleri ni çağırmamalıdır.

 Proje sistemi ortam değişkenlerini değiştirirse, yapının Düğüm'ünü OutOfProc olarak ayarlamalıdır. Bu gereksinim, proc düğümü gerektirdiğinden ana bilgisayar nesnelerini kullanamayacağınız anlamına gelir.

## <a name="use-ivsbuildmanageraccessor"></a>IVSBuildManagerAccessor'u kullanın

 Aşağıdaki kod, proje sisteminin bir yapıyı başlatmak için kullanabileceği bir yöntemi özetleyilmektedir:

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
