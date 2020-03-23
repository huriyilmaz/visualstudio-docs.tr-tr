---
title: İşlem Görünümü - Çekişme Verileri | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778407"
---
# <a name="process-view---contention-data"></a>İşlem Görünümü - çekişme verileri
İşlem görünümü, profil oluşturma çalışması sırasında yürütülen işlemler ve iş parçacıkları için çekişme verilerini görüntüler.

 Semboller kullanılabilir olduğunda, işlemler ada göre listelenir. Semboller kullanılamıyorsa, işlemler bellek adreslerine göre hexadecimal biçimde listelenir. İş parçacıkları, onları oluşturan işlemin çocukları olarak listelenir.

 Aşağıdaki tabloda İşlem görünümü tablosundaki sütunların değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Başlangıç Zamanı**|Profil oluşturmanın başlangıcından işlemin veya iş parçacığının başlangıcına kadar milisaniye veya işlemci döngülerinin sayısı.|
|**Engellenen Süre**|İşlemin veya iş parçacığının işlevlerinin yürütülmesinin engellendiği toplam süre.|
|**Engellenen Süre %**|İşlemin veya iş parçacığının işlevlerinin yürütülmesinin engellendiği işlemin veya iş parçacığının kullanım ömrü yüzdesi.|
|**Contentions**|İşlemin veya iş parçacığının işlevlerinin yürütülmesinin engellenme sayısı.|
|**Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, işlemin veya iş parçacığının çekişmeleriydi.|
|**Bitiş Saati**|Profil oluşturmanın başlangıcından işlemin veya iş parçacığının sonuna kadar milisaniye veya işlemci döngülerinin sayısı.|
|**Kimliği**|İşlemin veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|
|**Yaşam Süresi**|İşlemin veya iş parçacığının başlangıcından işlemin veya iş parçacığının sonuna veya profil oluşturmanın sonuna kadar milisaniye veya işlemci döngülerinin sayısı.|
|**Tür**|Satır türü, işlem veya iş parçacığı.<br /><br /> Yalnızca **VSReport** komut satırı raporlarında. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.|
|**Adı**|İşlemin veya iş parçacığının adı.|
|**Benzersiz Kimlik**|İşleme veya iş parçacığına özgü bir profil oluşturucu tarafından oluşturulan tanımlayıcı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [İşlem Görünümü](../profiling/process-view.md)
