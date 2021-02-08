---
title: Bir programın ayıklanamayacağını etkinleştirme | Microsoft Docs
description: Hata ayıklama altyapısını başlatma veya bir programda hata ayıklamak için hata ayıklama altyapısını mevcut bir programa iliştirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9dd31a9ff81493d0a315efc0ce0b607af0c6e422
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840671"
---
# <a name="enable-a-program-to-be-debugged"></a>Bir programın ayıklanamayacağını etkinleştir
Hata ayıklama altyapısından (DE) bir programda hata ayıklamadan önce, önce bunu başlatmanız veya mevcut bir programa bağlamanız gerekir.

## <a name="in-this-section"></a>Bu bölümde
 [Bağlantı noktası al](../../extensibility/debugger/getting-a-port.md) Bir programın ayıklanamayacağını etkinleştirmeye yönelik ilk adım olarak bir bağlantı noktasının nasıl alınacağını açıklar.

 [Programı kaydet](../../extensibility/debugger/registering-the-program.md) Bir programın hata ayıklamanın nasıl giderileceği konusunda bir sonraki adımı açıklar: bağlantı noktası ile kaydediliyor. Kaydolduktan sonra programa ekleme veya tam zamanında (JıT) hata ayıklama işlemi tarafından hata ayıklanabilir.

 [Programa iliştirme](../../extensibility/debugger/attaching-to-the-program.md) Bir sonraki adımı açıklar: hata ayıklayıcıyı programa ekleme.

 [Başlatma tabanlı iliştirme](../../extensibility/debugger/launch-based-attachment.md) , SDM tarafından başlatma sonrasında otomatik olan bir programa başlatma tabanlı ek açıklar.

 [Gerekli olayları gönder](../../extensibility/debugger/sending-the-required-events.md) Bir hata ayıklama altyapısı (DE) oluştururken ve bir programa iliştirirken gerekli olaylarda adım adım ilerleyin.

## <a name="related-sections"></a>İlgili bölümler
 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Bir hata ayıklama altyapısı (DE) tanımlar ve ayrıca, bu arabirimler aracılığıyla uygulanan Hizmetleri ve hata ayıklayıcının farklı çalışma modları arasında geçişine neden olabilecekleri hizmetleri açıklar.
