---
title: Olayları gönderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204736"
---
# <a name="sending-events"></a>Olayları Gönderme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı ile hata ayıklama altyapısı (DE) arasındaki iletişim mekanizması DCOM 'u temel alan bir olay modelidir. Olaylar COM nesneleri olarak gönderilir ve her olayda aşağıdakileri belirten parametreler bulunur:  
  
- Olayı çağıran DE.  
  
- Ne olduğunu görmek için bir açıklama.  
  
- Olayın gerçekleştiği bağlamı tanımlayan işlem, program ve iş parçacığı bilgileri. İşlem, bir DE ile gönderilen olaylar için gönderilmez.  
  
- Olayın zaman uyumlu veya zaman uyumsuz olduğunu gösteren olay türü.  
  
  Tüm hata ayıklama olayları [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)yöntemi kullanılarak gönderilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Olay kaynakları](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 İki olay kaynağını açıklar: hata ayıklama altyapısı (DE) ve oturum hata ayıklama Yöneticisi (SDM).  
  
 [Desteklenen Olay Türleri](../../extensibility/debugger/supported-event-types.md)  
 Şu anda desteklenen olay türlerini açıklar: zaman uyumsuz ve zaman uyumlu.  
  
 [Olay Açıklamaları](../../extensibility/debugger/event-descriptions.md)  
 Olayları ve kullanımları için nedenleri tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Hata ayıklama hizmetleri sağlamak için bir DE yorumlayıcı veya işletim sistemiyle nasıl çalıştığını açıklar.
