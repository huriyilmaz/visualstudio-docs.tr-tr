---
title: Yerel bir değeri değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782532"
---
# <a name="changing-the-value-of-a-local"></a>Yerel Bir Öğenin Değerini Değiştirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
   Bu yordam Ayrıca, **Watch** `IDebugProperty2` `IDebugProperty2` Yerel kendisiyle ilişkili nesne yerine kullanılan yerel değeri ile Ilişkili nesne dışında, izleme penceresindeki bir değişkenin değerini değiştirmek için de kullanılır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Örnek Değer Değiştirme Uygulaması](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Değerleri değiştirme işlemini adım adım yapmak için MyCEE örneğini kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR Ifade Değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Yerel Öğeleri Görüntüleme](../../extensibility/debugger/displaying-locals.md)
