---
title: Olay açıklamaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5aff88047d6b1f79544af927751d7a053eeda218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152818"
---
# <a name="event-descriptions"></a>Olay Açıklamaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Her olay türü için belirli bir amaç vardır.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Olaylar ve kullanımları için nedenler  
  
|Olay|Açıklama|  
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
|Olayları oluşturma ve yok etme|Visual Studio IDE 'nin hata ayıklamakta olan programların durumunu izleyebilmesi için işlemlerin, programların, özelliklerin, oturumların ve iş parçacıklarının oluşturulmasını veya yok etmesini duyurmak için gönderilir.|  
|Adım Tamam olayları|Bir adım tamamlandığında gönderilir.|  
|İş parçacığı adı değişiklik olayları|Kullanıcı bir iş parçacığının adını değiştirdiğinde gönderilir.|  
|Program adı değişiklik olayları|Kullanıcı bir programın adını değiştirdiğinde gönderilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları Gönderme](../../extensibility/debugger/sending-events.md)
