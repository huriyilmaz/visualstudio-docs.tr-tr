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
ms.openlocfilehash: 969f2bcb578d74ac02a7bdaa6984de5948e49e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817612"
---
# <a name="date-object-expected"></a>Tarih nesnesi bekleniyor
Dışındaki bir türün nesnesi üzerinde **date. prototype. ToString** veya **date. prototype.** bir yöntemini çağırmaya çalıştınız `Date` . Bu tür çağrının nesnesinin türünde olması gerekir `Date` . Örneğin:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca tür nesnelerinde **date. prototype. ToString** veya **date. prototype.** bir yöntemlerini çağırın `Date` .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Date nesnesi](../../javascript/reference/date-object-javascript.md)   
 [getDate metodu (Tarih)](../../javascript/reference/getdate-method-date-javascript.md)   
 [İç Nesneler](../../javascript/intrinsic-objects-javascript.md)