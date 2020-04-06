---
title: Özel Hata Ayıklama Motoru Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739033"
---
# <a name="create-a-custom-debug-engine"></a>Özel hata ayıklama altyapısı oluşturma
Hata ayıklama altyapısı (DE), belirli çalışma zamanı mimarilerinin hata ayıklanmasına izin veren bir bileşendir. Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulaması vardır.

> [!NOTE]
> Transact-SQL ve JScript için ayrı DE uygulamaları olsa da, VBScript ve JScript tek bir DE paylaşır.

 De, yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetlerini sağlamak için yorumlayıcı veya işlem sistemiyle birlikte çalışır. Bu hizmetler DE arabirimleri aracılığıyla uygulanır ve hata ayıklamanın farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için [Bkz. Operasyonel modlar.](../../extensibility/debugger/operational-modes.md)

 DE oluşturma aşağıdaki adımlardan oluşur:

1. Visual Studio ile BIR DE kaydolun

2. Bir programın debutlanmasını etkinleştirme

3. Yürütme denetimi ve durum değerlendirmesi uygulayın

4. Olayları gönderme

5. Sonlandırma ve ayırma ayarlama

## <a name="in-this-section"></a>Bu bölümde
 [Özel hata ayıklama altyapısı kaydetme](../../extensibility/debugger/registering-a-custom-debug-engine.md) Kullanılabilir, böylece bir hata ayıklama altyapısının Visual Studio'ya kaydedilmesi için gereken adımları açıklar.

 [Bir programın debutlanmasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) DE'niz bir programı hata ayıklamadan önce önce DE'yi başlatmanız veya varolan bir programa iliştirmeniz gerektiğini açıklar.

 [Yürütme denetimi ve durum değerlendirmesi uygulayın](../../extensibility/debugger/execution-control-and-state-evaluation.md) Bir uygulama hata ayıklama yürütme denetimi özellikleri uygulanmasını gerektirir neden tartışır.

 [Etkinlik gönderme](../../extensibility/debugger/sending-events.md) Hata ayıklama ve DE arasındaki iletişimi DCOM'a dayalı bir olay modeli olarak açıklar.

 [Sonlandırma ve ayırma ayarlama](../../extensibility/debugger/termination-and-detaching.md) Normal sonlandırmanın nasıl elde edilebildiğini açıklar, bu da uygulamada hata ayıklanacak kesme noktaları, özel durumlar, çalışma zamanı hataları veya sonsuz döngüler olmadığı anlamına gelir.

 [Hata ayıklama olaylarını arama](../../extensibility/debugger/calling-debugger-events.md) Hata ayıklama oturumunda meydana gelen olayların çağrı sırasını belgeler.

 [Nasıl Yapılsın: Özel hata ayıklama altyapısı hata ayıklama](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Özel bir DE hata ayıklama açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio hata ayıklama genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
