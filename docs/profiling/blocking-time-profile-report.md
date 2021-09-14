---
title: Engelleme Zamanı Profili Rapor | Microsoft Docs
description: 'Engelleme zamanı profili raporları, toplam engelleme süresi verilerini sağlar. Altı rapor türü vardır: Eşitleme, Uyku, I/O, Bellek, Ön Bellek ve Kullanıcı Arabirimi.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1658e837875e1688b2990b7cbf5f8f5b2e4d5de0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628383"
---
# <a name="blocking-time-profile-report"></a>Engelleme zamanı profili raporu
Profil Raporları, her engelleme kategorisine özgü çağrı yığınları için toplam engelleme süresi verileri sağlar (örneğin, "I/O" veya "Eşitleme"). Preemption raporu, geçerli işlemi önalımı önalım örneği sayısıyla birlikte önalımı olan işlemleri listeler. Engelleme profili raporunu derlemek için araç, engelleme API çağrılarını toplar ve bunları bir çağrı yığınları ağacına toplar. Bu raporlarda gösterilen veriler geçerli zaman aralığına, gizli iş parçacıklarına ve uygulanacak aşağıdaki iki filtreye göre değişiklik gösterir:

- Bu Yalnızca kendi kodum seçilirse, yalnızca kullanıcı koduna sahip yığın çerçeveler ve kullanıcı kodunun altında bir düzey görüntülenir.

- Gürültü azaltma değeri ayarlanırsa, belirtilen sıklıktan daha az olan harmanlanmış yığınlar atlanır.

  Engelleme zamanlarının harcanmış olduğu kod satırı bulmak için herhangi bir çağrı ağacı girişini genişletin. Girişin kaynak çizgisini bulmak için kısayol menüsünde Kaynağı **Görüntüle'yi seçin.** Bunu çağıran kod satırına bulmak için kısayol menüsünde Çağrı Sitelerini **Görüntüle'yi seçin.** Yalnızca bir çağrı sitesi varsa, komut çağrı sitesi için vurgulanan kod satırına bağlanır. Birden çok çağrı sitesi varsa, komut içinde bir giriş seçerek vurgulanan  çağrı sitesini bulmak için Kaynağına git düğmesini seçerek bir iletişim kutusu açar. Çoğu zaman en çok örneği, en çok zamanı veya her ikisini de olan çağrı sitesi için kaynak kodu görüntülemek yararlıdır.

## <a name="blocking-time-report-columns"></a>Zaman raporu sütunlarını engelleme
 Aşağıdaki tabloda her engelleme zamanı raporunun sütunları yer alır.

|Sütun adı|Description|
|-----------------|-----------------|
|**Ad**|Çağrı yığınının her düzeyi için işlevin adı.|
|**Örnekler**|Görünür zaman dönemi için engelleme çağrısının örnek sayısı.|
|**Kapsayıcı Engelleme Süresi**|Çağrı yığını ağacının bu düzeyine kadar topan tüm yığınlar için harcanan toplam engelleme süresi. Kapsayıcı sayı, bu işlev için özel engelleme süresi ve tüm alt düğümleri için özel engelleme süresi toplamıdır.|
|**Özel Engelleme Süresi**|Bu işlevin çağrı yığınının en düşük düzeyi olduğu toplam engelleme süresi. Özel engelleme süresi yüksek olan benzersiz bir çağrı yığını girişi, ilgini üzerine bir işlev olabilir.|
|**API/Bekleme Kategorisi**|Yalnızca çağrı yığınının en düşük düzeyindeki işlevler için gösterilir. Engelleme çağrısının imzası tanınıyorsa, engelleme API'sini adı sağlanır. İmza tanınmıyorsa, çekirdek tarafından bildirilen bilgiler sağlanır.|
|**Ayrıntılar**|İşlevin tam adı. Bu, kullanılabilir olduğunda satır sayısını içerir.|

### <a name="synchronization"></a>Eşitleme
 Eşitleme raporu, eşitlemede engelleyen kesimlerden sorumlu olan çağrıları ve her çağrı yığınının toplam engelleme sürelerini gösterir. Daha fazla bilgi için [bkz. Eşitleme zamanı.](../profiling/synchronization-time.md)

### <a name="sleep"></a>Uyku
 Uyku raporu, uykuda harcanan süreye ve her çağrı yığınının toplam engelleme süresine bağlı engelleme süresinden sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [Uyku süresi.](../profiling/sleep-time.md)

### <a name="io"></a>G/Ç
 I/O raporu, I/O üzerinde engelleyen segmentlerden sorumlu olan çağrıları ve her çağrı yığınının toplam engelleme sürelerini gösterir. Daha fazla bilgi için [bkz. I/O zamanı (iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).

### <a name="memory-management"></a>Bellek yönetimi
 Bellek Yönetimi raporu, bellek yönetimi işlemlerini engelleyen kesimlerden sorumlu olan çağrıları ve her çağrı yığınının toplam engelleme sürelerini gösterir. Daha fazla bilgi için [bkz. Bellek yönetim zamanı.](../profiling/memory-management-time.md)

### <a name="preemption"></a>Önserme
 Önalım raporu, geçerli işlemi önden alan işlemleri örnek sayısıyla birlikte listeler.  Geçerli işlemde iş parçacıklarını değiştiren belirli iş parçacıklarını görüntülemek ve iş parçacığı başına önksesyon örneklerinin dökümünü görüntülemek için her işlemi genişletebilirsiniz. Bu engelleme raporu diğerlerine göre daha az eyleme değiştirilebilir çünkü ön engelleme genellikle işleminize kodda bir sorun değil işletim sistemi tarafından uygulanıyor. Daha fazla bilgi için [bkz. Önk.](../profiling/preemption-time.md)

### <a name="ui-processing"></a>UI işleme
 UI İşleme raporu, UI işleme bloklarını engelleyen kesimleri ve her çağrı yığınının toplam engelleme sürelerini sorumlu olan çağrıları gösterir. Daha fazla bilgi için [bkz. UI işleme süresi.](../profiling/ui-processing-time.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacıkları görünümü](../profiling/threads-view-parallel-performance.md)