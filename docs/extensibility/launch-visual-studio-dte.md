---
title: DTE kullanarak Visual Studio’yu Başlatma
titleSuffix: ''
ms.date: 04/26/2019
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79af14e80ef39b0cad732dcd0c9f37af1481bd4c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590637"
---
# <a name="launch-visual-studio-using-dte"></a>DTE kullanarak Visual Studio’yu Başlatma

Visual Studio 2017 ' den itibaren, DTE 'yi kullanarak Visual Studio 'Yu başlatma mekanizması, Visual Studio 'nun önceki sürümlerini başlatmaya farklıdır. Visual Studio 2017 ve üzeri, ana sürümlerin yan yana yüklemelerini desteklediğinden bu değişiklik gereklidir (örneğin, bir önizleme ve bir sürüm sürümü yan yana yüklü olabilir).

Bu makalenin geri kalanında, Visual Studio 2019 ' i DTE kullanarak başlatmak için kullanabileceğiniz kod gösterilmektedir.

## <a name="set-up-the-project"></a>Projeyi ayarlama

Başlatma kodunu çalıştırmak için, aşağıdaki adımları izleyerek bir proje oluşturun.

1. .NET Framework için yeni bir **konsol uygulaması** projesi oluşturun.

2. [Microsoft. VisualStudio. Setup. Configuration. Interop](https://www.nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop/) NuGet paketini yükleme ve derlemeye bir başvuru ekleme.

3. EnvDTE öğesine bir başvuru ekleyin.

4. Aşağıdaki [örnek kodu](#example-code) *program.cs* dosyasına yapıştırın.

5. Programı çalıştırmak için **F5** tuşuna basın. Program çıkmadan önce Visual Studio 2019 açık ' i görmeniz gerekir.

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
                if (count == 1 &&
                    setupInstances != null &&
                    setupInstances.Length == 1 &&
                    setupInstances[0] != null)
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

            [DllImport("ole32.dll")]
            public static extern void GetRunningObjectTable(int reserved, out IRunningObjectTable prot);
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'Yu bulma](locating-visual-studio.md)
- [İzlenecek yol: bir düzenleyici uzantısından DTE nesnesine erişme](walkthrough-accessing-the-dte-object-from-an-editor-extension.md)
