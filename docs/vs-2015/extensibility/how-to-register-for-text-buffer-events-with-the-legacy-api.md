---
title: 'Nasıl yapılır: eski API ile metin arabelleği olaylarını kaydetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204090"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Nasıl Yapılır: Eski API ile Metin Arabelleği Olaylarına Kaydolma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eski API 'yi kullanarak metin arabelleğine erişiyorsanız, aşağıdaki yordamda gösterildiği gibi metin arabelleği olaylarına kaydolmanız gerekir.  
  
### <a name="to-advise-text-buffer-events"></a>Metin arabelleği olaylarını bildirmek için  
  
1. Bir işaretçisinden, üzerindeki arayüzlerden birine yönelik <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> `QueryInterface` bir işaretçi çağrısı yapın <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Yöntemini çağırın <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> ve kaydetmek istediğiniz olayların ARABIRIM kimliğini geçirin.  
  
     Örneğin, için kaydolmak istiyorsanız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> IID_IVsTextLinesEvents ARABIRIM kimliğini geçirin.  
  
     Metin arabelleği <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> uygun bağlantı noktası nesnesi için arabirime bir işaretçi döndürür.  
  
3. Bu işaretçiyi kullanarak, kaydetmek istediğiniz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> olay arabirimi uygulamanıza bir işaretçi geçirerek yöntemi çağırın, örneğin, `IVsTextLinesEvents` arabirim.  
  
     Ortam, yöntemi çağırarak olayları dinlemeyi durdurmak için kullanabileceğiniz bir tanımlama bilgisi döndürür <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API'deki Metin Arabelleği Olayları](../extensibility/text-buffer-events-in-the-legacy-api.md)
