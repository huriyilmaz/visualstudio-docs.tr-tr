---
title: İşlem görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e43541ddb75b067faa23437d315ce5f239256b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180225"
---
# <a name="process-view---contention-data"></a>İşlem Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|**ID**|İşlemin veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|  
|**Yaşam süresi**|İşlemin veya iş parçacığının başından, işlemin veya iş parçacığının sonuna veya profil oluşturmanın sonuna kadar geçen milisaniye veya işlemci döngüsü sayısı.|  
|**Tür**|Satır türü, işlem veya iş parçacığı.<br /><br /> Yalnızca **VSReport** komut satırı raporlarında. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).|  
|**Ad**|İşlemin veya iş parçacığının adı.|  
|**Benzersiz Kimlik**|İşlem veya iş parçacığı için benzersiz olan profil oluşturucu tarafından oluşturulan bir tanımlayıcı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [İşlem Görünümü](../profiling/process-view.md)
