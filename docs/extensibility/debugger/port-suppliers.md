---
title: Port Suppliers | Microsoft Docs
description: Bu makalede, Visual Studio'da hata ayıklayıcı mimarisinde bir bağlantı noktası sağlayıcının tanımı ve Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 098e1546dea997f83f0c73b5d337657b1a8d77a8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725828"
---
# <a name="port-suppliers"></a>Bağlantı noktası sağlayıcıları
Hata ayıklayıcısı mimarisinde bir bağlantı *noktası sağlayıcı:*

- Bir sunucu tarafından bulunur ve bu sunucuya istek üzerine bağlantı noktaları sağlar.

- Bağlantı noktalarını içeren sunucuya ekleyebilir ve kaldırabilir.

- Sunucuya sağladığı tüm bağlantı noktalarını numara olarak numaralara uzer.

- Kayıt defteri aracılığıyla bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimiyle temsil Visual Studio ile kaydedilir. Bu arabirim [GetPortSupplier çağrılarak elde edilir.](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , varsayılan bir bağlantı noktası sağlayıcı ve varsayılan bir bağlantı noktası sağlar. Özel bir bağlantı noktasının uygulanması gerekirse, bu özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası sağlayıcının da uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
