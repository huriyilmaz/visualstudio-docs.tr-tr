---
title: Bağlantı noktası sağlayıcısı uygulama | Microsoft Docs
description: DCOM olmayan bir makinede hata ayıklarken veya yeni bir cihaz destek gerektirdiğinde gerekli olan bir bağlantı noktası sağlayıcısı uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 98cc83ac9640241f0f97dc6e4adaacf8f90599b7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059918"
---
# <a name="implement-a-port-supplier"></a>Bağlantı noktası sağlayıcısı uygulama
Bir bağlantı noktası sağlayıcısı, oturum hata ayıklama Yöneticisi 'ne (SDM) istek üzerine bağlantı noktaları sağlar. DCOM olmayan bir makinede hata ayıklanırken veya yeni bir cihaz destek gerektirdiğinde, bir bağlantı noktası sağlayıcısı uygulanmalıdır. Örneğin, bir hücre telefonunda hata ayıklama sağlamak için, cep telefonuna (Belki IR veya bir hücre bağlantısı yoluyla) bağlanan bağlantı noktaları sağlayan bir bağlantı noktası sağlayıcısı ayarlayabilir ve telefonda çalışan işlem ve programları numaralandırır.

 Windows tabanlı makinelerde (uzaktan hata ayıklama dahil) programlarda hata ayıklama için, Visual Studio yerel ve ortak dil çalışma zamanı (CLR) işlemlerine yönelik bağlantı noktası sağlayıcıları sağlar, bu nedenle bu durumlarda kendi bağlantı noktası tedarikçinizi ayarlamaya gerek yoktur.

## <a name="in-this-section"></a>Bu bölümde
 [Bir bağlantı noktası sağlayıcısı uygulama ve kaydetme](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM 'nin bağlantı noktası tedarikçisiyle ve bağlantı noktalarıyla nasıl etkileşime gireceğini açıklar.

 [Gerekli bağlantı noktası sağlayıcısı arabirimleri](../../extensibility/debugger/required-port-supplier-interfaces.md) Bir bağlantı noktası sağlayıcısı almak için uygulamanız gereken arabirimlerin belgelerini alırlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
