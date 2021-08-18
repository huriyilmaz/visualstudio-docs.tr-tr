---
title: Windows (ETW) verileri için olay izlemeyi topla | Microsoft Docs
description: uygulamada performans sorunlarının nerede olduğunu anlamak için Windows (ETW) için olay izlemeyi nasıl kullanacağınızı öğrenin. Verileri VSPerfReport.exe görüntüleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42de6efe72db8ae8cc1583114a288dd037c4b0c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150475"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>nasıl yapılır: Windows (ETW) verileri için olay izlemeyi toplama

Windows için olay izleme (ETW), profil oluşturucu günlük çekirdeğini veya uygulama tanımlı olayları sağlayan etkili bir çekirdek düzeyi izleme olanıdır. Olay sağlayıcısından toplanan veriler yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracının/**summary: ETW** seçeneği kullanılarak görüntülenebilir. Uygulamada performans sorunlarının nerede olduğunu anlamak için bu raporu kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Olay izleme sağlayıcılarını etkinleştirmek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **özellik sayfalarında** **Windows olayları** özelliklerine tıklayın.

3. **Verileri toplamak için olay izleme sağlayıcısını seçin** listesinden, uygulamanızı profili eklemek için kullanmak istediğiniz olay sağlayıcılarını seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
