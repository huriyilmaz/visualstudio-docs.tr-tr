---
title: 'DA0502: Işlem tarafından profili oluşturulan en yüksek CPU kullanımı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a47a9c5964ccf15d2c609233eb600f39bc3ad2d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205930"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Profili oluşturulan İşlemin En Yüksek CPU kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0502 |  
| Kategori | Kaynak Izleme |  
| Profil oluşturma yöntemi | Tümü |  
| İleti | Bu kural yalnızca bilgi içindir. Işlem () \\ % Işlemci zamanı sayacı, profil oluşturduğunuz IŞLEMIN CPU tüketimini ölçer. Bildirilen değer tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir. |  
| Kural türü | Bilgilendirici |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin en uzun yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıkları arasında raporlanan en büyük değerdir. Yüzde 100 ' den fazla işlemciye sahip bir makinede yüzde ' den büyük olabilir.  
  
## <a name="how-to-use-the-rule-data"></a>Kural verilerini kullanma  
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kural değerini kullanın.
