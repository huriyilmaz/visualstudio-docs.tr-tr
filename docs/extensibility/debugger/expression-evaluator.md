---
title: İfade değerlendiricisi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738680"
---
# <a name="expression-evaluator"></a>İfade değerlendirici
Expression değerlendiricileri (EE), çalışma zamanında değişkenleri ve ifadeleri ayrıştırmak ve değerlendirmek için bir dilin söz dizimini inceleyerek, IDE kesme modundayken Kullanıcı tarafından görüntülenmesine izin verir.

## <a name="use-expression-evaluators"></a>Expression değerlendiricileri kullanma
 İfadeler, [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak şu şekilde oluşturulur:

1. Hata ayıklama altyapısı (DE) [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini uygular.

2. Hata ayıklama paketi bir `IDebugExpressionContext2` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden bir nesne alır ve sonra `IDebugStackFrame2::ParseText` bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi almak için bu yöntemi çağırır.

3. Hata ayıklama paketi, ifadenin değerini almak için [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) yöntemini veya [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemini çağırır. `IDebugExpression2::EvaluateAsync` Komut/komut penceresinden çağrılır. Tüm diğer kullanıcı arabirimi bileşenleri çağrısı `IDebugExpression2::EvaluateSync` .

4. İfade değerlendirmesinin sonucu, ifade değerlendirmesi sonucunun adını, türünü ve değerini içeren bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesidir.

   İfade değerlendirmesi sırasında, EE sembol sağlayıcısı bileşeninden bilgi gerektirir. Sembol sağlayıcısı, ayrıştırılmış ifadeyi tanımlamak ve anlamak için kullanılan sembolik bilgileri sağlar.

   Zaman uyumsuz ifade değerlendirmesi tamamlandığında, IDE 'ye ifade değerlendirmesi tamamlandığını bildirmek için, oturum hata ayıklama Yöneticisi (SDM) üzerinden DE zaman uyumsuz bir olay gönderilir. Ve sonra, değerlendirmenin sonucu `IDebugExpression2::EvaluateSync` yönteme döndürülür.

## <a name="implementation-notes"></a>Uygulama notları
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama motorları, ortak dil çalışma zamanı (CLR) arabirimlerini kullanarak ifade değerlendiricisi ile iletişim kurmasını bekler. Sonuç olarak, hata ayıklama altyapılarıyla birlikte çalışarak bir ifade değerlendirici [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] clr 'yi desteklemelidir (tüm clr hata ayıklama arabirimlerinin bir listesi, ' nin parçası olan debugref.doc bulunabilir [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] ).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
