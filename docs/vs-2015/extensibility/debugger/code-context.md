---
title: Kod bağlamı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197370"
---
# <a name="code-context"></a>Kod Bağlamı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklama sırasında **kod bağlamı**:  
  
- Hata ayıklama altyapısı (DE) tarafından bilinen kodda bir konumun soyutlamasını sağlar. Günümüzde çoğu çalışma zamanı mimarilerinde, bir programın yönerge akışında bir kod bağlamı adres olarak düşünülebilir. Geleneksel olmayan diller için kodun yönergelerle temsil edilebileceği durumlarda, bir kod bağlamı başka yollarla temsil edilebilir.  
  
- Hata ayıklanan programın yürütme akışındaki geçerli konumu açıklar.  
  
- Yalnızca bir program kesme noktasında durdurulduğunda vardır.  
  
- , İlişkili bir belge içeriğine sahiptir.  
  
- , Bir [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimi tarafından uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Belge bağlamı](../../extensibility/debugger/document-context.md)   
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)
