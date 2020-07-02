---
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
ms.openlocfilehash: 84ec3426c80da0578dda7cb99e9160b81e31ab87
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817638"
---
# <a name="cannot-assign-to-a-function-result"></a>İşlev sonucuna atanamaz
İşlev sonucuna bir değer atamaya çalıştınız. Bir işlevin sonucu bir değişkene atanabilir, ancak değişken olarak kullanılamaz. İşleve yeni bir değer atamak istiyorsanız ayraçları (işlev çağrısı işleci) atlayın. Aşağıdaki örnek, bu hatanın oluşturulduğu bir durumu gösterir.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bir işlev çağrısı sonucunun değerini, *atayabileceği*bir şey olarak kullanmayın. İşlev çağrısının sonucunu *bir değişkenine* atayabilirsiniz, ancak.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternatif olarak, işlevin kendisini (dönüş değerini değil) bir değişkene atayabilirsiniz.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [JavaScript kodu yazma](../../javascript/writing-javascript-code.md)   
 [İşlevler](../../javascript/functions-javascript.md)