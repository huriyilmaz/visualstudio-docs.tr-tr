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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585801"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Visual Studio kurtarılamaz işlem hatası

Visual Studio, canlı birim testi, kod Çözümleyicileri ve daha fazlası gibi gerekli arka plan görevlerini çalıştırmak için birkaç işlem dışı işlem kullanır. Bu işlemler, Visual Studio 'nun uzun, yoğun kaynak kullanan işleri çalıştırırken daha hızlı yanıt vermesini sağlayan, Visual Studio performans avantajları sağlamak için işlem dışı çalıştırıllardır. Ayrıca, Visual Studio 32 bitlik bir işlem olduğu için işlem dışı işlemler, yoğun bir şekilde çalışmak için daha büyük bir bellek alanı sağlar.

*Servicehub. RoslynCodeAnalysisService. exe* veya *Servicehub. RoslynCodeAnalysisService32. exe* işlemi bazı nedenlerle sona erdiğinde, aşağıdaki iletiyle birlikte bir açılan bilgi çubuğu görünür:

**"Ne yazık ki, Visual Studio tarafından kullanılan bir işlem kurtarılamaz bir hatayla karşılaştı. İşinizi kaydetmenizi ve sonra Visual Studio 'Yu kapatıp yeniden başlatmanızı öneririz. "**

Bu iletiyi görürseniz, çalışmanızı kaydetmeli ve sonra Visual Studio 'Yu kapatıp yeniden başlatmalısınız.

## <a name="list-of-processes"></a>İşlem listesi

Aşağıda, Visual Studio tarafından kullanılan işlem dışı işlemlerin bir listesi verilmiştir. Bu liste, belirli iş akışlarında veya senaryolarda başlatılan işlemlerin yanı sıra, çoğu durumda hepsi aynı anda çalışmıyor.

- Microsoft. alm. Shared. Remoting. RemoteContainer. dll
- Microsoft. CodeAnalysis. LiveUnitTesting. EntryPoint
- PerfWatson2. exe
- ServiceHub. Host. Node. x86. exe
- ServiceHub. ıdentityhost. exe
- ServiceHub. VSDetouredHost. exe
- ServiceHub. SettingsHost. exe
- ServiceHub. Host. CLR. x86. exe
- ServiceHub. RoslynCodeAnalysisService32. exe
- ServiceHub. RoslynCodeAnalysisService. exe
- WindowsAzureGuestAgent. exe
- WindowsAzureTelemetryService. exe
- WaAppAgent. exe

Bu işlemlerden herhangi biri beklenmedik bir şekilde sonlandırılırsa, Visual Studio içindeki bazı işlevler çalışmayı durdurur. Bazı süreçler için işlevsellik kaybı önemli olabilir. Diğerleri için, Visual Studio 'nun kararlılığı etkilendi ve bir hata iletisi görüntülenir.
