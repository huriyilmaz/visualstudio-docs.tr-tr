---
title: sunucular (Visual Studio SDK) | Microsoft Docs
description: Bu makalede, Visual Studio hata ayıklayıcı mimarisinde bir sunucunun tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 402e6df722cb0c5e3bceb88614e0b137e3ef5e488378c357b3788a441e59baa4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432936"
---
# <a name="servers-visual-studio-sdk"></a>Sunucular (Visual Studio SDK)
Hata ayıklayıcı mimarisinde bir *sunucu*:

- Bağlantı noktaları ve bağlantı noktası sağlayıcılarının bir kapsayıcısıdır ve oturum hata ayıklama Yöneticisi (SDM) ve hata ayıklama altyapılarına bağlantı noktalarını ve bağlantı noktası tedarikçilerini iletir.

- Kendisini adıyla tanımlayabilir ve bağlantı noktalarını ve bağlantı noktası tedarikçilerini numaralandırabilirsiniz.

- yalnızca Visual Studio (Visual Studio çalıştıran her örnek için bir sunucu örneği) tarafından uygulanan bir [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
- [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
