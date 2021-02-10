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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60c214fce57f5958d8b30ca231c3e8a2bc05194
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960812"
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
