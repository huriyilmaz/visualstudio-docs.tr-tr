---
title: Kod bağlamı | Microsoft Docs
description: kodda bir program kesme noktasında durdurulduğunda var olan bir konumu açıklayan Visual Studio hata ayıklama içindeki kod bağlamı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 774daabac461c00998048455f4e23bd2ab7bd379
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627675"
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
