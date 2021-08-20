---
title: Modüller | Microsoft Docs
description: Bu makalede, Visual Studio hata ayıklayıcı mimarisinde bir modülün tanımı ve rolü açıklanır.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160367"
---
# <a name="modules"></a>Modül
Hata ayıklayıcı mimarisi açısından bir *Modül*:

- , Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- , Kendi simgelerini yeniden yükleyebilir ve kendisi tanımlayabilir. Modül açıklamaları IDE 'nin modüller penceresinde görüntülenir.

- , Modülü anlatmak için bir hata ayıklama altyapısı tarafından oluşturulan bir [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
