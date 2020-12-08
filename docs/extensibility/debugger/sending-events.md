---
title: Olayları gönderme | Microsoft Docs
description: Hata ayıklayıcı ve hata ayıklama altyapısının DCOM 'a göre bir olay modeli nasıl kullandığını öğrenin. Olaylar COM nesneleri olarak gönderilir.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0262868ae442bfdd8b99c16f59e000f4ebfc35c5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847916"
---
# <a name="send-events"></a>Olayları gönderme
Hata ayıklayıcı ile hata ayıklama altyapısı (DE) arasındaki iletişim mekanizması DCOM 'u temel alan bir olay modelidir. Olaylar COM nesneleri olarak gönderilir ve her olayda şunları belirten parametreler bulunur:

- Olayı çağıran DE.

- Ne olduğunu görmek için bir açıklama.

- Olayın gerçekleştiği bağlamı tanımlayan işlem, program ve iş parçacığı bilgileri. İşlem, bir DE ile gönderilen olaylar için gönderilmez.

- Olayın zaman uyumlu veya zaman uyumsuz olduğunu gösteren olay türü.

  Tüm hata ayıklama olayları [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)yöntemi kullanılarak gönderilir.

## <a name="in-this-section"></a>Bu bölümde
 [Olay kaynakları](../../extensibility/debugger/event-sources-visual-studio-sdk.md) İki olay kaynağını açıklar: hata ayıklama altyapısı (DE) ve oturum hata ayıklama Yöneticisi (SDM).

 [Desteklenen olay türleri](../../extensibility/debugger/supported-event-types.md) Şu anda desteklenen olay türlerini açıklar: zaman uyumsuz ve zaman uyumlu.

 [Olay açıklamaları](../../extensibility/debugger/event-descriptions.md) Olayları ve kullanımları için nedenleri tanımlar.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Hata ayıklama hizmetleri sağlamak için bir DE yorumlayıcı veya işletim sistemiyle nasıl çalıştığını açıklar.
