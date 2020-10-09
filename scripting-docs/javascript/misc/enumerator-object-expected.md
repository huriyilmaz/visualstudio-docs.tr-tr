---
title: Numaralandırıcı nesne bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862631"
---
# <a name="enumerator-object-expected"></a>Numaralandırıcı nesne bekleniyor
**Numaralandırıcı. prototype. atEnd, Numaralandırıcı. prototype. Item, Numaralandırıcı. prototype. MoveFirst, ya da** **Numaralandırıcı. prototype. MoveNext** metodunu dışında bir türün nesnesi üzerinde çağırmaya çalıştınız `Enumerator` . Bu tür çağrının nesnesinin türünde olması gerekir `Enumerator` . Bu kuralı kesen bir kod örneği aşağıda verilmiştir:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca türündeki nesnelerde **Numaralandırıcı. prototype. atEnd**, **Numaralandırıcı. prototype. Item**, **Numaralandırıcı. prototype. MoveFirst**ya da **Numaralandırıcı. prototype. MoveNext** yöntemlerini çağırır `Enumerator` . Nesnenizin bir nesne olup olmadığını öğrenmek için `Enumerator` şunu kullanın:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Numaralandırıcı Nesnesi](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)