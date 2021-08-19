---
title: Özel Hata Ayıklama Altyapısı | Microsoft Docs
description: Belirli çalışma zamanı mimarilerinin hata ayıklamasını sağlayan bir hata ayıklama altyapısı oluşturma hakkında bilgi edinmek için bu makaleleri kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: dd04ac2183b726d777b180e1be127efec2284135
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111768"
---
# <a name="create-a-custom-debug-engine"></a>Özel hata ayıklama altyapısı oluşturma
Hata ayıklama altyapısı (DE), belirli çalışma zamanı mimarilerinin hata ayıklamasını sağlayan bir bileşendir. Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulaması vardır.

> [!NOTE]
> Transact-SQL ve JScript için ayrı DE uygulamaları JScript, VBScript ve JScript de tek bir DE paylaşır.

 DE, yürütme denetimi, kesme noktaları ve ifade değerlendirmesi gibi hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işlem sistemiyle birlikte çalışır. Bu hizmetler DE arabirimleri aracılığıyla uygulanır ve hata ayıklayıcının farklı işlem modları arasında geçişe neden olabilir. Daha fazla bilgi için bkz. [İşletim modları.](../../extensibility/debugger/operational-modes.md)

 DE oluşturmak aşağıdaki adımlardan oluşur:

1. De'i Visual Studio

2. Bir programın hata ayıklamasını etkinleştirme

3. Yürütme denetimi ve durum değerlendirmesini uygulama

4. Olayları gönderme

5. Sonlandırmayı ve ayırmayı ayarlama

## <a name="in-this-section"></a>Bu bölümde
 [Özel hata ayıklama altyapısını kaydetme](../../extensibility/debugger/registering-a-custom-debug-engine.md) Bir hata ayıklama altyapısını Visual Studio için gereken adımları açıklar.

 [Bir programın hata ayıklamasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) DE'nizin bir programda hata ayıklaması için önce DE'i başlatmanız veya var olan bir programa eklemeniz gerektiğini açıklar.

 [Yürütme denetimi ve durum değerlendirmesini uygulama](../../extensibility/debugger/execution-control-and-state-evaluation.md) Bir uygulamada hata ayıklamanın neden yürütme denetimi özelliklerinin uygulanmasını gerektirdiğini tartışan.

 [Olayları gönderme](../../extensibility/debugger/sending-events.md) Hata ayıklayıcı ile DE arasındaki iletişimi DCOM tabanlı bir olay modeli olarak açıklar.

 [Sonlandırmayı ve ayırmayı ayarlama](../../extensibility/debugger/termination-and-detaching.md) Hata ayıklanacak uygulamada kesme noktası, özel durum, çalışma zamanı hatası veya sonsuz döngüler olmadığını ifade eder.

 [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md) Hata ayıklama oturumunda oluşan olayların çağırma sırasını belgeler.

 [Nasıl 2: Özel hata ayıklama altyapısında hata ayıklama](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Özel DE'de hata ayıklamayı açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
