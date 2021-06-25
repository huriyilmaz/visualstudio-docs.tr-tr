---
title: Sunucular (Visual Studio SDK) | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir sunucunun tanımı ve rolü açıklanır.
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
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902130"
---
# <a name="servers-visual-studio-sdk"></a>Sunucular (Visual Studio SDK)
Hata ayıklayıcı mimarisinde bir *sunucu*:

- Bağlantı noktaları ve bağlantı noktası sağlayıcılarının bir kapsayıcısıdır ve oturum hata ayıklama Yöneticisi (SDM) ve hata ayıklama altyapılarına bağlantı noktalarını ve bağlantı noktası tedarikçilerini iletir.

- Kendisini adıyla tanımlayabilir ve bağlantı noktalarını ve bağlantı noktası tedarikçilerini numaralandırabilirsiniz.

- Yalnızca Visual Studio tarafından uygulanan bir [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) arabirimi tarafından temsil edilir (çalıştırılan her Visual Studio örneği için bir sunucu örneği).

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktaları](../../extensibility/debugger/ports.md)
- [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
