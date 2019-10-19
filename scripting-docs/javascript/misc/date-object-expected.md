---
title: Tarih nesnesi bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572892"
---
# <a name="date-object-expected"></a>Tarih nesnesi bekleniyor
@No__t_2 dışında bir türün nesnesi üzerinde **date. prototype. ToString** veya **date. prototype.** bir yöntemini çağırmaya çalıştınız. Bu tür çağrının nesnesinin `Date` türünde olması gerekir. Örneğin:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- @No__t_2 türündeki nesnelerde yalnızca **date. prototype. ToString** veya **date. prototype.** bir yöntemi çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Tarih nesnesi](../../javascript/reference/date-object-javascript.md)    
 [getdate metodu (Tarih)](../../javascript/reference/getdate-method-date-javascript.md)    
 [İç Nesneler](../../javascript/intrinsic-objects-javascript.md)