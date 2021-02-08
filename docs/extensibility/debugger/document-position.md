---
title: Belge konumu | Microsoft Docs
description: Visual Studio hata ayıklama içindeki bir belge konumunun, IDE olarak bilinen bir kaynak dosyasındaki konumun bir soyutlamasını nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 42f85d0d15c46cfdfc2b76130649976d15035d7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840723"
---
# <a name="document-position"></a>Belge konumu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama sırasında bir *belge konumu*:

- IDE olarak bilinen bir kaynak dosyasındaki konumun bir soyutlamasını sağlar. Günümüzde çoğu dil için bir belge konumu kaynak dosyada konum olarak düşünülebilir.

- Bir kaynak belgede hata ayıklama altyapısına bir konum tanımlar.

- , Bir [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) arabirimi tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [Belge bağlamı](../../extensibility/debugger/document-context.md)
- [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
- [Sembol sağlayıcısı arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
