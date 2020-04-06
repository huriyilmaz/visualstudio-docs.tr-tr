---
title: Etkinlik Açıklamaları | Microsoft Dokümanlar
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
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738793"
---
# <a name="event-descriptions"></a>Olay açıklamaları
Her olay türünün belirli bir amacı vardır.

## <a name="events-and-the-reasons-for-their-use"></a>Olaylar ve kullanım nedenleri

|Olay|Açıklama|
|-----------|-----------------|
|Belge olaylarını etkinleştirme|Hata ayıklama altyapısı (DE) IDE'nin bir belgeyi açmasını veya ön plana çıkarmasını istediğinde oluşur.|
|Kesme noktası bağlama veya kesme noktası hata olayları|Kesme noktası bağlıyken veya bir kesme noktası bağlanamadığında ve bir hata döndürüldüğünde gönderilir.|
|Kopmaz nokta bağlanmamış olaylar|Bağlı bir kesme noktası koddan ayrılırsa oluşur.|
|Olayları durdurabilir|Kullanıcının kodda belirli bir noktada durmak isteyip istemeyeceğini belirlemek için IDE'ye gönderilir.|
|Kesme noktası olayları|Bir kod veya veri kesme noktası vurulduğunda oluşur.|
|Metin olaylarını belgeleme|Belgedeki metin değiştirildiğinde oluşur. Bu olaylar `IDebugEventCallBack2::Event` yöntem aracılığıyla gönderilmez.|
|Motor oluşturma olayları|Bir motor ilk oluşturulduğunda gönderilir.|
|Giriş noktası olayları|Debugged olan program başlatma kodunu çalıştırdığında ve ilk kullanıcı giriş noktasına ulaştığında gönderilir.|
|Özel durum olayları|Çalışan bir program özel bir özel durum çarptırıldığında gönderilir.|
|İfade değerlendirmesi tam olaylar|Eşzamanlı ifade değerlendirmesi tamamlandığında gönderilir.|
|Sembol olaylarını bul|DE bir modül için semboller bulmak için kullanıcı sormak gerektiğinde gönderilir.|
|Tam olayları yükleyin|Yalnızca ilk program yükü tamamlandığında ve ilk kod programda çalışmak üzereyken gönderilir.|
|İleti olayları|İletiler kullanıcılara gönderildiğinde gönderilir.|
|Modül yük olayları|Yeni bir modül yüklendiğinde veya boşaltıldığında gönderilir.|
|Çıkış dize olayları|Program hata ayıklama çıktısı yazdığında gönderilir.|
|Olayları oluşturma ve yok et|Visual Studio IDE'nin debugged olan programların durumunu takip edebilsin diye süreçlerin, programların, özelliklerin, oturumların ve iş parçacıklarının oluşturulmasını veya yok edilmesini duyurmak için gönderilir.|
|Etkinlikleri tamamla|Bir adım tamamlandığında gönderilir.|
|İş parçacığı adı değiştirme olayları|Kullanıcı iş parçacığının adını değiştirdiğinde gönderilir.|
|Program adı değiştirme olayları|Kullanıcı bir programın adını değiştirdiğinde gönderilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Etkinlik gönderme](../../extensibility/debugger/sending-events.md)
