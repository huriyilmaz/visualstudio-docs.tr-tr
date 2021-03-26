---
title: Sunucular (Visual Studio SDK) | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir sunucunun tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7bb19262d4ce5fd1b3139f05cd9bbc57131db1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070368"
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
