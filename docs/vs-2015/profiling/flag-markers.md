---
title: Bayrak Işaretçileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e531d2d2a41cc9ceaa3b6ba39c6d77a166cfae83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193694"
---
# <a name="flag-markers"></a>Bayrak İşaretleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bayrak işaretçisi, bir uygulamada anında zamanında oluşan bir şeyi temsil eder. Bayrak birçok tür uygulama olayını temsil edebilir. Örneğin, belirli bir iş öğesi zamanlandığında veya bir özel durum oluştuğunda bayrak gösterilebilir. Görev paralel kitaplığı gibi çalışma zamanları da bayrak oluşturabilir.  
  
## <a name="flag-importance"></a>Bayrak önemi  
 Bayraklar önem derecesine bağlı olarak farklı boyutlarda görüntülenir. Herhangi bir işaret gibi, önem düzeyi düşük, normal, yüksek veya kritik olabilir.  Bu çizimde, işaretlerin önem düzeyine göre görünümü gösterilmektedir:  
  
 ![Düşük, normal, yüksek ve kritik önem işaretçileri](../profiling/media/cvmarkerimportance.png "Cvmarkerönem derecesi")  
Bayrak önemini gösteren işaretçiler  
  
## <a name="flag-category"></a>Bayrak kategorisi  
 Bir bayrak, kategorisine göre beş farklı renkten birinde görüntülenir. 5 ' ten fazla kategori varsa renkler yeniden kullanılır. Rengi seçemezsiniz. Herhangi bir işaretleyici gibi kategori herhangi bir tamsayı olabilir. Sonraki çizimde ilk beş kategorinin renkleri gösterilmektedir.  
  
 ![Kategori işaretçilerinin beş rengi](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Kategorileri gösteren işaretçiler  
  
## <a name="alerts"></a>Uyarılar  
 Uyarı, özel durum gibi kritik bir uygulama olayını temsil eden kırmızı renkli bir bayraktır.  Bir uyarı aşağıda verilmiştir:  
  
 ![Eşzamanlılık görselleştiricisi uyarı Işaretleyicisi](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Bir uyarı işaretleyicisi  
  
## <a name="aggregation-flags"></a>Toplama bayrakları  
 Bazen bazı bayraklar, Eşzamanlılık Görselleştiricisinin tek tek çiziledikleri bir diğeri için kapalı olur. Bu gerçekleştiğinde, temeldeki bayrakları temsil eden bir gri *toplama bayrağı* gösterilir. İşaretçiyi Bu simgelerden birine bıraktığınızda, bir araç ipucu temsil edilen temeldeki bayrakların sayısını görüntüler. Bayrakları görüntülemek için yakınlaştırın. Tüm yolu yakınlaştırıp yine de bir toplama bayrağı almaya devam ederseniz, [Işaretçi raporundaki](../profiling/markers-report.md)temel bayrakları görüntüleyebilirsiniz.  
  
 Toplama bayrakları farklı boyutlarda çizilir. Boyut, toplamada en önemli bayrağın önem düzeyine bağlıdır. Aşağıdaki çizim, toplama bayraklarını artan önem sırasına göre gösterir.  
  
 ![Dört önemli düzeyi gösteren toplama bayrakları](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Önem düzeyine göre toplama bayrakları  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi Işaretçileri](../profiling/concurrency-visualizer-markers.md)   
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
