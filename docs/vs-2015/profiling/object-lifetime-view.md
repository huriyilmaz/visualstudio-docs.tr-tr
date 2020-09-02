---
title: Nesne ömrü görünümü | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef216c1220cbfda37da579d3ea2dfdd32837ab75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195564"
---
# <a name="object-lifetime-view"></a>Nesne Ömrü Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayrıca, performans oturumu özellik sayfalarında **.NET nesne yaşam süresi verilerini de topladığınızda** , nesne ömrü görünümü kullanılabilir.  
  
 Öğesinin atık toplayıcısı, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] uygulamanız için bellek ayırmayı ve serbest bırakma işlemini yönetir. Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanının atık toplayıcısı, nesil 0 ' da yeni nesneleri depolar. Tutulan koleksiyonlar, 1. ve 2. nesil içinde yükseltilerek saklanır.  
  
 Tüm nesnelerin neslini ayırmayı kaldırarak çöp toplayıcı geri kazanır belleği. Profili oluşturulmuş uygulama tarafından oluşturulan nesneler için, nesne ömrü görünümü nesnelerin sayısını ve boyutunu ve geri kazanıladıkları üretimi görüntüler.  
  
## <a name="general"></a>Genel  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Sınıf adı**|Ayrılmış türün sınıf adı.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI.|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|İşlevi içeren modülün yolu.|  
  
## <a name="instance-data"></a>Örnek verileri  
 Örnek verileri, profil oluşturma çalıştırmasında oluşturulan türdeki nesne sayısını ve nesnelerin çöp toplayıcı tarafından serbest bırakıldığı üretimi gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Örnekler**|Bu türdeki nesnelerin ayırma sayısı.|  
|**Toplam örnek yüzdesi**|Profil oluşturma çalıştırmasında yapılan toplam ayırma sayısının yüzdesi.|  
|**Toplanan Gen 0 örnekleri**|Çöp toplama algoritmasının 0 üretimi üzerinde serbest bırakılan tür örneklerinin sayısı.|  
|**Toplanan Gen 1 örnekleri**|Çöp toplama algoritmasının 1. kuşak öğesinde serbest bırakılmış olan türün örnek sayısı.|  
|**Toplanan Gen 2 örnekleri**|Çöp toplama algoritmasının 2. kuşak öğesinde serbest bırakılan tür örneklerinin sayısı.|  
|**Uçta etkin olan örnekler**|Profil oluşturma işleminin sonuna kadar serbest bırakılmayan tür örneklerinin sayısı.|  
  
## <a name="size-byte-data"></a>Boyut (bayt) verileri  
 Boyut (bayt) verileri, profil oluşturma çalıştırmasında oluşturulan türdeki nesnelerin boyutunu ve nesnelerin serbest bırakıldığı her nesil için geri kazanılan bellek miktarını gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ayrılan toplam bayt**|Türün tüm örnekleri için toplam bayt sayısı.|  
|**Toplam bayt yüzdesi**|Bu türün örnekleri için ayrılan, profil oluşturma çalıştırmasında toplam ayrılan bayt sayısının yüzdesi.|  
|**Toplanan Gen 0 bayt**|Çöp toplama algoritmasının 0 üretimi için serbest bırakılmış olan türdeki örneklerin boyutu.|  
|**Toplanan Gen 1 bayt**|Çöp toplama algoritmasının nesil 1 ' de serbest bırakılmış tür örneklerinin boyutu.|  
|**Gen 2 bayt toplandı**|Çöp toplama algoritmasının 2. kuşak öğesinde serbest bırakılan tür örneklerinin boyutu.|  
  
## <a name="large-object-heap-data"></a>Büyük nesne yığın verileri  
 .NET bellek ayırıcısı, Standart yönetilen yığından ayrı bir konumdaki çok büyük nesneleri yönetir. Büyük nesne yığını verileri, bu konumda yönetilen türdeki nesnelerin sayısını ve boyutunu gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Büyük nesne yığın örnekleri toplandı**|Bu türün, büyük nesne yığınında bulunan ve profil oluşturma çalıştırmasında toplanan örneklerinin sayısı.|  
|**Büyük nesne yığını toplanan bayt**|Büyük nesne yığınında bulunan ve profil oluşturma çalıştırmasında toplanan bu türün örneklerinin bayt cinsinden boyutu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
