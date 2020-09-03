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
ms.openlocfilehash: f177bf81a43c45dcff4cef3040c64425ed544057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816975"
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
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [prototype Özelliği (Nesne)](../../javascript/reference/prototype-property-object-javascript.md)