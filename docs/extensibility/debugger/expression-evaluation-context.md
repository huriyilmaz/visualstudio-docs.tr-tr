---
title: İfade Değerlendirme Bağlamı | Microsoft Docs
description: İfade değerlendirmesi bağlamını temsil eden ve bir program kesme noktası durdurulmuş olduğunda var olan ifade değerlendirme bağlamı hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73eeafb95c7e4d52f69109c5eb7c06eb48bd8d88
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901220"
---
# <a name="expression-evaluation-context"></a>İfade değerlendirme bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada ifade **değerlendirme bağlamı:**

- İfade değerlendirmesi için bir bağlamı temsil eder. Genel olarak, bir değerlendirme bağlamı değişkenlerin, parametrelerin, işlevlerin ve yöntemlerin değerlendirilmesinde kullanılan sözcüksel kapsama karşılık gelen bir bağlamdır. Örneğin, bir yığın çerçevesiyle ilişkili ifade değerlendirme bağlamı yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini (varsa) değerlendirme bağlamını sağlar.

- Bir program kesme noktası durdurulurken var olur. İfadenin kendisi, verilen bağlam içinde bağlamaya ve değerlendirmeye hazır ayrıştırıldı ifadesini temsil eden bir veri yapısıdır.

     Daha ayrıntılı olarak ifadeler [ParseText yöntemi kullanılarak](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) oluşturulur. Bir ifade değerlendir geldiğinde, değişkenin veya bağımsız değişkenin adını ve türünü ve değerini içeren yazdırılabilir bir dize üretir. Bu dize, izleme penceresi veya IDE'nin Yereller penceresinde görüntülenir.

     Bir ve `BSTR` [bir IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimine sahip bir hata ayıklama altyapısı (DE), bir ifadeyi ayrıştırarak [bir IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi oluşturabilir. Bir `IDebugExpression2` arabirimde DE, zaman uyumlu veya zaman uyumsuz ifade değerlendirmesi aracılığıyla bir değer elde etmek için kullanılabilir. Bu değer, değişkenin veya bağımsız değişkenin adı ve türüyle birlikte görüntülenmek üzere IDE'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendirme arabirimleri](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md)
