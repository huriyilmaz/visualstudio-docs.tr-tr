---
title: 'Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810209"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Nasıl yapılır: Windows için Olay İzleme (ETW) Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows için olay Izleme (ETW), profil oluşturucu günlük çekirdeğini veya uygulama tanımlı olayları sağlayan etkili bir çekirdek düzeyi izleme olanıdır. Olay sağlayıcısından toplanan veriler yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracının/**summary: ETW** seçeneği kullanılarak görüntülenebilir. Uygulamada performans sorunlarının nerede olduğunu anlamak için bu raporu kullanabilirsiniz.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Olay izleme sağlayıcılarını etkinleştirmek için  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Özellik sayfalarında**, **Windows olayları** özelliklerine tıklayın.  
  
3. **Verileri toplamak için olay izleme sağlayıcısını seçin** listesinden, uygulamanızı profili eklemek için kullanmak istediğiniz olay sağlayıcılarını seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Oturumlarını Yapılandırma](../profiling/configuring-performance-sessions.md)
