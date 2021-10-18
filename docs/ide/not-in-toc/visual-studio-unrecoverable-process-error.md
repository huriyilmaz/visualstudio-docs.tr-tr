---
title: Bir işlem kurtarılamaz bir hatayla karşılaştı
description: Visual Studio normal işlemleri sırasında kurtarılamaz hatalarla karşılaşılabilecek işlemler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/14/2021
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
ms.openlocfilehash: 040e767f5c0bfd064b5e604d1975a1a5415b1867
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087442"
---
# <a name="visual-studio-unrecoverable-process-error"></a>kurtarılamaz işlem hatası Visual Studio

::: moniker range="<=vs-2019"
Visual Studio, canlı birim testi, kod çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç işlem dışı işlem kullanır. bu işlemler, uzun kaynak yoğunluklu işleri çalıştırırken Visual Studio daha hızlı yanıt vermesini sağlamak gibi Visual Studio performans avantajları sağlamak için işlem dışı çalıştırıllardır. ayrıca, Visual Studio 32 bitlik bir işlem olduğu için işlem dışı işlemler, yoğun bir şekilde çalışmak için daha büyük bir bellek alanı sağlar.
:::moniker-end
:::moniker range=">=vs-2022"
Visual Studio, canlı birim testi, kod çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç işlem dışı işlem kullanır. bu işlemler, uzun kaynak yoğunluklu işleri çalıştırırken Visual Studio daha hızlı yanıt vermesini sağlamak gibi Visual Studio performans avantajları sağlamak için işlem dışı çalıştırıllardır.
:::moniker-end

*ServiceHub.RoslynCodeAnalysisService.exe* veya *ServiceHub.RoslynCodeAnalysisService32.exe* işlemi herhangi bir nedenle sona erdiğinde, aşağıdaki iletiyle birlikte bir açılan bilgi çubuğu görünür:

**"ne yazık ki Visual Studio tarafından kullanılan bir işlem kurtarılamaz bir hatayla karşılaştı. Çalışmanızı kaydetmenizi ve sonra Visual Studio kapatıp yeniden başlatmanızı öneririz. "**

Bu iletiyi görürseniz, çalışmanızı kaydedip Visual Studio kapatıp yeniden başlatmanız gerekir.

## <a name="list-of-processes"></a>İşlem listesi

Visual Studio tarafından kullanılan işlem dışı işlemlerin bir listesi aşağıda verilmiştir. Bu liste, belirli iş akışlarında veya senaryolarda başlatılan işlemlerin yanı sıra, çoğu durumda hepsi aynı anda çalışmıyor.

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

bu işlemlerden herhangi biri beklenmedik bir şekilde sonlandırılırsa Visual Studio içindeki bazı işlevler çalışmayı durdurur. Bazı süreçler için işlevsellik kaybı önemli olabilir. başkaları için Visual Studio kararlılığı etkilenir ve bir hata iletisi görüntülenir.

> [!NOTE]
> bu sayfada başvurulmayan bir sorunla karşılaşırsanız, lütfen Visual Studio Yükleyicisi ve Visual Studio ıde 'de görüntülenen [sorun bildir](../../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.
