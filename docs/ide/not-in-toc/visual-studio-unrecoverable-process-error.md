---
title: Bir işlem kurtarılamaz bir hatayla karşılaştı
description: Visual Studio 'nun normal işlemleri sırasında kurtarılamaz hatalarla karşılaşılabilecek işlemler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e44f96e0a8056a369b164e725aca6832b5a349cb
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871489"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio kurtarılamaz işlem hatası

Visual Studio, canlı birim testi, kod Çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç işlem dışı işlem kullanır. Bu işlemler, Visual Studio 'nun uzun, yoğun kaynak kullanan işleri çalıştırırken daha hızlı yanıt vermesini sağlayan, Visual Studio performans avantajları sağlamak için işlem dışı çalıştırıllardır. Ayrıca, Visual Studio 32 bitlik bir işlem olduğu için işlem dışı işlemler, yoğun bir şekilde çalışmak için daha büyük bir bellek alanı sağlar.

*ServiceHub.RoslynCodeAnalysisService.exe* veya *ServiceHub.RoslynCodeAnalysisService32.exe* işlemi herhangi bir nedenle sona erdiğinde, aşağıdaki iletiyle birlikte bir açılan bilgi çubuğu görünür:

**"Ne yazık ki, Visual Studio tarafından kullanılan bir işlem kurtarılamaz bir hatayla karşılaştı. İşinizi kaydetmenizi ve sonra Visual Studio 'Yu kapatıp yeniden başlatmanızı öneririz. "**

Bu iletiyi görürseniz, çalışmanızı kaydetmeli ve sonra Visual Studio 'Yu kapatıp yeniden başlatmalısınız.

## <a name="list-of-processes"></a>İşlem listesi

Aşağıda, Visual Studio tarafından kullanılan işlem dışı işlemlerin bir listesi verilmiştir. Bu liste, belirli iş akışlarında veya senaryolarda başlatılan işlemlerin yanı sıra, çoğu durumda hepsi aynı anda çalışmıyor.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft. CodeAnalysis. LiveUnitTesting. EntryPoint
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

Bu işlemlerden herhangi biri beklenmedik bir şekilde sonlandırılırsa, Visual Studio içindeki bazı işlevler çalışmayı durdurur. Bazı süreçler için işlevsellik kaybı önemli olabilir. Diğerleri için, Visual Studio 'nun kararlılığı etkilendi ve bir hata iletisi görüntülenir.

> [!NOTE]
> Bu sayfada başvurulmayan bir sorunla karşılaşırsanız, lütfen Visual Studio Yükleyicisi ve Visual Studio IDE içinde görüntülenen [sorun bildir](../../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.
