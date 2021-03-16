---
description: İşlev sonucuna bir değer atamaya çalıştınız.
title: İşlev sonucuna atanamaz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 125d2dc7d41b1b65027952e4e6cb94ff97083e6e
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571928"
---
# <a name="cannot-assign-to-a-function-result"></a>İşlev sonucuna atanamaz
İşlev sonucuna bir değer atamaya çalıştınız. Bir işlevin sonucu bir değişkene atanabilir, ancak değişken olarak kullanılamaz. İşleve yeni bir değer atamak istiyorsanız ayraçları (işlev çağrısı işleci) atlayın. Aşağıdaki örnek, bu hatanın oluşturulduğu bir durumu gösterir.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bir işlev çağrısı sonucunun değerini, *atayabileceği* bir şey olarak kullanmayın. İşlev çağrısının sonucunu *bir değişkenine* atayabilirsiniz, ancak.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternatif olarak, işlevin kendisini (dönüş değerini değil) bir değişkene atayabilirsiniz.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İşlev nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [JavaScript kodu yazma](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web/JavaScript_basics)   
 [İşlevler](https://developer.mozilla.org/docs/Learn/JavaScript/Building_blocks/Functions)
