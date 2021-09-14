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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 91011c021c429c5f09556f749e305572097a8de6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725837"
---
# <a name="modules"></a>Modül
Hata ayıklayıcısı mimarisi açısından bir *modül:*

- Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- Sembolleri yeniden yük içerebilir ve kendisini açıklar. Modül açıklamaları IDE'nin Modüller penceresinde görüntülenir.

- Modülü açıklamak için bir hata ayıklama altyapısı tarafından oluşturulan [bir IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimiyle temsil eder.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
