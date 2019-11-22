---
title: 'DA0506: Işlem için ayrılan en fazla özel bayt Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7452e8394b6397b79c49b9b706db5ba8899351e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291182"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: İşlem için izin verilen Maksimum Özel Bayt Sayısının profili oluşturuluyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0506 |  
| Kategori | Kaynak Izleme |  
| Profil oluşturma yöntemi | Tümü |  
| İleti | Bu bilgiler yalnızca bilgi için toplanmıştı. Işlem özel baytları sayacı, profil oluşturduğunuz işlem tarafından ayrılan sanal belleği ölçer. Bildirilen değer tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu ileti, işlemin Şu anda ayırdığı en fazla sanal bellek miktarını bayt (özel bayt) olarak bildirir. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıklarının erişebileceği sanal bellek konumlarını temsil eder.  
  
 32 bit makinede çalışan 32 bitlik işlemler için, işlem adres alanının özel bölümünün üst sınırı 2 GB 'dir. 32 bitlik süreçler, [/3 GB](https://go.microsoft.com/fwlink/?LinkId=177831) Boot. ini anahtarını kullanarak 3 GB 'a kadar sanal bellek alabilir. 64 bit makinede çalışan 32 bitlik bir işlem, 4 GB 'a kadar özel sanal bellek elde edebilir.  
  
 64 bit makinede çalışan 64 bitlik bir işlem, 8 TB 'a kadar özel sanal belleği elde edebilir.  
  
 Bildirilen değer, tüm ölçüm aralıklarının üzerinde profili oluşturulan işlemin etkin olduğu en fazla değerdir.  
  
 İşlem adres alanları hakkında daha fazla bilgi için Windows bellek yönetimi belgelerindeki [sanal adres alanı](https://go.microsoft.com/fwlink/?LinkId=177832) ' na bakın.  
  
## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma  
 Bildirilen değeri, programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kullanın.  
  
 İşlem adres alanının büyük bir bölümünü büyümeye yönelik mimari sınırına yaklaştığı en yüksek işlem özel bayt değeri, bellek dışı özel durumlara neden olabilir. Daha fazla bilgi için bkz. MSDN Magazine 'te [bellek sorunlarını araştırma](https://go.microsoft.com/fwlink/?LinkID=177833) .
