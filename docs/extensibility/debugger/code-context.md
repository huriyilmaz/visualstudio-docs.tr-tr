---
title: Kod bağlamı | Microsoft Docs
description: Visual Studio hata ayıklamada kod bağlamı hakkında bilgi edinin. Bu, bir program kesme noktasında durdurulduğunda mevcut olan koddaki bir konumu açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c668cd1fa80efe24fa596cc4e9f311e2db519246
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055043"
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
