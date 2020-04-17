---
title: Bir işlem kurtarılamaz bir hatayla karşılaştı
ms.date: 06/22/2018
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c30ac5950ca9bf775b05e9f77867c119b7c7565d
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544347"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio kurtarılamaz işlem hatası

Visual Studio, canlı birim testi, kod çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç prok dışı işlem kullanır. Bu süreçler Visual Studio performans avantajları sağlamak için proc'un dışında dır, örneğin Visual Studio'nun uzun ve kaynak yoğun işlerde çalışırken daha hızlı yanıt vermesini sağlamak gibi. Ayrıca, Visual Studio 32 bit lik bir işlem olduğundan, proc dışında çalışan işlemler bellek yoğun çalışma içinde çalışması için daha büyük bir bellek alanı verir.

*ServiceHub.RoslynCodeAnalysisService.exe* veya *ServiceHub.RoslynCodeAnalysisService32.exe* işlemi nedense sona ererse, aşağıdaki iletiyle birlikte bir açılır bilgi çubuğu görüntülenir:

**"Ne yazık ki, Visual Studio tarafından kullanılan bir süreç kurtarılamaz bir hata ile karşılaştı. Çalışmanızı kaydetmenizi ve Ardından Visual Studio'yı kapatıp yeniden başlatmanızı öneririz."**

Bu iletiyi görürseniz, çalışmanızı kaydetmeli ve ardından Visual Studio'yı kapatıp yeniden başlatmalısınız.

## <a name="list-of-processes"></a>Süreçler listesi

Aşağıda Visual Studio tarafından kullanılan proc dışı süreçlerin bir listesi yer almaktadır. Bu liste, belirli iş akışlarında veya senaryolarda başlatılan işlemleri içerir ve bu nedenle çoğu durumda bunların tümü aynı anda çalışmaz.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- Msbuild.exe
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

Bu işlemlerden herhangi biri beklenmedik bir şekilde sona ererse, Visual Studio'daki bazı işlevler çalışmayı durdurur. Bazı işlemler için işlevsellik kaybı önemsiz olabilir. Diğerleri için Visual Studio'nun kararlılığı etkilenir ve bir hata iletisi görüntülenir.
