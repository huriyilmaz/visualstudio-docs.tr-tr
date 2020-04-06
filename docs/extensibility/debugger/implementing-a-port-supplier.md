---
title: Liman Tedarikçisi Nin Uygulanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738562"
---
# <a name="implement-a-port-supplier"></a>Liman tedarikçisi uygulama
Bir bağlantı noktası tedarikçisi, oturum hata ayıklama yöneticisine (SDM) istek üzerine bağlantı noktaları sağlar. Bir bağlantı noktası tedarikçisi, DCOM olmayan bir makineye hata ayıklarken veya yeni bir cihaz destek gerektirdiğinde uygulanmalıdır. Örneğin, bir cep telefonuna hata ayıklama sağlamak için, cep telefonuna bağlanan bağlantı noktaları sağlayan (belki IR veya cep bağlantısı ile) ve telefonda çalışan işlemleri ve programları numaralandırmak için bir bağlantı noktası tedarikçisi ayarlayabilirsiniz.

 Windows tabanlı makinelerde (uzaktan hata ayıklama dahil) programları hata ayıklamak için Visual Studio, yerel ve Ortak Dil Çalışma Zamanı (CLR) işlemleri için bağlantı noktası tedarikçileri sağlar, bu nedenle bu gibi durumlarda kendi bağlantı noktası tedarikçinizi ayarlamanıza gerek yoktur.

## <a name="in-this-section"></a>Bu bölümde
 [Bir liman tedarikçisiuygulama ve kaydettirme](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM'nin liman tedarikçisi ve limanları ile nasıl etkileşimde bulunduğu açıklanmıştır.

 [Gerekli bağlantı noktası tedarikçisi arayüzleri](../../extensibility/debugger/required-port-supplier-interfaces.md) Bağlantı noktası tedarikçisi almak için uygulamanız gereken arabirimleri belgeler.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramları açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Studio hata ayıklama genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
