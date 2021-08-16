---
title: Bağlantı Noktası Sağlayıcı | Microsoft Docs
description: DCOM olmayan bir makinede hata ayıklarken veya yeni bir cihaz için destek gerektiğinde gerekli olan bir bağlantı noktası sağlayıcı uygulama hakkında bilgi alın.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 54960d2728fdf617db6c5e3d22f331a7e84c18fba9cf6d94e5140dab45e2916c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361138"
---
# <a name="implement-a-port-supplier"></a>Bağlantı noktası sağlayıcı uygulama
Bağlantı noktası sağlayıcı, oturum hata ayıklama yöneticisine (SDM) istek üzerine bağlantı noktaları sağlar. DCOM olmayan bir makinede hata ayıklarken veya yeni bir cihaz destek gerektirdiği zaman bir bağlantı noktası sağlayıcı uygulanıyor olması gerekir. Örneğin, bir cep telefonunda hata ayıklama sağlamak için, cep telefonuna (IR veya hücre bağlantısı üzerinden) bağlanan ve telefonda çalışan işlemleri ve programları numaralandıran bağlantı noktaları sağlayan bir bağlantı noktası tedarikçisi kurabilirsiniz.

 Windows tabanlı makinelerde (uzaktan hata ayıklama dahil) programlarda hata ayıklamak için Visual Studio yerel ve Ortak Dil Çalışma Zamanı (CLR) işlemleri için bağlantı noktası sağlayıcıları sağlar, bu nedenle bu durumlarda kendi bağlantı noktası tedarikçinizi ayarlamaya gerek yoktur.

## <a name="in-this-section"></a>Bu bölümde
 [Bağlantı noktası sağlayıcı uygulama ve kaydetme](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM'nin bağlantı noktası tedarikçi ve bağlantı noktalarıyla nasıl etkileşim kurarak etkileşime geçmeyi ele almaktadır.

 [Gerekli bağlantı noktası tedarikçi arabirimleri](../../extensibility/debugger/required-port-supplier-interfaces.md) Bir bağlantı noktası sağlayıcı almak için uygulamalı arabirimleri belgeler.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramlarını açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Studio ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
