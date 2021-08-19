---
title: Bir Programın Hata Ayıklamasını Etkinleştirme | Microsoft Docs
description: Bir programda hata ayıklamak için hata ayıklama altyapınızı başlatmayı veya var olan bir programa hata ayıklama altyapısını iliştirme hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 231934a246a5ce57f87bf08b134c0e288c6f5534
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138893"
---
# <a name="enable-a-program-to-be-debugged"></a>Bir programın hata ayıklamasını etkinleştirme
Hata ayıklama altyapınız (DE) bir programda hata ayıklamadan önce DE'i başlatmanız veya var olan bir programa eklemeniz gerekir.

## <a name="in-this-section"></a>Bu bölümde
 [Bağlantı noktası al](../../extensibility/debugger/getting-a-port.md) Bir programın hata ayıklamasını etkinleştirmenin ilk adımı olarak bir bağlantı noktasının nasıl alınacaklarını ele almaktadır.

 [Programı kaydetme](../../extensibility/debugger/registering-the-program.md) Bir programın hata ayıklamasını etkinleştirmenin sonraki adımını açıklar: bunu bağlantı noktasına kaydetme. Kaydedildiktan sonra, ekleme işlemi veya tam zamanında (JIT) hata ayıklama işlemiyle programda hata ayıklaması gerçek zamanlı olabilir.

 [Programa ekleme](../../extensibility/debugger/attaching-to-the-program.md) Sonraki adımı açıklar: hata ayıklayıcıyı programa ekleme.

 [Başlatma tabanlı ekleme](../../extensibility/debugger/launch-based-attachment.md) SDM tarafından başlatmadan sonra otomatik olan bir programa başlatma tabanlı eki açıklar.

 [Gerekli olayları gönderme](../../extensibility/debugger/sending-the-required-events.md) Hata ayıklama altyapısı (DE) oluşturma ve bunu bir programa ekleme sırasında gerekli olaylarda size yol sağlar.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Bir hata ayıklama altyapısını (DE) tanımlar ve DE arabirimleri aracılığıyla uygulanan hizmetleri ve hata ayıklayıcının farklı işlem modları arasında geçişe nasıl neden olduğunu açıklar.
