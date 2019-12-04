---
title: İşlem görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 30c938088538bcecc71e3a7e37d5ae403dd476e1
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778407"
---
# <a name="process-view---contention-data"></a>İşlem görünümü-çekişme verileri
Işlem görünümü, profil oluşturma çalışması sırasında yürütülen işlemler ve iş parçacıkları için çekişme verilerini görüntüler.

 Semboller kullanılabilir olduğunda, süreçler ada göre listelenir. Semboller kullanılabilir olmadığında, işlem bellek adresleri tarafından onaltılık biçimde listelenir. İş parçacıkları, kendilerini oluşturan işlemin alt öğeleri olarak listelenir.

 Aşağıdaki tabloda, Işlem görünümü tablosundaki sütunların değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Başlangıç zamanı**|Profil oluşturmanın başından işlemin veya iş parçacığının başlangıcına kadar geçen milisaniye veya işlemci döngüsü sayısı.|
|**Engellenme süresi**|İşlemin veya iş parçacığının işlevlerinin yürütülmesinin engellendiği toplam süre.|
|**Engellenme süresi yüzdesi**|İşlemin veya iş parçacığının işlevlerinin yürütülmesinin engellendiği işlemin veya iş parçacığının yaşam süresinin yüzdesi.|
|**Çekişme**|İşlem veya iş parçacığının işlevlerinin yürütülmesinin engellendiği zaman sayısı.|
|**Çekişme**|İşlem veya iş parçacığının çekişmeleri olan profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|
|**Bitiş zamanı**|Profil oluşturmanın başından işlemin veya iş parçacığının sonuna kadar geçen milisaniye veya işlemci döngüsü sayısı.|
|**NUMARASıNı**|İşlemin veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|
|**Yaşam süresi**|İşlemin veya iş parçacığının başından, işlemin veya iş parçacığının sonuna veya profil oluşturmanın sonuna kadar geçen milisaniye veya işlemci döngüsü sayısı.|
|**Türüyle**|Satır türü, işlem veya iş parçacığı.<br /><br /> Yalnızca **VSReport** komut satırı raporlarında. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).|
|**Ad**|İşlemin veya iş parçacığının adı.|
|**Benzersiz KIMLIK**|İşlem veya iş parçacığı için benzersiz olan profil oluşturucu tarafından oluşturulan bir tanımlayıcı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlem Görünümü](../profiling/process-view.md)
