---
title: Belge bağlamı | Microsoft Docs
description: Visual Studio hata ayıklamada belge bağlamı hakkında bilgi edinin. Bu, kaynak dosyadaki bir konumu veya bir kod bağlamı için kaynak belgedeki konumu temsil eder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898194"
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
