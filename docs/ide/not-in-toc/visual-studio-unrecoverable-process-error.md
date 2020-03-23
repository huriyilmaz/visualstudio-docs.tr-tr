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
ms.openlocfilehash: 206fcddca51f8e770e013ff67de6ae3d5562f633
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585801"
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
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

Bu işlemlerden herhangi biri beklenmedik bir şekilde sona ererse, Visual Studio'daki bazı işlevler çalışmayı durdurur. Bazı işlemler için işlevsellik kaybı önemsiz olabilir. Diğerleri için Visual Studio'nun kararlılığı etkilenir ve bir hata iletisi görüntülenir.
