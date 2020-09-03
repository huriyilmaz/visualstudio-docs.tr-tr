---
title: Belge bağlamı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200578"
---
# <a name="document-context"></a>Belge Bağlamı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklama içinde, bir **belge bağlamı**:  
  
- Kaynak dosyadaki bir konumu temsil eder. Kaynak dosyanın mevcut olmadığı diller için bir belge bağlamı, genellikle çalışma zamanı ortamı tarafından oluşturulan bir belgedeki konumu tanımlar. Örneğin, bir komut dosyası altyapısı betikten bir belge oluşturabilir. Daha fazla bilgi için bkz. [belge konumu](../../extensibility/debugger/document-position.md).  
  
- Bir kod bağlamına karşılık gelen kaynak belgedeki konumu açıklar. Sembol işleyici, bir derleyici veya yorumlayıcı tarafından oluşturulan bilgileri kullanarak bir kod bağlamını belge bağlamına eşler.  
  
- , Bir [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi tarafından uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod bağlamı](../../extensibility/debugger/code-context.md)   
 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)   
 [Sembol sağlayıcısı arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)
