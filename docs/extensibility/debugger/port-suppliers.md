---
title: Liman Tedarikçileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738309"
---
# <a name="port-suppliers"></a>Liman tedarikçileri
Hata ayıklama mimarisinde, bir *liman tedarikçisi:*

- Bir sunucu tarafından bulunur ve istek üzerine bu sunucuya bağlantı noktaları sağlar.

- Bağlantı noktaları ekleyebilir ve içerdiği sunucudan kaldırabilir.

- Sunucuya sağladığı tüm bağlantı noktalarını sayısalhale getirebilir.

- Kayıt defteri aracılığıyla Visual Studio'ya kayıtlı bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi tarafından temsil edilir. Bu arayüz [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)arayarak elde edilebilir.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]varsayılan bir bağlantı noktası tedarikçisi ve varsayılan bir bağlantı noktası sağlar. Özel bir bağlantı noktasının uygulanması gerekiyorsa, bu özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası tedarikçisinin de uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Bağlantı Noktaları](../../extensibility/debugger/ports.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
