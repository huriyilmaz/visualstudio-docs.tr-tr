---
title: Sunucular (Visual Studio SDK) | Microsoft Docs
description: Bu makalede, Visual Studio'daki hata ayıklayıcı mimarisinde sunucunun tanımı ve rolü Visual Studio.
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
ms.openlocfilehash: 06317f9249371076ddc306ac5a38e3fe764996f7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626444"
---
# <a name="servers-visual-studio-sdk"></a>Sunucular (Visual Studio SDK)
Hata ayıklayıcısı mimarisinde bir *sunucu:*

- Bağlantı noktalarının ve bağlantı noktası sağlayıcılarının kapsayıcısıdır ve bağlantı noktalarını ve bağlantı noktası sağlayıcılarını oturum hata ayıklama yöneticisi (SDM) ve hata ayıklama altyapılarına iletir.

- Kendi kendini adıyla tanımlayabilir ve bağlantı noktalarını ve bağlantı noktası sağlayıcılarını numaralarına numaralatabilirsiniz.

- Yalnızca Visual Studio tarafından uygulanan [bir IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimiyle temsil Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
- [Bağlantı noktası sağlayıcıları](../../extensibility/debugger/port-suppliers.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
