---
title: Olay açıklamaları | Microsoft Docs
description: Olay türleri ve kullanımları için nedenler hakkında bilgi edinin. Her olay türü için belirli bir amaç vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea477d3d21cd3b7a1a5352c736dc2f78195b99a4
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915615"
---
# <a name="event-descriptions"></a>Olay açıklamaları
Her olay türü için belirli bir amaç vardır.

## <a name="events-and-the-reasons-for-their-use"></a>Olaylar ve kullanımları için nedenler

|Olay|Description|
|-----------|-----------------|
|Belge olaylarını etkinleştir|Hata ayıklama altyapısı (DE) IDE 'nin bir belgeyi açmasını veya ön plana getirmeyi istediğinde oluşur.|
|Kesme noktası bağlantılı veya kesme noktası hata olayları|Bir kesme noktası bağlandığında veya bir kesme noktası bağlanıdığı zaman ve bir hata döndürüldüğünde gönderilir.|
|Kesme noktası ilişkisiz olaylar|Bağlı bir kesme noktası koddan bağlantısını kaldırmazsa oluşur.|
|Olayları durdurabilir|Kullanıcının kodda belirtilen bir noktada durdurulmasını isteyip istemediğinizi öğrenmek için IDE 'ye gönderilir.|
|Kesme noktası olayları|Bir kod veya veri kesme noktası isabet edildiğinde gerçekleşir.|
|Belge metin olayları|Belgedeki metin değiştirildiğinde gerçekleşir. Bu olaylar yöntemi aracılığıyla gönderilmez `IDebugEventCallBack2::Event` .|
|Altyapı oluşturma olayları|Bir altyapı ilk oluşturulduğunda gönderilir.|
|Giriş noktası olayları|Hata ayıklamakta olan programın başlatma kodunu çalıştırması ve ilk kullanıcı giriş noktasına ulaştığı zaman gönderilir.|
|Özel durum olayları|Çalışan bir program bir özel durumu ziyaret edildiğinde gönderilir.|
|İfade değerlendirmesi tamamlanma olayları|Zaman uyumsuz ifade değerlendirmesi tamamlandığında gönderilir.|
|Sembol olaylarını bul|Kullanıcının bir modül için sembolleri bulmasını istemesi her seferinde gönderilir.|
|Yük Tamam olayları|Yalnızca ilk program yükü tamamlandığında ve ilk kod programda çalışmak üzere olduğunda gönderilir.|
|İleti olayları|İletiler kullanıcılara gönderildiğinde gönderilir.|
|Modül yükleme olayları|Yeni bir modül yüklendiğinde veya kaldırıldığında gönderilir.|
|Çıkış dizesi olayları|Program hata ayıklama çıkışı yazdığında gönderilir.|
|Olayları oluşturma ve yok etme|Visual Studio IDE 'nin hata ayıklamakta olan programların durumunu izleyebilmesi için işlem, program, özellik, oturum ve iş parçacıklarının oluşturulmasını veya yok etmesini duyurmak için gönderilir.|
|Adım Tamam olayları|Bir adım tamamlandığında gönderilir.|
|İş parçacığı adı değişiklik olayları|Kullanıcı bir iş parçacığının adını değiştirdiğinde gönderilir.|
|Program adı değişiklik olayları|Kullanıcı bir programın adını değiştirdiğinde gönderilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Olayları gönderme](../../extensibility/debugger/sending-events.md)
