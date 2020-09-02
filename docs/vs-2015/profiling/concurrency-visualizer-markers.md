---
title: Eşzamanlılık görselleştiricisi Işaretçileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43b6115c45f9583b90711ef030834da662106f08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704359"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlılık Görselleştiricisi İşaretleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşzamanlılık görselleştiricisi içinde işaretçiler, bir uygulamadaki olayları temsil eden simgelerdir.  Genellikle uygulama, bir uygulamadaki aşamaları veya oluşumları belirlemek için bu olayları oluşturur.  Olaylar, uygulama tarafından veya uygulama tarafından kullanılan kitaplıklar ve çalışma zamanları tarafından oluşturulabilir.  
  
## <a name="kinds-of-markers"></a>Işaretçiler türleri  
 Eşzamanlılık görselleştiricisi uygulama olaylarını temsil etmek için üç tür işaretçi kullanır: bayraklar, iletiler ve yayılmalar.  
  
1. Uygulamanızda ilginç bir zaman noktası belirtmek için bir *bayrak* kullanın.  Örneğin, bir değişken değerinin belirli bir eşiğe ulaşmış olduğunu veya bir özel durumun oluşturulduğunu temsil eden bir bayrak kullanabilirsiniz.  
  
2. *İleti* Ayrıca bir zaman noktası da işaretler, ancak bunu günlük stili izleme için kullanabilirsiniz.  Örneğin, bir günlük dosyasına kaydedilmiş olabilecek özellikler artık bir ileti çağrısına kaydırabilmenizi sağlayacak ve bunu Eşzamanlılık Görselleştiricisinin içinde görüntüleyebilmenizi sağlayabilir. Eşzamanlılık Görselleştiricisini Ayrıca bu verileri bir CSV dosyasına aktarmak için de kullanabilirsiniz.  
  
3. Bir *yayılma* , uygulamanızdaki bir zaman aralığını temsil eder, örneğin aşamalarından biri.  
  
## <a name="marker-linkage-to-threads"></a>Iş parçacığına işaret bağlantısı  
 İşaretçiler üreten her iş parçacığının ayrı bir zaman çizelgesi kanalı vardır.  İşaretleyici olayları oluşturmaktan sorumlu iş parçacığının KIMLIĞI, işaret kanalının açıklamasının yanında gösterilir.  İşaret kanalının sol tarafında gösterilen KIMLIK, geçerli işlemdeki başka bir iş parçacığının KIMLIĞIYLE eşleşir.  
  
## <a name="marker-importance"></a>İşaret önemi  
 İşaretçiler dört önem düzeyinden birine sahip olabilir: düşük, normal, yüksek ve kritik.  İşaret kaynaklarını önem düzeyine göre filtreleyebilirsiniz.  Örneğin, yalnızca normal veya kritik öneme sahip belirli bir kaynağın işaretçilerini görmek isterseniz, filtreyi [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda yapılandırabilirsiniz. Bir işaretin önem derecesi, araç ipucunda ve [Işaretçiler raporunda](../profiling/markers-report.md)görüntülenir.  
  
## <a name="marker-category"></a>İşaretleyici kategorisi  
 İşaretleyici kategorisi, aynı kaynaktan gelen bir işaretleyici olayları grubunu belirtir.  Eşzamanlılık görselleştiricisi, bayrakların ve yayılmaları farklı kategorilerini ayırt etmek için renk kullanır. Eşzamanlılık Görselleştiricisini, belirli bir olay sağlayıcısından işaret olaylarını filtrelemek için kategorileri kullanacak şekilde yapılandırabilirsiniz.  Filtreyi yapılandırmak için [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanın.  
  
## <a name="known-sources-of-markers"></a>Bilinen Işaret kaynakları  
 Tüm ETW sağlayıcıları, sağlayıcı belirli kısıtlamalara uygun olduğu sürece işaretçiler oluşturabilir. Eşzamanlılık Görselleştiricisi ' i işaretçiler için ek olay kaynaklarını dinleyecek şekilde yapılandırabilirsiniz. Varsayılan olarak, bu olay kaynaklarını dinler:  
  
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)  
  
- [Görev Paralel Kitaplığı (TPL)](https://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Veri akışı](https://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Paralel LINQ (PLINQ)](https://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Eşzamanlılık Çalışma Zamanı](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Senaryo Işaretçisi desteği](https://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](https://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Çeşitli kaynaklardaki işaretlerin eşzamanlılık Görselleştiricide görüntülenip görüntülenmeyeceğini denetlemek için, [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Iletişim kutusundaki işaretçiler sekmesini kullanabilirsiniz. Bu, önemli ve kategoriye göre işaretleyiciler için filtre uygulayabilirsiniz.  
  
## <a name="markers-from-eventsource"></a>EventSource 'tan işaretçiler  
 Eşzamanlılık görselleştiricisi Ayrıca EventSource olaylarını gösterebilir.  Daha fazla bilgi için bkz. [EventSource olaylarını işaretçiler olarak görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bayrak Işaretçileri](../profiling/flag-markers.md)   
 [İleti Işaretçileri](../profiling/message-markers.md)   
 [Aralık Işaretçileri](../profiling/span-markers.md)   
 [EventSource Olaylarını İşaretleyici Olarak Görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md)
