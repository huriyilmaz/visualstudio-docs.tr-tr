---
title: Bir Programın Debugged Olmasını Etkinleştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738899"
---
# <a name="enable-a-program-to-be-debugged"></a>Bir programın debutlanmasını etkinleştirme
Hata ayıklama altyapınız (DE) bir programı hata ayıklamadan önce DE'yi başlatmanız veya varolan bir programa iliştirmeniz gerekir.

## <a name="in-this-section"></a>Bu bölümde
 [Bir bağlantı noktası alın](../../extensibility/debugger/getting-a-port.md) Bir programın debugged olmasını etkinleştirmek için ilk adım olarak bir bağlantı noktası elde etmek için nasıl tartışır.

 [Programı kaydedin](../../extensibility/debugger/registering-the-program.md) Bir programın debugged olmasını etkinleştirmedeki bir sonraki adımı açıklar: bağlantı noktasına kaydetme. Bir kez kaydedildikten sonra, program ekleme işlemi veya tam zamanında (JIT) hata ayıklama işlemi ile debugged olabilir.

 [Programa ekle](../../extensibility/debugger/attaching-to-the-program.md) Bir sonraki adımı açıklar: hata ayıklamayı programa takmak.

 [Başlatma tabanlı ekleme](../../extensibility/debugger/launch-based-attachment.md) SDM tarafından başlatıldıktan sonra otomatik olarak başlatılan bir programa başlatma tabanlı eki açıklar.

 [Gerekli olayları gönderme](../../extensibility/debugger/sending-the-required-events.md) Hata ayıklama altyapısı (DE) oluştururken ve bir programa takarken gerekli olayları iletir.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Hata ayıklama altyapısını (DE) tanımlar ve DE arabirimleri aracılığıyla uygulanan hizmetleri ve hata ayıklamanın farklı çalışma modları arasında geçişe nasıl neden olabileceğini açıklar.
