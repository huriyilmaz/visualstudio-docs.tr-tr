---
title: İşlev bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576587"
---
# <a name="function-expected"></a>İşlev bekleniyor
@No__t_1 nesnesi olmayan bir nesne üzerindeki **işlev prototipi** yöntemlerinden birini çağırmaya çalıştınız ya da bir işlev çağrısı bağlamında bir nesne kullandınız. Örneğin, aşağıdaki kod bu hatayı üretir çünkü **örnek** bir işlev değildir.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca `Function` nesnelerinde **işlev prototip** yöntemlerini çağırın.  
  
- Yalnızca işlevleri çağırmak için `()` işlev çağrısı işlecini kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Işlev nesnesi](../../javascript/reference/function-object-javascript.md)    
 [prototype Özelliği (Nesne)](../../javascript/reference/prototype-property-object-javascript.md)