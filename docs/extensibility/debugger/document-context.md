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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be2e5e168b232f120a22e7e4b39352008fee7418
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840762"
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
