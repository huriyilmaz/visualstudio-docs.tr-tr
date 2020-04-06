---
title: Modüller | Microsoft Dokümanlar
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
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738354"
---
# <a name="modules"></a>Modüller
Hata ayıklama mimarisi açısından, bir *modül:*

- Yürütülebilir dosya veya DLL gibi fiziksel bir kod kapsayıcısıdır.

- Sembollerini yeniden yükleyebilir ve kendini tarif edebilir. Modül açıklamaları IDE'nin Modüller penceresinde görüntülenir.

- Modülü tanımlamak için hata ayıklama altyapısı tarafından oluşturulan bir [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
