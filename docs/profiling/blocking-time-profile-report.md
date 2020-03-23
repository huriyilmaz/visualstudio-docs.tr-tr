---
title: Engelleme Zamanı Profil Raporu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ed24dce0779b9bc7ea9cfd7bedcaa5ca181c68
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926307"
---
# <a name="blocking-time-profile-report"></a>Zaman profili raporunu engelleme
Profil Raporları, her engelleme kategorisine özgü çağrı yığınları için toplu engelleme zamanı verileri sağlar (örneğin"G/Ç" veya "Eşitleme"). Preemption raporu, geçerli işlemi önleyen işlemleri, preemption örneklerinin sayısıyla birlikte listeler. Engelleme profili raporunu oluşturmak için araç, engelleme API çağrılarını toplar ve bunları çağrı yığınları ağacında birikir. Bu raporlarda gösterilen veriler geçerli zaman aralığına, gizli iş parçacıklarına ve uygulanabilecek aşağıdaki iki filtreye göre değişir:

- Yalnızca Kodum seçilirse, yalnızca kullanıcı koduna sahip yığın çerçeveleri ve kullanıcı kodunun altında bir düzey sunulur.

- Gürültü azaltma değeri ayarlanırsa, belirtilen frekanstan daha az olan harmanlanmış yığınlar atlanır.

  Engelleme süresinin harcandıği kod satırını bulmak için herhangi bir çağrı ağacı girişini genişletin. Bir girişin kaynak satırını bulmak için, kısayol menüsünde **Kaynak Görüntüle'yi**seçin. Kısayol menüsünde buna çağrılan kod satırını bulmak için **Arama Sitelerini Görüntüle'yi**seçin. Yalnızca bir arama sitesi varsa, komut çağrı sitesi için vurgulanan kod satırına bağlanır. Birden çok arama sitesi varsa, komut, bir giriş seçebileceğiniz ve ardından vurgulanan arama sitesini bulmak **için kaynak** için git düğmesini seçebileceğiniz bir iletişim kutusu açar. Çoğu örneği, en çok zaman veya her ikisine sahip arama sitesinin kaynak kodunu görüntülemek genellikle yararlıdır.

## <a name="blocking-time-report-columns"></a>Zaman raporu sütunlarını engelleme
 Aşağıdaki tablo, her engelleme zamanı raporu için sütunları gösterir.

|Sütun adı|Açıklama|
|-----------------|-----------------|
|**Adı**|Çağrı yığınının her düzeyi için işlevin adı.|
|**Örnekler**|Görünür zaman dilimi için engelleme çağrısıörneklerinin sayısı.|
|**Kapsayıcı Engelleme Süresi**|Çağrı yığını ağacının bu düzeyine kadar yuvarlanan tüm yığınlar için harcanan toplam engelleme süresi. Kapsayıcı sayı, bu işlev için özel engelleme süresinin ve tüm alt düğümleri için özel engelleme süresinin toplamıdır.|
|**Özel Engelleme Süresi**|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplam engelleme süresi. Yüksek özel engelleme süresine sahip benzersiz bir çağrı yığını girişi ilgi çekici bir işlev olabilir.|
|**API/Bekle Kategorisi**|Yalnızca çağrı yığınının en alt düzeyindeki işlevler için gösterilir. Engelleme çağrısının imzasının tanındığı durumlarda, engelleme API'sinin adı sağlanır. İmza tanınmazsa, çekirdek tarafından bildirilen bilgiler sağlanır.|
|**Şey**|Fonksiyonun tam nitelikli adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

### <a name="synchronization"></a>Eşitleme
 Eşitleme raporu, eşitleme üzerinde engelleme yapan segmentlerden sorumlu çağrıları ve her çağrı yığınının toplu engelleme sürelerini gösterir. Daha fazla bilgi için [Eşitleme süresine](../profiling/synchronization-time.md)bakın.

### <a name="sleep"></a>Uyku
 Uyku raporu, uyku için harcanan zamana atfedilen zamanı engellemekten sorumlu çağrıları ve her çağrı yığınının toplu engelleme sürelerini gösterir. Daha fazla bilgi için [Uyku süresine](../profiling/sleep-time.md)bakın.

### <a name="io"></a>G/Ç
 G/Ç raporu, G/Ç'de engellenen segmentlerden sorumlu çağrıları ve her çağrı yığınının toplu engelleme sürelerini gösterir. Daha fazla bilgi için [G/Ç saati (iş parçacığı görünümü)](../profiling/i-o-time-threads-view.md)konusuna bakın.

### <a name="memory-management"></a>Bellek yönetimi
 Bellek Yönetimi raporu, bellek yönetimi işlemlerini engelleyen segmentlerden sorumlu çağrıları ve her çağrı yığınının toplu engelleme sürelerini gösterir. Daha fazla bilgi için [Bellek yönetimi süresine](../profiling/memory-management-time.md)bakın.

### <a name="preemption"></a>Preemption
 Preemption raporu, örnek sayısıyla birlikte geçerli işlemi engelleyen işlemleri listeler.  Geçerli işlemdeki iş parçacıklarının yerini alan belirli iş parçacıklarını görüntülemek ve iş parçacığı başına preemption örneklerinin dökümünü görüntülemek için her işlemi genişletebilirsiniz. Bu engelleme raporu diğerlerinden daha az işlem lenebilir, çünkü önalım genellikle işleminize kodunuzdaki bir sorun tarafından değil, işletim sistemi tarafından uygulanır. Daha fazla bilgi için [Preemption süresine](../profiling/preemption-time.md)bakın.

### <a name="ui-processing"></a>UI işleme
 UI İşleme raporu, UI işleme bloklarında engellenen kesimleri engellemekten sorumlu çağrıları ve her çağrı yığınının toplu engelleme sürelerini gösterir. Daha fazla bilgi için [Kullanıcı Arabirimi işleme süresine](../profiling/ui-processing-time.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)