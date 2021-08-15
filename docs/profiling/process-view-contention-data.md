---
title: İşlem Görünümü - Contention Data | Microsoft Docs
description: İşlem görünümünün profil oluşturma çalıştırması sırasında yürütülen işlemler ve iş parçacıkları için tartışma verilerini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 042b8834b9b3d1b4f91bef09a5a71b2bdb394da5865426f352b28446ee858811
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121246012"
---
# <a name="process-view---contention-data"></a>İşlem Görünümü - karşıtlık verileri
İşlem görünümü, profil oluşturma çalıştırması sırasında yürütülen işlemler ve iş parçacıkları için tartışma verilerini görüntüler.

 Semboller kullanılabilir olduğunda işlemler adla listelenir. Semboller kullanılabilir değilken işlemler onaltılık biçimde bellek adreslerine göre listelenir. İş parçacıkları, bunları oluşturan sürecin altında listelenir.

 Aşağıdaki tabloda İşlem görünümü tablosunda sütunların değerleri açıkmektedir.

|Sütun|Açıklama|
|------------|-----------------|
|**Başlangıç Saati**|Profil oluşturmanın başlamasından işlem veya iş parçacığının başlangıcına kadar olan milisaniye veya işlemci döngüsü sayısı.|
|**Engellenen Süre**|İşlem veya iş parçacığı işlevlerinin yürütülmesinin engellenmiş olduğu toplam süre.|
|**Engellenen Süre %**|İşlem veya iş parçacığı işlevlerinin yürütülmesinin engellenmiş olduğu işlem veya iş parçacığının yaşam süresi yüzdesi.|
|**Contentions**|İşlem veya iş parçacığı işlevlerinin yürütülmesinin kaç kez engellenmiş olduğu.|
|**İçerik %**|Profil oluşturma çalıştırması sırasında sürecin veya iş parçacığının tüm içeriğinin yüzdesi.|
|**Bitiş Zamanı**|Profil oluşturmanın başlamasından işlem veya iş parçacığının sonuna kadar olan milisaniye veya işlemci döngüsü sayısı.|
|**ID**|İşlem veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|
|**Yaşam Süresi**|Milisaniye veya işlemci döngülerinin sayısı, işlem veya iş parçacığının ya da profil oluşturmanın sonuna kadar olan işlem veya iş parçacığının başlangıcıdır.|
|**Tür**|İşlem veya iş parçacığı gibi satır türü.<br /><br /> Yalnızca **VSReport komut** satırı raporlarında. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).|
|**Ad**|İşlem veya iş parçacığının adı.|
|**Benzersiz Kimlik**|İşlem veya iş parçacığı için benzersiz olan profil oluşturma tarafından oluşturulan tanımlayıcı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlem Görünümü](../profiling/process-view.md)
