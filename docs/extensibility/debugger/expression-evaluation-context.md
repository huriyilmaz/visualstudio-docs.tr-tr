---
title: İfade değerlendirme bağlamı | Microsoft Docs
description: İfade değerlendirmesi bağlamını temsil eden ifade değerlendirme bağlamı hakkında bilgi edinin ve bir program kesme noktasında durdurulduğunda vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4555cf1431b23766085a4174223d3f880d08df45
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089569"
---
# <a name="expression-evaluation-context"></a>İfade değerlendirme bağlamı
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hata ayıklama sırasında **ifade değerlendirme bağlamı**:

- İfade değerlendirmesi için bir bağlamı temsil eder. Genellikle, bir değerlendirme bağlamı değişkenleri, parametreleri, işlevleri ve yöntemleri değerlendirmek için içindeki sözcük temelli kapsama karşılık gelir. Örneğin, yığın çerçevesiyle ilişkili bir ifade değerlendirme bağlamı yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini (varsa) değerlendirmek için bağlam sağlar.

- Bir program kesme noktasında durdurulduğunda vardır. İfade, belirtilen bağlam içinde bağlama ve değerlendirme için hazırlanma bir ayrıştırılmış ifadeyi temsil eden bir veri yapısıdır.

     Daha ayrıntılı olarak, ifadeler [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) yöntemi kullanılarak oluşturulur. Bir ifade değerlendirildiğinde, değişken veya bağımsız değişkenin adını ve türünü ve değerini içeren yazdırılabilir bir dize oluşturur. Bu dize izleme penceresi veya IDE 'nin Yereller penceresinde görüntülenir.

     Ve bir `BSTR` [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimi verildiğinde, bir hata ayıklama altyapısı (de) bir ifadeyi ayrıştırarak bir [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) arabirimi oluşturabilir. Bir `IDebugExpression2` arabirim verildiğinde, de zaman uyumlu veya zaman uyumsuz ifade değerlendirmesi aracılığıyla bir değer alabilir. Bu değer, değişkenin veya bağımsız değişkenin adı ve türü ile birlikte görüntülenmek üzere IDE 'ye gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [İfade değerlendirme arabirimleri](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)
