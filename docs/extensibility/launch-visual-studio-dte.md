---
title: DTE kullanarak Visual Studio’yu Başlatma
description: Ana sürümler Visual Studio yan yana yüklemeleri desteklemek için DTE kullanarak uygulama başlatmayı öğrenin. Bu makale bir kod örneği içerir.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/26/2019
ms.topic: how-to
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3f5aa141d73879e61a06e7a2b19f03bd53243a7
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046033"
---
# <a name="launch-visual-studio-using-dte"></a>DTE kullanarak Visual Studio’yu Başlatma

Visual Studio 2017'den başlayarak DTE kullanarak Visual Studio başlatma mekanizması, DTE'nin önceki sürümlerinin başlatılmasıyla Visual Studio. Visual Studio 2017 ve sonraki sürümler ana sürümlerde yan yana yüklemeleri desteklediği için bu değişiklik gereklidir (örneğin, bir önizleme ve sürüm sürümü yan yana yüklenmiş olabilir).

Bu makalenin geri kalanında, DTE kullanarak 2019'Visual Studio başlatmak için kullanabileceğiniz kodlar açıklanmıştır.

## <a name="set-up-the-project"></a>Projeyi ayarlama

Başlatma kodunun nasıl olduğunu görmek için aşağıdaki adımları izleyin ve bir proje oluşturun.

1. Uygulama için **yeni bir Konsol** Uygulaması .NET Framework.

2. uration [Microsoft.VisualStudio.Setup.Configyükleyin. Birlikte](https://www.nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop/) Çalışma NuGet paketi ve derlemeye bir başvuru ekleyin.

3. EnvDTE'ye bir başvuru ekleyin.

4. Aşağıdaki [örnek kodu](#example-code) *Program.cs dosyasına* yapıştırın.

5. Programı **çalıştırmak için F5** tuşuna basın. Programdan çık Visual Studio önce 2019'un açık olduğunu görüyor gerekir.

## <a name="example-code"></a>Örnek kod

```csharp
using Microsoft.VisualStudio.Setup.Configuration;
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.IO;
using System.Linq;
using System.Runtime.InteropServices;
using System.Runtime.InteropServices.ComTypes;
using System.Threading;

namespace ConsoleLauncherApp
{
    class Program
    {
        static void Main(string[] args)
        {
            EnvDTE.DTE dte = LaunchVsDte(isPreRelease: false);

            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMaximize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateMinimize;
            dte.MainWindow.WindowState = EnvDTE.vsWindowState.vsWindowStateNormal;
            dte.Quit();
        }

        private static EnvDTE.DTE LaunchVsDte(bool isPreRelease)
        {
            ISetupInstance setupInstance = GetSetupInstance(isPreRelease);
            string installationPath = setupInstance.GetInstallationPath();
            string executablePath = Path.Combine(installationPath, @"Common7\IDE\devenv.exe");
            Process vsProcess = Process.Start(executablePath);
            string runningObjectDisplayName = $"VisualStudio.DTE.16.0:{vsProcess.Id}";

            IEnumerable<string> runningObjectDisplayNames = null;
            object runningObject;
            for (int i = 0; i < 60; i++)
            {
                try
                {
                    runningObject = GetRunningObject(runningObjectDisplayName, out runningObjectDisplayNames);
                }
                catch
                {
                    runningObject = null;
                }

                if (runningObject != null)
                {
                    return (EnvDTE.DTE)runningObject;
                }

                Thread.Sleep(millisecondsTimeout: 1000);
            }

            throw new TimeoutException($"Failed to retrieve DTE object. Current running objects: {string.Join(";", runningObjectDisplayNames)}");
        }

        private static object GetRunningObject(string displayName, out IEnumerable<string> runningObjectDisplayNames)
        {
            IBindCtx bindContext = null;
            NativeMethods.CreateBindCtx(0, out bindContext);

            IRunningObjectTable runningObjectTable = null;
            bindContext.GetRunningObjectTable(out runningObjectTable);

            IEnumMoniker monikerEnumerator = null;
            runningObjectTable.EnumRunning(out monikerEnumerator);

            object runningObject = null;
            List<string> runningObjectDisplayNameList = new List<string>();
            IMoniker[] monikers = new IMoniker[1];
            IntPtr numberFetched = IntPtr.Zero;
            while (monikerEnumerator.Next(1, monikers, numberFetched) == 0)
            {
                IMoniker moniker = monikers[0];

                string objectDisplayName = null;
                try
                {
                    moniker.GetDisplayName(bindContext, null, out objectDisplayName);
                }
                catch (UnauthorizedAccessException)
                {
                    // Some ROT objects require elevated permissions.
                }

                if (!string.IsNullOrWhiteSpace(objectDisplayName))
                {
                    runningObjectDisplayNameList.Add(objectDisplayName);
                    if (objectDisplayName.EndsWith(displayName, StringComparison.Ordinal))
                    {
                        runningObjectTable.GetObject(moniker, out runningObject);
                        if (runningObject == null)
                        {
                            throw new InvalidOperationException($"Failed to get running object with display name {displayName}");
                        }
                    }
                }
            }

            runningObjectDisplayNames = runningObjectDisplayNameList;
            return runningObject;
        }

        private static ISetupInstance GetSetupInstance(bool isPreRelease)
        {
            return GetSetupInstances().First(i => IsPreRelease(i) == isPreRelease);
        }

        private static IEnumerable<ISetupInstance> GetSetupInstances()
        {
            ISetupConfiguration setupConfiguration = new SetupConfiguration();
            IEnumSetupInstances enumerator = setupConfiguration.EnumInstances();

            int count;
            do
            {
                ISetupInstance[] setupInstances = new ISetupInstance[1];
                enumerator.Next(1, setupInstances, out count);
                if (count == 1 && setupInstances[0] != null)
                {
                    yield return setupInstances[0];
                }
            }
            while (count == 1);
        }

        private static bool IsPreRelease(ISetupInstance setupInstance)
        {
            ISetupInstanceCatalog setupInstanceCatalog = (ISetupInstanceCatalog)setupInstance;
            return setupInstanceCatalog.IsPrerelease();
        }

        private static class NativeMethods
        {
            [DllImport("ole32.dll")]
            public static extern int CreateBindCtx(uint reserved, out IBindCtx ppbc);
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’yu Bulma](locating-visual-studio.md)
- [Adım adım kılavuz: DTE nesnesine bir düzenleyici uzantısından erişme](walkthrough-accessing-the-dte-object-from-an-editor-extension.md)
