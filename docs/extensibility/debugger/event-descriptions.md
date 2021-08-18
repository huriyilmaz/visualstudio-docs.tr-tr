---
title: Olay Açıklamaları | Microsoft Docs
description: Olay türleri ve kullanım nedenleri hakkında bilgi öğrenin. Her olay türünün belirli bir amacı vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4a9aae8668bbe2b0a92524ccfc5d8d0d18565fd80ea1a7dec2211f47e37f179d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342810"
---
# <a name="event-descriptions"></a>Olay açıklamaları
Her olay türünün belirli bir amacı vardır.

## <a name="events-and-the-reasons-for-their-use"></a>Olaylar ve kullanım nedenleri

|Olay|Açıklama|
|-----------|-----------------|
|Belge olaylarını etkinleştirme|Hata ayıklama altyapısı (DE), IDE'nin bir belgeyi açması veya ön plana getirmesini istediği zaman gerçekleşir.|
|Kesme noktası bağlı veya kesme noktası hata olayları|Bir kesme noktası bağlı olduğunda veya bir kesme noktası bağlanamazken gönderilir ve bir hata döndürülür.|
|Kesme noktası sınırsız olaylar|Bağlı bir kesme noktası koddan çıkar geldiğinde gerçekleşir.|
|Olayları durdurabilir|IDE'ye gönderip kullanıcının kodda belirtilen bir noktada durdurmak isteyip istemeyeceklerini belirleme.|
|Kesme noktası olayları|Bir koda veya veri kesme noktasına isabet olduğunda gerçekleşir.|
|Belge metni olayları|Belgede metin değiştiriken gerçekleşir. Bu olaylar yöntemi aracılığıyla `IDebugEventCallBack2::Event` gönderilmez.|
|Altyapı oluşturma olayları|Bir altyapı ilk oluşturulduğunda gönderilir.|
|Giriş noktası olayları|Hata ayıklaması yapılan program başlatma kodunu çalıştırarak ilk kullanıcı giriş noktasına ulaştığında gönderilir.|
|Özel durum olayları|Çalışan bir program özel bir özel durumla karşıdan geldiğinde gönderilir.|
|İfade değerlendirme tamamlama olayları|Zaman uyumsuz ifade değerlendirmesi tamamlandığında gönderilir.|
|Sembol olaylarını bulma|DE'nin kullanıcıdan modüle ait sembolleri bulmalarını istemesi gereken her zaman gönderilir.|
|Tam olayları yükleme|Yalnızca ilk program yükü tamamlandığında ve ilk kod programda çalıştırmak üzere olduğunda gönderilir.|
|İleti olayları|İletiler kullanıcılara gönder geldiğinde gönderilir.|
|Modül yükleme olayları|Yeni bir modül yüklendiğinde veya kaldırılmış olduğunda gönderilir.|
|Çıkış dizesi olayları|Program hata ayıklama çıkışı yazdığında gönderilir.|
|Olayları oluşturma ve yok etme|Visual Studio IDE'nin hata ayıklanan programların durumunu takip etmelerini için işlemlerin, programların, özelliklerin, oturumların ve iş parçacıklarının oluşturulmasını veya yok edilmesi duyurusuna gönderilir.|
|Adım tamamlama olayları|Bir adım tamamlandığında gönderilir.|
|İş parçacığı adı değişiklik olayları|Kullanıcı bir iş parçacığının adını değiştirirken gönderilir.|
|Program adı değişiklik olayları|Kullanıcı bir programın adını değiştirirken gönderilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Olayları gönderme](../../extensibility/debugger/sending-events.md)
