---
title: Engelleme zamanı profil raporu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68926307"
---
# <a name="blocking-time-profile-report"></a>Engelleme zamanı profil raporu
Profil raporları, her engelleme kategorisine özgü çağrı yığınları için toplu engelleme zaman verileri sağlar (örneğin, "g/ç" veya "eşitleme"). Önalım raporu, önalım örneklerinin sayısıyla birlikte geçerli işlemi içeren işlemleri listeler. Engelleme profili raporunu oluşturmak için araç, API çağrılarını engellemeyi ve bunları bir çağrı yığını ağacına biriktirir. Bu raporlarda gösterilen veriler, geçerli zaman aralığına, gizli iş parçacıklarına ve uygulanabilecek aşağıdaki iki filtreye göre farklılık gösterir:

- Yalnızca kendi kodum seçilirse, yalnızca Kullanıcı kodu olan yığın çerçeveleri ve kullanıcı kodunun altında bir düzey gösterilir.

- Gürültü azaltma değeri ayarlandıysa, belirtilen sıklığından daha az olan harmanlanmış yığınlar atlanır.

  Engelleme zamanının harcadığı kod satırını bulmak için herhangi bir çağrı ağacı girişini genişletin. Bir girdinin kaynak çizgisini bulmak için, kısayol menüsünde **kaynağı görüntüle**' yi seçin. Bunu çağıran kod satırını bulmak için kısayol menüsünde, **çağrı sitelerini görüntüle**' yi seçin. Yalnızca bir adet çağrı sitesi varsa, komut, çağrı sitesi için vurgulanan kod satırına bağlanır. Birden çok çağrı sitesi varsa, komut bir giriş seçebileceğiniz ve sonra vurgulanan çağrı sitesini bulmak için **Kaynağa Git** düğmesini seçebileceğiniz bir iletişim kutusu açar. En çok, en çok örneğe sahip olan çağrı sitesi için kaynak kodunu, en son saati veya her ikisini birden görüntülemek en yararlı seçenektir.

## <a name="blocking-time-report-columns"></a>Engelleme zamanı rapor sütunları
 Aşağıdaki tabloda her engelleme zamanı raporunun sütunları gösterilmektedir.

|Sütun adı|Açıklama|
|-----------------|-----------------|
|**Ad**|Çağrı yığınının her bir düzeyi için işlevin adı.|
|**Örnekler**|Görünen zaman aralığı için engelleme çağrısının örnek sayısı.|
|**Kapsamlı engelleme süresi**|Çağrı yığını ağacının bu düzeyine kadar toplanan tüm yığınlar için harcanan toplam engelleme süresi. Dahil edilen sayı bu işlev için dışlamalı engelleme zamanının toplamı ve tüm alt düğümleri için dışlamalı engelleme süresi.|
|**Dışlamalı engelleme süresi**|Bu işlevin çağrı yığınının en düşük düzeyi olduğu zaman harcanan toplam engelleme süresi. Yüksek dışlamalı bir engelleme süresine sahip benzersiz bir çağrı yığını girişi, ilgilendiğiniz bir işlev olabilir.|
|**API/bekleme kategorisi**|Yalnızca çağrı yığınının en düşük düzeyindeki işlevler için gösterilir. Engelleme çağrısının imzasının tanınması durumunda, engelleyici API 'nin adı sağlanır. İmza tanınmazsa, çekirdek tarafından bildirilen bilgiler sağlanır.|
|**Ayrıntılar**|İşlevin tam adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

### <a name="synchronization"></a>Eşitleme
 Eşitleme raporu, eşitlemede bloke olan kesimlerden sorumlu olan çağrıları ve her bir çağrı yığınının toplam engellenme sürelerini gösterir. Daha fazla bilgi için bkz. [eşitleme süresi](../profiling/synchronization-time.md).

### <a name="sleep"></a>Uyku
 Uyku raporu, uyumaya harcanan zamana ve her bir çağrı yığınının toplam engellenme zamanına sahip olan zamanı engelleme işleminden sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [uyku süresi](../profiling/sleep-time.md).

### <a name="io"></a>G/Ç
 G/ç raporu g/ç 'de engelleyen kesimlerden sorumlu olan çağrıları ve her bir çağrı yığınının toplam engellenme sürelerini gösterir. Daha fazla bilgi için bkz. [g/ç zamanı (iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Bellek yönetimi
 Bellek yönetimi raporu, bellek yönetimi işlemlerini engelleyen kesimlerden sorumlu olan çağrıları ve her bir çağrı yığınının toplam engellenme sürelerini gösterir. Daha fazla bilgi için bkz. [bellek yönetimi zamanı](../profiling/memory-management-time.md).

### <a name="preemption"></a>Önalım
 Önalım raporu, geçerli işlemi örnek sayısıyla birlikte alan işlemleri listeler.  Her bir işlemi, geçerli işlemdeki iş parçacıklarının değiştirildiği belirli iş parçacıklarını görüntülemek ve iş parçacığı başına önalım örneklerinin dökümünü görüntülemek için genişletebilirsiniz. Bu engelleme raporu, kodunuzun kodunuzda bir sorun değil, önalım genellikle işletim sistemi tarafından işlebir şekilde yapıldığından, diğerleri bundan daha az işlem yapılabilir. Daha fazla bilgi için bkz. [önalım Time](../profiling/preemption-time.md).

### <a name="ui-processing"></a>UI işleme
 UI Işleme raporu, Kullanıcı arabirimi işleme blokları üzerinde engelleyici olan kesimleri ve her bir çağrı yığınının toplam engellenme süresini engelleyen çağrıları gösterir. Daha fazla bilgi için bkz. [UI işleme süresi](../profiling/ui-processing-time.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)