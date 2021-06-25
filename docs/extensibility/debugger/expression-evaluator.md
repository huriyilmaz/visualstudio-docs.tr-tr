---
title: İfade Değerlendirici | Microsoft Docs
description: Çalışma zamanında kesme modunda değişkenleri ve ifadeleri ayrıştırmak ve değerlendirmek için bir dilin söz dizimini inceleyen ifade değerlendiricileri hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 998f361d8008257cb8f4a888b4d4fbb985c9c977
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900986"
---
# <a name="expression-evaluator"></a>İfade değerlendirici
İfade değerlendiricileri (EE), çalışma zamanında değişkenleri ve ifadeleri ayrıştırmak ve değerlendirmek için bir dilin söz dizimini inceler ve IDE kesme modundayken kullanıcı tarafından sınanmalarını sağlar.

## <a name="use-expression-evaluators"></a>İfade değerlendiricileri kullanma
 İfadeler Aşağıdaki gibi [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak oluşturulur:

1. Hata ayıklama altyapısı (DE), [IDebugExpressionContext2 arabirimini](../../extensibility/debugger/reference/idebugexpressioncontext2.md) uygulama.

2. Hata ayıklama paketi bir `IDebugExpressionContext2` [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden bir nesnesi alır ve ardından `IDebugStackFrame2::ParseText` bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) nesnesi almak için bu nesne üzerinde yöntemini arar.

3. Hata ayıklama paketi, [ifadenin değerini](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) almak için EvaluateSync yöntemini veya [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) yöntemini çağırarak. `IDebugExpression2::EvaluateAsync` Komut/Hemen penceresinden çağrılır. Diğer tüm kullanıcı arabirimi bileşenleri çağrısında `IDebugExpression2::EvaluateSync` bulundu.

4. İfade değerlendirmesinin sonucu, ifade değerlendirmesinin sonucun adını, türünü ve değerini içeren [bir IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesidir.

   İfade değerlendirmesi sırasında EE, sembol sağlayıcısı bileşeninden bilgi gerektirir. Sembol sağlayıcısı ayrıştırilen ifadeyi tanımlamak ve anlamak için kullanılan sembolik bilgileri sağlar.

   Zaman uyumsuz ifade değerlendirmesi tamamlandığında, IDE'ye ifade değerlendirmesinin tamam olduğunu bildirmek için oturum hata ayıklama yöneticisi (SDM) aracılığıyla DE tarafından zaman uyumsuz bir olay gönderilir. Ardından, değerlendirmenin sonucu yöntemine yapılan çağrıdan `IDebugExpression2::EvaluateSync` döndürülür.

## <a name="implementation-notes"></a>Uygulama notları
 Hata ayıklama altyapıları, Common Language Runtime (CLR) arabirimlerini kullanarak ifade [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değerlendiricisi ile konuşmayı bekler. Sonuç olarak, hata ayıklama altyapıları ile çalışan bir ifade değerlendirici CLR'i desteklemeli (tüm CLR hata ayıklama arabirimlerinin tam listesi debugref.doc içinde bulunabilir ve bu da 'nin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir parçası). [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md)
