---
description: Tarih dışında bir türdeki nesne üzerinde Date. prototype. toString veya Date. prototype. bir yöntemini çağırmaya çalıştınız.
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
ms.openlocfilehash: 171514ae180c2e9b24e8aee56a23c47a909bd152
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571096"
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
