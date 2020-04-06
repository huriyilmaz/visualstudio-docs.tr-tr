---
title: Kod Bağlamı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739158"
---
# <a name="code-context"></a>Kod bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada, **kod bağlamı:**

- Hata ayıklama altyapısı (DE) tarafından bilindiği gibi koddaki bir konumun soyutlamasını sağlar. Günümüzde çoğu çalışma zamanı mimarisi için, bir kod bağlamı bir programın yönerge akışında bir adres olarak düşünülebilir. Kodun yönergeler tarafından temsil edilemeyebildiği geleneksel olmayan dillerde, kod bağlamı başka yollarla temsil edilebilir.

- Hata ayıklama programının yürütme akışındaki geçerli konumu açıklar.

- Yalnızca bir program bir kesme noktasında durdurulduğunda var olabilir.

- İlişkili bir belge bağlamı vardır.

- [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimi tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge bağlamı](../../extensibility/debugger/document-context.md)
- [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md)
