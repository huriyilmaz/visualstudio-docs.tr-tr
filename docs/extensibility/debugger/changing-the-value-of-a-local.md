---
title: Yerel Bir Değer Değiştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739140"
---
# <a name="change-the-value-of-a-local"></a>Yerel bir değer değiştirme
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR ifade değerlendiricilerve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneğine](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 **Yereller** penceresinin değer alanına yeni bir değer yazıldığında, hata ayıklama paketi dizeyi, yazıldığında ifade değerlendiricisine (EE) geçirir. EE, basit bir değer veya ifade içerebilen bu dizeyi değerlendirir ve elde edilen değeri ilişkili yerel depolar.

 Bu, yerel bir yerelin değerini değiştirme işlemine genel bir bakıştır:

1. Kullanıcı yeni değeri girdikten sonra Visual Studio, yerel le ilişkili [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi üzerinde [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) çağırır.

2. `IDebugProperty2::SetValueAsString` aşağıdaki görevleri gerçekleştirir:

   1. Bir değer üretmek için dize değerlendirir.

   2. Bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) nesnesi elde etmek için ilişkili [IDebugField](../../extensibility/debugger/reference/idebugfield.md) nesnesini bağlar.

   3. Değeri bir bayt serisine dönüştürür.

   4. Değerin baytlarını belleğe koymak için [SetValue'i](../../extensibility/debugger/reference/idebugobject-setvalue.md) çağırır, böylece debugged olan program bunlara erişebilir.

3. Visual Studio **Yerel ekranını** yeniler (ayrıntılar için [yerel halkları görüntülemeye](../../extensibility/debugger/displaying-locals.md) bakın).

   Bu yordam, yerel kendisi ile ilişkili `IDebugProperty2` nesne yerine kullanılan yerel `IDebugProperty2` değeri ile ilişkili nesne dışında, **Watch** penceresinde bir değişkenin değerini değiştirmek için de kullanılır.

## <a name="in-this-section"></a>Bu bölümde
 [Değişen değerlerin örnek uygulaması](../../extensibility/debugger/sample-implementation-of-changing-values.md) Değerleri değiştirme işleminde adım atmak için MyCEE örneğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Yerel halkların görüntülenmesi](../../extensibility/debugger/displaying-locals.md)
