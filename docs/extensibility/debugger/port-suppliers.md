---
title: Bağlantı noktası tedarikçileri | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738309"
---
# <a name="port-suppliers"></a>Bağlantı noktası tedarikçileri
Hata ayıklayıcı mimarisinde, bir *bağlantı noktası sağlayıcısı*:

- , Bir sunucu tarafından içerilir ve bu sunucuya istekte bağlantı noktaları sağlar.

- , İçeren sunucuya bağlantı noktaları ekleyebilir ve kaldırabilir.

- , Sunucu tarafından sağlanan tüm bağlantı noktalarını numaralandırabilirler.

- , Kayıt defteri aracılığıyla Visual Studio ile kaydedilen bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi tarafından temsil edilir. Bu arabirim [Getporttedarikçinin](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)çağırarak elde edilebilir.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Varsayılan bir bağlantı noktası tedarikçisi ve varsayılan bir bağlantı noktası sağlar. Özel bir bağlantı noktasının uygulanması gerekiyorsa, bu özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası tedarikçinin de uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
