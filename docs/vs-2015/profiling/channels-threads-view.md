---
title: Kanallar (Iş parçacıkları görünümü) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df93a87285bdf1172e75b63ed956c1aa978fc71e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545541"
---
# <a name="channels-threads-view"></a>Kanallar (İş Parçacıkları Görünümü)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi dört tür kanal gösterir: iş parçacığı kanalları, disk kanalları, işaret kanalları ve GPU kanalları.  
  
## <a name="thread-channels"></a>İş parçacığı kanalları  
 İş parçacığı kanalı, yalnızca bir iş parçacığı için iş parçacığı durumunu renge göre gösterir. Kanal adında durakladığınızda, verilen iş parçacığı için Başlat işlevi görüntülenir. Eşzamanlılık görselleştiricisi çeşitli iş parçacığı türlerini algılar. En yaygın türleri aşağıdaki tabloda gösterilmiştir.  
  
|İş Parçacığı|Açıklama|  
|-|-|  
|Ana iş parçacığı|Uygulamayı başlatan iş parçacığı.|  
|Çalışan iş parçacığı|Uygulama ana iş parçacığı tarafından oluşturulan bir iş parçacığı.|  
|CLR Worker Iş parçacığı|Ortak dil çalışma zamanı (CLR) tarafından oluşturulan bir çalışan iş parçacığı.|  
|Hata ayıklayıcı Yardımcısı|Visual Studio hata ayıklayıcısı tarafından oluşturulan bir çalışan iş parçacığı.|  
|ConcRT Iş parçacığı|Microsoft Eşzamanlılık Çalışma Zamanı tarafından oluşturulan bir iş parçacığı.|  
|GDI Iş parçacığı|GDIPlus tarafından oluşturulan bir iş parçacığı.|  
|OLE/RPC Iş parçacığı|RPC çalışan Iş parçacığı olarak oluşturulan bir iş parçacığı.|  
|RPC Iş parçacığı|RPC Iş parçacığı olarak oluşturulan bir iş parçacığı.|  
|Winsock Iş parçacığı|Winsock Iş parçacığı olarak oluşturulan bir iş parçacığı.|  
|İş parçacığı havuzu|CLR Iş parçacığı havuzu tarafından oluşturulan bir iş parçacığı.|  
  
## <a name="disk-channels"></a>Disk kanalları  
 Disk kanalları bilgisayardaki fiziksel sürücülere karşılık gelir. Sistemdeki her fiziksel sürücü için okuma ve yazma işlemleri için ayrı kanallar bulunduğundan, her sürücüde iki kanal bulunur. Disk numaraları çekirdek cihaz adlarına karşılık gelir. Disk kanalı yalnızca diskte etkinlik varsa gösterilir.  
  
## <a name="marker-channels"></a>İşaret kanalları  
 İşaretleyici kanalları, uygulama tarafından oluşturulan olaylara ve kullandığı kitaplıklara karşılık gelir. Örneğin, görev paralel kitaplığı, paralel Desenler kitaplığı ve C++ AMP işaretleyiciler olarak görüntülenen olaylar oluşturur. Her işaretleyici kanalı, kanalın açıklamasının yanında görünen bir iş parçacığı KIMLIĞI ile ilişkilendirilir. KIMLIĞI, olayı oluşturan iş parçacığını tanımlar. Kanalın açıklaması, olayları oluşturan Windows için olay Izleme (ETW) sağlayıcısının adını içerir. Kanal [Eşzamanlılık Görselleştiricisi SDK 'sının](../profiling/concurrency-visualizer-sdk.md)olaylarını görüntülüyorsa, seri adı da görüntülenir.  
  
## <a name="gpu-channels"></a>GPU kanalları  
 GPU kanalları sistemde DirectX 11 etkinliği hakkındaki bilgileri görüntüler.  Grafik kartıyla ilişkili her DirectX altyapısının ayrı bir kanalı vardır.  Tek tek segmentler, bir DMA paketini işlemek için harcanan süreyi temsil eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
