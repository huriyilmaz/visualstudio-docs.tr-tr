---
title: İşlev bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2028d8923c2f81d1d99fec752d7ac0ce2fb32f65
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862180"
---
# <a name="function-expected"></a>İşlev bekleniyor
Nesne olmayan bir nesnede **işlev prototipi** yöntemlerinden birini çağırmaya çalıştınız ya da bir `Function` işlev çağrısı bağlamında bir nesne kullandınız. Örneğin, aşağıdaki kod bu hatayı üretir çünkü **örnek** bir işlev değildir.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Nesneler üzerinde yalnızca **işlev prototip** yöntemlerini çağırın `Function` .  
  
- İşlev çağrısı işlecini `()` yalnızca işlevleri çağırmak için kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İşlev nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype Özelliği (Nesne)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)