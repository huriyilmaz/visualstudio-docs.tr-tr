---
title: 'Nasıl Yapılır: Windows (ETW) Verileri için Olay İzlemesini Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2fa0547682351d1a7ba4efe4ce3b4350b906462c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779031"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Nasıl yapılır: Windows (ETW) verileri için Olay İzlemesini Toplama

Windows için Olay İzleme (ETW), profil oluşturucu günlük çekirdeğini veya uygulama tanımlı olayları etkinleştiren etkili bir çekirdek düzeyinde izleme tesisidir. Olay sağlayıcısından toplanan veriler yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracının /**Summary:ETW** seçeneği kullanılarak görüntülenebilir. Bu raporu, uygulamada performans sorunlarının nerede oluştuğunu belirlemek için kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="to-enable-event-trace-providers"></a>Olay izleme sağlayıcılarını etkinleştirmek için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Özellik **Sayfalarında,** Windows **Olayları** özelliklerini tıklatın.

3. Listeden **veri toplamak için Olay İzleme Sağlayıcısını Seç'te,** uygulamanızın profilini çıkarmak için kullanmak istediğiniz olay sağlayıcılarını seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
