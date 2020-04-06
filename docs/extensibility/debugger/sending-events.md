---
title: Etkinlikler Gönderme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713038"
---
# <a name="send-events"></a>Olayları gönderme
Hata ayıklama ve hata ayıklama altyapısı (DE) arasındaki iletişim mekanizması DCOM'a dayalı bir olay modelidir. Olaylar COM nesneleri olarak gönderilir ve her olayın aşağıdakileri belirten parametreleri vardır:

- Olayı çağıran DE.

- Olanların tarifi.

- Olayın oluştuğu yerin bağlamını tanımlayan işlem, program ve iş parçacığı bilgileri. İşlem, de'den gönderilen olaylar için gönderilmez.

- Olayın senkron mu yoksa eşzamanlı mı olduğunu gösteren olay türü.

  Tüm hata ayıklama olayları [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)yöntemi kullanılarak gönderilir.

## <a name="in-this-section"></a>Bu bölümde
 [Olay kaynakları](../../extensibility/debugger/event-sources-visual-studio-sdk.md) İki olay kaynağını açıklar: hata ayıklama altyapısı (DE) ve oturum hata ayıklama yöneticisi (SDM).

 [Desteklenen etkinlik türleri](../../extensibility/debugger/supported-event-types.md) Şu anda desteklenen olay türlerini açıklar: asynchronous ve senkron.

 [Olay açıklamaları](../../extensibility/debugger/event-descriptions.md) Olayları ve kullanım nedenlerini tanımlar.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Hata ayıklama hizmetleri sağlamak için de'nin tercüman veya işletim sistemiyle nasıl çalıştığını açıklar.
