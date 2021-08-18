---
title: Örnek Line-Level Veri Toplama | Microsoft Docs
description: Profil oluşturmanın satır düzeyi örneklemesinin büyük miktarlarda işlemci süresi kullanan kodu nasıl ortaya çıkara olduğunu öğrenin. Hem yönetilen hem de yerel kodla çalışır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 163f0edd1042340f7d1abdbc73dc6099af946394
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061044"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Nasıl kullanılır: Satır düzeyi örnekleme verileri toplama
Satır düzeyi örnekleme, profil oluşturma işlevinin, yüksek özel örneklere sahip bir işlev gibi yoğun işlemcili bir işlevin kodunda zamanlarının çoğunu harcaması gereken yeri belirleme becerisidir.

## <a name="overview"></a>Genel Bakış
 Profil oluşturma, satır düzeyi örnekleme için program çağrı yığınında belirli aralıklarla yol gösterir ve bu sonuçları toplar. Bu sonuçlar, örnekler alınırken işlemcinin hangi yönergeleri yürütmesini gösterir. Özel örnekler hakkında toplanan veriler daha sonra kod satırlarını ve yönerge işaretçisini (IP) tanımlamak için analiz edilir.

 Satır düzeyi örnekleme hem yönetilen hem de yerel kod için çalışır. Bu verileri görüntü alan performans raporları, Çizgiler görünümünü ve Modüller görünümünü içerir.

 Karakter başlangıç/bitiş bilgileri yerel kod için kullanılamaz. Çok satırlı deyimler için satır başlangıç bilgileri yerel kod için kullanılamaz; yalnızca satır sonu bilgileri kullanılabilir.

### <a name="available-data"></a>Kullanılabilir veriler
 Kullanılabilir satır düzeyi örnekleme verileri aşağıdaki bilgileri içerir:

- İşlev adı.

- İşlev adresi.

- Satırlar, örnek alınan kodun satır numarasıyla başlar.

- Satır sonu - bitiş kaynak satır numarası. Bu genellikle "Line begin" verileriyle aynıdır ancak tek bir program deyimi birden çok kaynak kod satırına yayma durumudur.

- Karakterler başlar- toplama örneğinin başlangıç sütunu. Tek bir satırın birden çok program deyimi içerdiği durum dışında bu genellikle 0'dır.

- Karakter sonu - toplama örneğinin bitiş sütunu.

- IP - toplama örneğinin alınarak alınan adres (yalnızca IP görünümü).

  Modüller **görünümünde,** bir işlevin satır düzeyi istatistikleri varsa, istatistikler her işlevin altına iç içe geçmiştir. Ayrıca, her satırın altına iç içe geçmiş IP düzeyinde istatistikler de sunulmaktadır.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Yönetilen kod için satır düzeyi örneklemeyi kapatma
 Satır düzeyi örnekleme varsayılan olarak açıktır. Aşağıdaki komutlardan birini kullanarak yönetilen kod için satır düzeyi veri toplamayı kapatabilirsiniz:

- Profil oluşturmadan önce **VSPerfCLREnv /samplelineoff yazın.** Bu, hem uygulamaları hem de hizmetleri etkiler.

     — veya —

- Bir uygulamayı başlatarak **VSPerfCmd /lineoff yazın. \<other arguments>**

## <a name="see-also"></a>Ayrıca bkz.
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
