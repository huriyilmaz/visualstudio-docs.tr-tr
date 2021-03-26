---
title: Belge konumu | Microsoft Docs
description: Visual Studio hata ayıklama içindeki bir belge konumunun, IDE olarak bilinen bir kaynak dosyasındaki konumun bir soyutlamasını nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d14f9619059735aaecabf72adef248c69ed247e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097259"
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
