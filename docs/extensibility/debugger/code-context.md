---
title: Kod Bağlamı | Microsoft Docs
description: Hata ayıklamada program Visual Studio bir kesme noktası olduğunda var olan bir konumu açıklayan hata ayıklamada kod bağlamı hakkında bilgi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111807"
---
# <a name="code-context"></a>Kod bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada bir **kod bağlamı:**

- Hata ayıklama altyapısı (DE) olarak bilinen kodda bir konumun özetlerini sağlar. Günümüzde çoğu çalışma zamanı mimarisinde kod bağlamı, bir programın yönerge akışında adres olarak düşünebilirsiniz. Kodun yönergelerle temsili olmayan, koşulsuz diller için, kod bağlamı başka bir şekilde temsil olabilir.

- Hata ayıklamakta olduğunu programın yürütme akışındaki geçerli konumu açıklar.

- Yalnızca bir program kesme noktası durdurulmuşsa var olur.

- İlişkili bir belge bağlamına sahip.

- [IDebugCodeContext2 arabirimi tarafından](../../extensibility/debugger/reference/idebugcodecontext2.md) uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge bağlamı](../../extensibility/debugger/document-context.md)
- [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md)
