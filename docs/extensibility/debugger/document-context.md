---
title: Belge Bağlamı | Microsoft Docs
description: Kaynak dosyada bir Visual Studio veya kod bağlamı için kaynak belgede bir konumu temsil eden hata ayıklamada belge bağlamı hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 519a5903d01fb8a1abd37939cc7f29b325eae002e8a010db6ca5ca7c7614d7a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343065"
---
# <a name="document-context"></a>Belge bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada bir *belge bağlamı:*

- Kaynak dosyada bir konumu temsil eder. Kaynak dosyanın mevcut olmayan diller için, belge bağlamı genellikle çalışma zamanı ortamı tarafından oluşturulan bir belge konumunu tanımlar. Örneğin, bir betik altyapısı betikten bir belge oluşturabilirsiniz. Daha fazla bilgi için [bkz. Belge konumu.](../../extensibility/debugger/document-position.md)

- Kaynak belgede kod bağlamına karşılık gelen bir konumu açıklar. Sembol işleyicisi, derleyici veya yorumlayıcı tarafından oluşturulan bilgileri kullanarak bir kod bağlamını belge bağlamıyla eşler.

- Bir [IDebugDocumentContext2 arabirimi tarafından](../../extensibility/debugger/reference/idebugdocumentcontext2.md) uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)
- [Sembol sağlayıcısı Arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md)
