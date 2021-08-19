---
title: Yerel Bir | Microsoft Docs
description: Yereller penceresinin değer alanına yeni bir değer yazarak yerel değeri değiştirme işlemini öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ba6ea460d16491d651c52e9dec1ca430c33fefd6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145984"
---
# <a name="change-the-value-of-a-local"></a>Yerel değeri değiştirme
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Yereller penceresinin değer alanına yeni bir  değer yazgınca, hata ayıklama paketi dizeyi yazıldık şekilde ifade değerlendiricisine (EE). Bu EE, basit bir değer veya ifade içererek elde edilen değeri ilişkili yerelde depolandıran bu dizeyi değerlendirir.

 Bu, yerel bir değeri değiştirme sürecine genel bir bakıştır:

1. Kullanıcı yeni değeri girdikten sonra, Visual Studio [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesinde [SetValueAsString'i](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) çağırıyor.

2. `IDebugProperty2::SetValueAsString` aşağıdaki görevleri gerçekleştirir:

   1. Değer üretmek için dizeyi değerlendirir.

   2. Bir [IDebugObject nesnesi elde](../../extensibility/debugger/reference/idebugfield.md) etmek için ilişkili [IDebugField nesnesini](../../extensibility/debugger/reference/idebugobject.md) bağlar.

   3. Değeri bir bayt dizisine dönüştürür.

   4. Hata ayıklaması yapılan programın erişmesi için değerin baytlarını belleğe koymak için [SetValue'ya](../../extensibility/debugger/reference/idebugobject-setvalue.md) çağrılar.

3. Visual Studio yereller ekranı **yenilenir** (ayrıntılar [için bkz. Yerelleri](../../extensibility/debugger/displaying-locals.md) görüntüleme).

   Bu yordam ayrıca İzleme penceresindeki bir değişkenin değerini değiştirmek için de kullanılır, ancak yerelin kendisiyle ilişkili nesne yerine kullanılan yerel değeriyle ilişkili  `IDebugProperty2` `IDebugProperty2` nesnedir.

## <a name="in-this-section"></a>Bu bölümde
 [Değerleri değiştirme örneği uygulama](../../extensibility/debugger/sample-implementation-of-changing-values.md) Değerleri değiştirme sürecinde adım adım ilerley etmek için MyCEE örneğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)
