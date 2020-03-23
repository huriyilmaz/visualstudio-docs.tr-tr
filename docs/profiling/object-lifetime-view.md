---
title: Nesne Yaşam Boyu Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d4ea486930d0ea9f266b4ee57b69a50f7c570651
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772630"
---
# <a name="object-lifetime-view"></a>Nesne Ömrü Görünümü
Ayrıca **.NET nesne yaşam boyu verileri Performans** **Oturumu** özellik sayfalarında denetlendiğinde Nesne Ömrü görünümü kullanılabilir.

 .NET Framework'ün çöp toplayıcısı, uygulamanız için bellek tahsisini ve serbest bırakılmasını yönetir. Atık toplayıcının performansını optimize etmek için, yönetilen yığın üç nesle ayrılır: 0, 1 ve 2. Çalışma zamanının çöp toplayıcısı yeni nesneleri nesil 0'da depolar. Koleksiyonlardan kurtulan nesneler 1 ve 2.

 Çöp toplayıcı, tüm nesne neslini ayırarak belleği geri alır. Profilli uygulama tarafından oluşturulan nesneler için Object Lifetime görünümü, nesnelerin sayısını ve boyutunu ve geri alındıkları nesli görüntüler.

## <a name="general"></a>Genel

|Sütun|Açıklama|
|------------|-----------------|
|**Sınıf Adı**|Ayrılan türün sınıf adı.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği.|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|

## <a name="instance-data"></a>Örnek veriler
 Örnek verileri, profil oluşturma çalışmasında oluşturulan türdeki nesnelerin sayısını ve nesnelerin çöp toplayıcı tarafından ayrılarak oluşturulduğu nesli gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Örnekler**|Bu tür nesnelerin ayırma sayısı.|
|**Toplam Örnekler %**|Profil oluşturma çalışmasında yapılan toplam ayırma sayısının yüzdesi.|
|**Gen 0 Örnekleri Toplandı**|Çöp toplama algoritmasının nesil 0'ında ayrılan tür örneklerinin sayısı.|
|**Gen 1 Örnekleri Toplandı**|Çöp toplama algoritmasının 1.|
|**Gen 2 Örnekleri Toplandı**|Çöp toplama algoritmasının 2.|
|**Örnekler Alive At End**|Profil oluşturma çalışmasının sonuna kadar ayrılmamış tür örneklerinin sayısı.|

## <a name="size-byte-data"></a>Boyut (bayt) verileri
 Boyut (bayt) verileri, profil oluşturma çalışmasında oluşturulan türdeki nesnelerin boyutunu ve nesnelerin tahsis edildiği her nesilde geri alınan bellek miktarını gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Ayrılan Toplam Bayt Sayısı**|Türün tüm örnekleri için toplam bayt sayısı.|
|**Toplam Bayt %**|Profil oluşturma çalışmasında bu tür örnekler için ayrılan toplam bayt sayısının yüzdesi.|
|**Gen 0 Bayt Toplandı**|Çöp toplama algoritmasının nesil 0'ında ayrılan tür örneklerinin boyutu.|
|**Gen 1 Bayt Toplandı**|Çöp toplama algoritmasının 1.|
|**Gen 2 Bayt Toplandı**|Çöp toplama algoritmasının 2.|

## <a name="large-object-heap-data"></a>Büyük nesne yığını verileri
 .NET bellek ayırıcısı, standart yönetilen yığından ayrı bir konumda çok büyük nesneleri yönetir. Büyük nesne yığını verileri, bu konumda yönetilen türdeki nesnelerin sayısını ve boyutunu gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Toplanan Büyük Nesne Yığını Örnekleri**|Bu tür büyük nesne yığınında bulunan ve profil oluşturma çalışmasında toplanan örneklerin sayısı.|
|**Toplanan Büyük Nesne Yığını Baytları**|Büyük nesne yığınında bulunan ve profil oluşturma çalışmasında toplanan bu tür örneklerin baytlar halindeki boyutu.|

## <a name="see-also"></a>Ayrıca bkz.
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
