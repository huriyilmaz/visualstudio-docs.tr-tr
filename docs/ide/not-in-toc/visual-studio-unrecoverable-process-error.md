---
title: İşlem kurtarılamaz bir hatayla karşılaştı
description: İşlemlerin normal işlemleri sırasında kurtarılamaz hatalarla karşılaşan işlemler hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 97cd6a5d85cd35c4365d9a71c97b8b2d20e05153
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078225"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio kurtarılamaz işlem hatası

Visual Studio birim testi, kod çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç yordam dışında işlem kullanır. Bu işlemler, uzun, kaynak kullanımı Visual Studio daha hızlı yanıt verme gibi Visual Studio sağlamak için yordam dışı çalışır. Ayrıca, Visual Studio 32 bitlik bir işlem olduğundan, işlem dışında çalışan işlemler yoğun bellek kullanımına sahip iş için çalıştıracak daha büyük bir bellek alanı sağlar.

Herhangi *ServiceHub.RoslynCodeAnalysisService.exe* *ServiceHub.RoslynCodeAnalysisService32.exe* bir nedenle sona ererse, aşağıdaki iletiyle birlikte bir açılır bilgi çubuğu görüntülenir:

**"Ne yazık ki, Visual Studio tarafından kullanılan bir işlem kurtarılamaz bir hatayla karşılaştı. Çalışmanızı kaydetmenizi ve ardından çalışmanızı kapatıp yeniden başlatmanızı Visual Studio."**

Bu iletiyi görüyorsanız, çalışmanızı kaydetmeli ve ardından çalışmanızı kapatıp yeniden Visual Studio.

## <a name="list-of-processes"></a>İşlemlerin listesi

Aşağıda, Visual Studio tarafından kullanılan yordam dışında işlemlerin listesi ve Visual Studio. Bu liste, belirli iş akışlarında veya senaryolarda başlatan işlemleri içerir ve bu nedenle çoğu durumda bunların hepsi aynı anda çalışmaz.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Bu işlemlerden herhangi biri beklenmedik şekilde sonlandırılırsa, Visual Studio işlevleri çalışmayı durdurur. Bazı işlemler için işlev kaybı önemli olabilir. Diğerleri için, uygulamanın Visual Studio etkilenir ve bir hata iletisi görüntülenir.

> [!NOTE]
> Bu sayfada başvurulmayan bir sorunla karşınız varsa lütfen [](../../ide/how-to-report-a-problem-with-visual-studio.md) hem Visual Studio Yükleyicisi'de hem de Visual Studio IDE'de görünen Sorun Bildir aracı aracılığıyla bize rapor edin.
