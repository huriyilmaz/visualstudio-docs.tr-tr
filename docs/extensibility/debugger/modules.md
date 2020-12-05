---
title: Modüller | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir modülün tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606651"
---
# <a name="modules"></a>Modül
Hata ayıklayıcı mimarisi açısından bir *Modül*:

- , Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- , Kendi simgelerini yeniden yükleyebilir ve kendisi tanımlayabilir. Modül açıklamaları IDE 'nin modüller penceresinde görüntülenir.

- , Modülü anlatmak için bir hata ayıklama altyapısı tarafından oluşturulan bir [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
