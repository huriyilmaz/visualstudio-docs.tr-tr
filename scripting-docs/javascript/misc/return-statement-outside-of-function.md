---
title: işlev dışında ' Return ' deyimleri | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 2ec17d9e421d06736a236e26dd5a1200a5564e7d
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862048"
---
# <a name="return-statement-outside-of-function"></a>'return' deyimi işlev dışı
`return`Kodunuzun genel kapsamında bir ifade kullandınız. `return`İfade yalnızca bir işlevin gövdesi içinde görünmelidir.  
  
 İşleci ile bir işlevi çağırmak `()` bir ifadedir. Tüm ifadelerde değerler vardır; `return` ifade, bir işlev tarafından döndürülen değeri belirtmek için kullanılır. Genel form:  
  
```js
  
return [ expression ];  
```  
  
 `return`Deyim yürütüldüğünde, *ifade* değerlendirilir ve işlevin değeri olarak döndürülür. İfade yoksa, **tanımsız** döndürülür.  
  
 İşlev `return` gövdesinde hala kalan başka deyimler olsa bile, işlevin yürütülmesi deyim yürütüldüğünde duraklar. Bu kuralın istisnası, **Return** ifadesinin bir **TRY** bloğunda oluşması ve buna karşılık gelen bir **finally** bloğunun olması durumunda, **finally** bloğundaki kod, işlev döndürmeden önce yürütülür.  
  
 Bir işlev, bir deyimi yürütmeden işlev gövdesinin sonuna ulaştığı için dönerse `return` , döndürülen değer **tanımsız** değerdir (Bu, işlev sonucunun daha büyük bir ifadenin parçası olarak kullanılamayacağı anlamına gelir).  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `return`Deyiminizi kodunuzun ana gövdesinden kaldırın (genel kapsam).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Return ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [İşlev nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [caller Özelliği (İşlev)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)