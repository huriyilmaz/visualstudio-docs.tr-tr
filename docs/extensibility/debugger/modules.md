---
title: Modüller | Microsoft Docs
description: Bu makalede, modülde hata ayıklayıcı mimarisinde modülün tanımı ve rolü Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902611"
---
# <a name="modules"></a>Modül
Hata ayıklayıcısı mimarisi açısından bir *modül:*

- Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- Sembolleri yeniden yük içerebilir ve kendisini açıklar. Modül açıklamaları IDE'nin Modüller penceresinde görüntülenir.

- Modülü açıklamak için bir hata ayıklama altyapısı tarafından oluşturulan [bir IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimiyle temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
