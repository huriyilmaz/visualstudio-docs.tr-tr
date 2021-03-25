---
title: Yerel bir değeri değiştirme | Microsoft Docs
description: Yereller penceresinin değer alanına yeni bir değer yazıldığında bir yerel değerin değerini değiştirme işlemi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8baac2f0e288e9bde1288ed72e43d7f1d150d04
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055082"
---
# <a name="change-the-value-of-a-local"></a>Yerel bir değeri değiştirme
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 **Yereller** penceresinin değer alanına yeni bir değer yazıldığında, hata ayıklama paketi dizeyi, dize DEĞERLENDIRICI (ee) öğesine yazılı olarak geçirir. EE, bir basit değer veya ifade içerebilen bu dizeyi değerlendirir ve sonuçta elde edilen değeri ilişkili yerelde depolar.

 Bu, yerel bir değeri değiştirme işlemine genel bakış.

1. Kullanıcı yeni değeri girdikten sonra, Visual Studio yerel ile ilişkili [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesine [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) öğesini çağırır.

2. `IDebugProperty2::SetValueAsString` aşağıdaki görevleri gerçekleştirir:

   1. Dizeyi bir değer üretecek şekilde değerlendirir.

   2. Bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesi almak Için Ilişkili [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesini bağlar.

   3. Değeri bir bayt dizisine dönüştürür.

   4. , Hata ayıklamakta olan programın bunlara erişebilmesi için değerin baytlarını belleğe koymak için [DeğerBelirle](../../extensibility/debugger/reference/idebugobject-setvalue.md) çağırır.

3. Visual Studio **Locals** görüntüsünü yeniler (Ayrıntılar için bkz. [Locals görüntüleme](../../extensibility/debugger/displaying-locals.md) ).

   Bu yordam Ayrıca,  `IDebugProperty2` `IDebugProperty2` Yerel kendisiyle ilişkili nesne yerine kullanılan yerel değeri ile Ilişkili nesne dışında, Gözcü penceresindeki bir değişkenin değerini değiştirmek için de kullanılır.

## <a name="in-this-section"></a>Bu bölümde
 [Değişen değerlerin örnek uygulama](../../extensibility/debugger/sample-implementation-of-changing-values.md) Değerleri değiştirme işlemini adım adım yapmak için MyCEE örneğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)
