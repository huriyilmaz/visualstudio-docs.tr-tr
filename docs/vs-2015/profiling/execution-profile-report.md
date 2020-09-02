---
title: Yürütme profili raporu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0d95d4593939b878194d2aeef79bdd0a8ad946a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160642"
---
# <a name="execution-profile-report"></a>Yürütme Profil Raporu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yürütme profili raporu, geleneksel bir örnekleme profilidir. Örnekler, bir iş parçacığı mantıksal bir çekirdek üzerinde çalışırken, zaman aralığı boyunca yaklaşık olarak her milisaniyeye alınır ve eşzamanlılık görselleştiricisi, örnek yığınları birikmiş kümesini harmanlayarak tipik bir çağrı ağacı oluşturur. Bu tablodaki veriler geçerli zaman aralığı ve gizli iş parçacıklarından ve uygulanabilecek Bu filtrelerle etkilenebilir:  
  
- Yalnızca kendi kodum seçilirse yalnızca Kullanıcı kodu olan ve kullanıcı kodunun altında bir düzey olan yığın çerçeveleri gösterilir.  
  
- Gürültü azaltma değeri ayarlandıysa, belirtilen sıklığından daha az olan harmanlanmış yığınlar raporun dışına filtrelenir  
  
  Aşağıdaki tabloda rapordaki sütunlar gösterilmektedir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|Ad|Çağrı yığınının her bir düzeyi için işlevin adı.|  
|Kapsamlı örnekler|Çağrı yığını ağacının bu düzeyine toplanan tüm yığınlar için toplanan örneklerin toplam sayısı. Dahil edilen sayı, bu işlev için dışlamalı örneklerin toplamı ve tüm alt düğümleri için kapsamlı sayaçlardır.|  
|Dışlamalı örnekler|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplam toplanan örnek sayısı.|  
|Dahil yüzdesi|Kapsamlı örnekler sütununda gösterilen toplam örnek yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanır.|  
|% Özel|Dışlamalı örnekler sütununda gösterilen toplam örnek yüzdesi. Yüzdeler iki ondalık basamağa yuvarlanır.|  
|Ayrıntılar|İşlevin tam adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|  
  
 Bu rapor tablosu, [yürütme zamanı (Iş parçacıkları görünümü)](../profiling/execution-time-threads-view.md) görünümünde görülebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)
