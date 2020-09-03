---
title: 'DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor. | Microsoft Belgeleri'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155769"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA501 |  
| Kategori | Kaynak Izleme |  
| Profil oluşturma yöntemi | Tümü |  
| İleti | Işlem tarafından ortalama CPU kullanımı profili oluşturuldu. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir. Değerin değeri, birden fazla işlemciye sahip bir makinede %100 değerinden büyük olabilir.  
  
## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma  
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.
