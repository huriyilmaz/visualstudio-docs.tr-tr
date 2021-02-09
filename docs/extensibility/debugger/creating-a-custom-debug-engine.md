---
title: Özel hata ayıklama altyapısı oluşturma | Microsoft Docs
description: Belirli çalışma zamanı mimarilerinin hata ayıklamasına izin veren bir hata ayıklama altyapısı oluşturma hakkında bilgi edinmek için bu makaleleri kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c0aa8550bc402520052003b59cf4ab1deaad7b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888972"
---
# <a name="create-a-custom-debug-engine"></a>Özel hata ayıklama altyapısı oluşturma
Hata ayıklama altyapısı (DE), belirli çalışma zamanı mimarilerinin hata ayıklamasına izin veren bir bileşendir. Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulama vardır.

> [!NOTE]
> Transact-SQL ve JScript için ayrı uygulamalar olsa da, VBScript ve JScript tek bir DE paylaşabilirsiniz.

 Aynı hata ayıklama hizmetlerini yürütme denetimi, kesme noktaları ve ifade değerlendirmesi olarak sağlamak için yorumlayıcı veya işlem sistemiyle birlikte da kullanılır. Bu hizmetler DE aynı arabirimler aracılığıyla uygulanır ve hata ayıklayıcının farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için bkz. [işletimsel modlar](../../extensibility/debugger/operational-modes.md).

 DE oluşturmak aşağıdaki adımlardan oluşur:

1. Visual Studio ile DE kaydetme

2. Bir programın ayıklanamayacağını etkinleştir

3. Yürütme denetimi ve durum değerlendirmesi uygulama

4. Olayları gönderme

5. Sonlandırma ve ayırmayı ayarlama

## <a name="in-this-section"></a>Bu bölümde
 [Özel bir hata ayıklama altyapısını kaydetme](../../extensibility/debugger/registering-a-custom-debug-engine.md) Kullanılabilmesi için, Visual Studio ile bir hata ayıklama altyapısını kaydetmek için gereken adımları açıklar.

 [Bir programın ayıklanamayacağını etkinleştir](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Aynı programda hata ayıklamanıza başlamadan önce, önce bunu başlatmanız veya mevcut bir programa iliştirmelisiniz.

 [Yürütme denetimi ve durum değerlendirmesi uygulama](../../extensibility/debugger/execution-control-and-state-evaluation.md) Uygulamanın hata ayıklamanın yürütme denetim özelliklerinin uygulanması gerektirdiğini açıklar.

 [Olayları gönder](../../extensibility/debugger/sending-events.md) DCOM tabanlı bir olay modeli olarak hata ayıklayıcı ile DE arasındaki iletişimi açıklar.

 [Sonlandırma ve ayırmayı ayarlama](../../extensibility/debugger/termination-and-detaching.md) Hata ayıklama için kesme noktası, özel durum, çalışma zamanı hataları veya hatalı döngüler olmadığı anlamına gelen normal sonlandırmanın nasıl yapılacağını açıklar.

 [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md) Hata ayıklama oturumunda gerçekleşen olayların arama sırasını belgeler.

 [Nasıl yapılır: özel hata ayıklama altyapısında hata ayıklama](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Özel bir DE hata ayıklamanın nasıl yapılacağını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
