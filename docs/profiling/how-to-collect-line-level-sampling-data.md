---
title: 'Nasıl Kullanılır: Satır Düzeyinde Örnekleme Verileri Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f64040c9180a152650de16b23276ab0e65cc9ead
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776364"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Nasıl kullanılır: Satır düzeyinde örnekleme verileri toplama
Satır düzeyinde örnekleme, profilcinin, yüksek özel örnekleri olan bir işlev gibi işlemci yoğun bir işlevin kodunda, işlemcinin zamanının çoğunu nerede geçirmesi gerektiğini belirleme yeteneğidir.

## <a name="overview"></a>Genel Bakış
 Satır düzeyinde örnekleme için profiloluşturucu program arama yığınını belirli aralıklarla yürür ve bu sonuçları toplar. Bu sonuçlar, örnekler alındığında işlemcinin hangi yönergeleri çalıştıracağını gösterir. Özel örnekler le ilgili toplanan veriler daha sonra kod satırlarını ve talimat işaretçisini (IP) tanımlamak için analiz edilir.

 Satır düzeyinde örnekleme, yerel kodun yanı sıra yönetilen kod için de çalışır. Bu verileri görüntüleyen performans raporları, Satırlar görünümünü ve Modüller görünümünü içerir.

 Karakter başlangıç/bitiş bilgileri yerel kod için kullanılamaz. Çok satırlı ifadeler için satır başlangıç bilgileri yerel kod için kullanılamaz; yalnızca satır sonu bilgileri kullanılabilir.

### <a name="available-data"></a>Kullanılabilir veriler
 Kullanılabilir satır düzeyinde örnekleme verileri aşağıdaki bilgileri içerir:

- Fonksiyon adı.

- Fonksiyon adresi.

- Satırlar, örnekalınan kodun satır numarası olarak başlar.

- Satır sonu - bitiş kaynak satır numarası. Bu genellikle tek bir program deyimi birden çok kaynak kodu satırları yayılan dışında "Satır başlar" verileri ile aynıdır.

- Karakterler başlar - toplam örneğin başlangıç sütunu. Tek bir satır birden çok program deyimleri içerdiği durumlar dışında bu genellikle 0'dır.

- Karakter sonu - toplam örneğin bitiş sütunu.

- IP - toplam örneğin alındığı adres (yalnızca IP görünümü).

  **Modüller** görünümünde, bir işlevin satır düzeyinde istatistikleri varsa, istatistikler her işlevin altında iç içe dir. Ayrıca, her satırın altında iç içe olan IP düzeyi istatistikleri sunulur.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Yönetilen kod için satır düzeyinde örneklemeyi kapatma
 Varsayılan olarak, satır düzeyinde örnekleme açık. Yönetilen kod için satır düzeyinde veri toplamayı aşağıdaki komutlardan birini kullanarak kapatabilirsiniz:

- Profil çıkarmadan önce **VSPerfCLREnv /samplelineoff**yazın. Bu hem uygulamaları hem de hizmetleri etkiler.

     — veya —

- Bir uygulamayı başlatırken, **VSPerfCmd \</lineoff diğer bağımsız değişkenler>** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
