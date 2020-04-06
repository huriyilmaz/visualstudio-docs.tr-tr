---
title: Belge Bağlamı | Microsoft Dokümanlar
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
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738925"
---
# <a name="document-context"></a>Belge bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada, *belge bağlamında:*

- Kaynak dosyasındaki bir konumu temsil eder. Kaynak dosyanın bulunamayabileceği diller için belge bağlamı, çalışma zamanı ortamı tarafından oluşturulan bir belgedeki konumu tanımlar. Örneğin, komut dosyası altyapısı komut dosyasından bir belge oluşturabilir. Daha fazla bilgi için [Belge konumuna](../../extensibility/debugger/document-position.md)bakın.

- Kaynak belgedeki kod bağlamına karşılık gelen bir konumu açıklar. Sembol işleyicisi, derleyici veya yorumlayıcı tarafından oluşturulan bilgileri kullanarak bir kod bağlamını belgeleme bağlamına eşler.

- [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [Sembol sağlayıcı](../../extensibility/debugger/symbol-provider.md)
- [Sembol sağlayıcı Arayüzleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md)
