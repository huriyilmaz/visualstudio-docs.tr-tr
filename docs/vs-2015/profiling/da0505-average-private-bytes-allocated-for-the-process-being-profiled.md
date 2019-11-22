---
title: 'DA0505: Işlem için ayrılan ortalama özel bayt sayısı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab96f8f6dea40adcf18847cf9503fd934f7ed3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300452"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: İşlem için izin verilen Ortalama Özel Bayt Sayısının profili oluşturuluyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0505 |  
| Kategori | Kaynak yönetimi |  
| Profil oluşturma yöntemi | Tümü |  
| İleti | Bu bilgiler yalnızca bilgi için toplanmıştı. Işlem özel baytları sayacı, profil oluşturduğunuz işlem tarafından ayrılan sanal belleği ölçer. Bildirilen değer tüm ölçüm aralıklarında hesaplanan ortalama değerdir. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu ileti, işlemin o anda ayrılan ortalama sanal bellek miktarını bayt (özel bayt) olarak bildirir. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıklarının erişebileceği sanal bellek konumlarını temsil eder.  
  
 32 bit makinede çalışan 32 bitlik işlemler için, işlem adres alanının özel bölümünün üst sınırı 2 GB 'dir. [/3Gb](https://go.microsoft.com/fwlink/?LinkId=177831) Boot. ini anahtarını kullanarak, 32 bitlik süreçler 3 GB 'a kadar sanal bellek alabilir. 64 bit makinede çalışan 32 bitlik bir işlem, 4 GB 'a kadar özel sanal bellek elde edebilir.  
  
 64 bit makinede çalışan 64 bitlik bir işlem, 8 TB 'a kadar özel sanal belleği elde edebilir.  
  
 Bildirilen değer, bir işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir.  
  
 İşlem adres alanları hakkında daha fazla bilgi için Windows bellek yönetimi belgelerindeki [sanal adres alanı](https://go.microsoft.com/fwlink/?LinkId=177832) ' na bakın.  
  
## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma  
 Bildirilen değeri, programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kullanın.
