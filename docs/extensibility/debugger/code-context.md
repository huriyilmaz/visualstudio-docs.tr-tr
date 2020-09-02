---
title: Kod bağlamı | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739158"
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
