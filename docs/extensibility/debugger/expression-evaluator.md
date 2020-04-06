---
title: İfade Değerlendirici | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738680"
---
# <a name="expression-evaluator"></a>İfade değerlendiricisi
İfade değerlendiriciler (EE), bir dilin sözdizimini, değişkenleri ve ifadeleri çalışma zamanında ayrıştırmak ve değerlendirmek için inceler ve IDE kesme modundayken kullanıcı tarafından görüntülenmelerini sağlar.

## <a name="use-expression-evaluators"></a>İfade değerlendiricilerkullanın
 İfadeler [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak oluşturulur:

1. Hata ayıklama altyapısı (DE) [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini uygular.

2. Hata ayıklama paketi `IDebugExpressionContext2` bir [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden `IDebugStackFrame2::ParseText` bir nesne alır ve daha sonra bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi almak için üzerindeki yöntemi çağırır.

3. Hata ayıklama paketi, ifadenin değerini almak için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) yöntemini veya [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemini çağırır. `IDebugExpression2::EvaluateAsync`Komut/Hemen penceresinden çağrılır. Diğer tüm UI `IDebugExpression2::EvaluateSync`bileşenleri çağırır.

4. İfade değerlendirme sonucu, ifade değerlendirme sonucunun adını, türünü ve değerini içeren bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesidir.

   İfade değerlendirmesi sırasında, EE sembol sağlayıcı bileşeninden bilgi gerektirir. Sembol sağlayıcı, ayrışmış ifadeyi tanımlamak ve anlamak için kullanılan sembolik bilgileri sağlar.

   Eşsenkronize ifade değerlendirmesi tamamlandığında, de tarafından oturum hata ayıklama yöneticisi (SDM) aracılığıyla bir eşzamanlı olay gönderilir ve ifade değerlendirmesinin tamamladığını bildirir. Ve, değerlendirme sonucu daha sonra `IDebugExpression2::EvaluateSync` yönteme çağrı döndürülür.

## <a name="implementation-notes"></a>Uygulama notları
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama motorları, Ortak Dil Çalışma Zamanı (CLR) arabirimlerini kullanarak ifade değerlendiricisi ile konuşmayı bekler. Sonuç olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama motorları ile çalışan bir ifade değerlendirici CLR destek gerekir (tüm CLR hata ayıklama arabirimleri tam bir listesi [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]debugref.doc bulunabilir, hangi bir parçasıdır).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
