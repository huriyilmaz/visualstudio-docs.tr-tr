---
title: Kod bağlamı | Microsoft Docs
description: Visual Studio hata ayıklamada kod bağlamı hakkında bilgi edinin. Bu, bir program kesme noktasında durdurulduğunda mevcut olan koddaki bir konumu açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e3bd252990e52f4ecaede0cc5026067b28434bc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905728"
---
# <a name="code-context"></a>Kod bağlamı
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama sırasında **kod bağlamı**:

- Hata ayıklama altyapısı (DE) tarafından bilinen kodda bir konumun soyutlamasını sağlar. Günümüzde çoğu çalışma zamanı mimarilerinde, bir programın yönerge akışında bir kod bağlamı adres olarak düşünülebilir. Geleneksel olmayan diller için kodun yönergelerle temsil edilebileceği durumlarda, bir kod bağlamı başka yollarla temsil edilebilir.

- Hata ayıklamakta olduğunuz programın yürütme akışındaki geçerli konumu açıklar.

- Yalnızca bir program kesme noktasında durdurulduğunda vardır.

- , İlişkili bir belge içeriğine sahiptir.

- , Bir [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimi tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge bağlamı](../../extensibility/debugger/document-context.md)
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
