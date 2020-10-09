---
title: Tarih nesnesi bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862643"
---
# <a name="date-object-expected"></a>Tarih nesnesi bekleniyor
Dışındaki bir türün nesnesi üzerinde **date. prototype. ToString** veya **date. prototype.** bir yöntemini çağırmaya çalıştınız `Date` . Bu tür çağrının nesnesinin türünde olması gerekir `Date` . Örnek:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca tür nesnelerinde **date. prototype. ToString** veya **date. prototype.** bir yöntemlerini çağırın `Date` .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Date nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [getDate metodu (Tarih)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [İç Nesneler](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)