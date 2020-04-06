---
title: İfade Değerlendirme Bağlamı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738742"
---
# <a name="expression-evaluation-context"></a>İfade değerlendirme bağlamı
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklama, bir **ifade değerlendirme bağlamında:**

- İfade değerlendirmesi için bir bağlamtemsil eder. Genel olarak, bir değerlendirme bağlamı değişkenleri, parametreleri, işlevleri ve yöntemleri değerlendirmek için hangi sözlü kapsama karşılık gelir. Örneğin, yığın çerçevesiyle ilişkili bir ifade değerlendirme bağlamı, yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini (varsa) değerlendirmek için bağlamı sağlar.

- Bir program kesme noktasında durdurulduğunda var olabilir. İfadenin kendisi, verilen bağlam içinde bağlamaya ve değerlendirmeye hazır ayrıştırılmış bir ifadeyi temsil eden bir veri yapısıdır.

     Daha ayrıntılı olarak, ifadeler [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak oluşturulur. Bir ifade değerlendirildiğinde, değişken veya bağımsız değişkenin adını ve türünü ve değerini içeren yazdırılabilir bir dize oluşturur. Bu dize, İzleme penceresinde veya IDE'nin Yerel Ler penceresinde görüntülenir.

     Bir `BSTR` ve Bir [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi göz önüne alındığında, hata ayıklama altyapısı (DE) bir ifadeyi ayrıştırarak bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi oluşturabilir. Bir `IDebugExpression2` arabirim verildiğinde, DE senkron veya eşzamanlı ifade değerlendirmesi yoluyla bir değer elde edebilir. Bu değer, değişken in adı ve türü yle birlikte görüntülenmek üzere IDE'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendirme arabirimleri](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md)
