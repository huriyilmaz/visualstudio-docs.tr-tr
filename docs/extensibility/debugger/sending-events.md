---
title: Olay Gönderme | Microsoft Docs
description: Hata ayıklayıcısının ve hata ayıklama altyapısının DCOM'u temel alan bir olay modelini nasıl kullanabileceğini öğrenin. Olaylar COM nesneleri olarak gönderilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e9af2618150df522a459e47f312c1dc1e6a220c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902260"
---
# <a name="send-events"></a>Olayları gönderme
Hata ayıklayıcı ile hata ayıklama altyapısı (DE) arasındaki iletişim mekanizması, DCOM'u temel alan bir olay modelidir. Olaylar COM nesneleri olarak gönderilir ve her olayın şunları belirten parametreleri vardır:

- Olayı çağıran DE.

- Neler olduğunu açıklama.

- Olayın nerede meydana geldiği bağlamını tanımlayan işlem, program ve iş parçacığı bilgileri. İşlem, DE'den gönderilen olaylar için gönderilmez.

- Olayın zaman uyumlu mu yoksa zaman uyumsuz mu olduğunu gösteren olay türü.

  Tüm hata ayıklama olayları [IDebugEventCallback2::Event yöntemi kullanılarak gönderilir.](../../extensibility/debugger/reference/idebugeventcallback2-event.md)

## <a name="in-this-section"></a>Bu bölümde
 [Olay kaynakları](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Olayların iki kaynağı açıklandı: hata ayıklama altyapısı (DE) ve oturum hata ayıklama yöneticisi (SDM).

 [Desteklenen olay türleri](../../extensibility/debugger/supported-event-types.md) Şu anda desteklenen olay türlerini açıklama: zaman uyumsuz ve zaman uyumlu.

 [Olay açıklamaları](../../extensibility/debugger/event-descriptions.md) Olayları ve bunların kullanım nedenlerini tanımlar.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) De'nin hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işletim sistemiyle nasıl çalıştığını açıklar.
