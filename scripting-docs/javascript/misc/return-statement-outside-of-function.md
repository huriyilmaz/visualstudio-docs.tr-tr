---
title: işlev dışında ' Return ' deyimleri | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573696"
---
# <a name="return-statement-outside-of-function"></a>'return' deyimi işlev dışı
Kodunuzun genel kapsamında bir `return` ifadesini kullandınız. `return` deyimin yalnızca bir işlevin gövdesinde görünmesi gerekir.  
  
 `()` işleci ile bir işlevi çağırmak bir ifadedir. Tüm ifadelerde değerler vardır; `return` deyimleri, bir işlev tarafından döndürülen değeri belirtmek için kullanılır. Genel form:  
  
```js
  
return [ expression ];  
```  
  
 `return` deyimi yürütüldüğünde, *ifade* değerlendirilir ve işlevin değeri olarak döndürülür. İfade yoksa, **tanımsız** döndürülür.  
  
 İşlev gövdesinde hala kalan başka deyimler olsa bile, işlevin yürütülmesi `return` deyimi yürütüldüğünde duraklar. Bu kuralın istisnası, **Return** ifadesinin bir **TRY** bloğunda oluşması ve buna karşılık gelen bir **finally** bloğunun olması durumunda, **finally** bloğundaki kod, işlev döndürmeden önce yürütülür.  
  
 Bir işlev, `return` deyimi yürütmeden işlev gövdesinin sonuna ulaştığı için döndürülürse, döndürülen değer **tanımsız** değerdir (Bu, işlev sonucunun daha büyük bir ifadenin parçası olarak kullanılamayacağı anlamına gelir).  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `return` ifadesini, kodunuzun ana gövdesinden kaldırın (genel kapsam).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [return ifadesinin](../../javascript/reference/return-statement-javascript.md)   
 [Işlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [caller Özelliği (İşlev)](../../javascript/reference/caller-property-function-javascript.md)