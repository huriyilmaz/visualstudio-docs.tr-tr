---
title: Belge bağlamı | Microsoft Docs
description: Visual Studio hata ayıklamada belge bağlamı hakkında bilgi edinin. Bu, kaynak dosyadaki bir konumu veya bir kod bağlamı için kaynak belgedeki konumu temsil eder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d19830346ea09731dde608e019109f61011cd60
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915537"
---
# <a name="document-context"></a>Belge bağlamı
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama içinde, bir *belge bağlamı*:

- Kaynak dosyadaki bir konumu temsil eder. Kaynak dosyanın mevcut olmadığı diller için bir belge bağlamı, genellikle çalışma zamanı ortamı tarafından oluşturulan bir belgedeki konumu tanımlar. Örneğin, bir komut dosyası altyapısı betikten bir belge oluşturabilir. Daha fazla bilgi için bkz. [belge konumu](../../extensibility/debugger/document-position.md).

- Bir kod bağlamına karşılık gelen kaynak belgedeki konumu açıklar. Sembol işleyici, bir derleyici veya yorumlayıcı tarafından oluşturulan bilgileri kullanarak bir kod bağlamını belge bağlamına eşler.

- , Bir [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
- [Sembol sağlayıcısı arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
