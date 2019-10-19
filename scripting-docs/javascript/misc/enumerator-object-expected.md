---
title: Numaralandırıcı nesne bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572872"
---
# <a name="enumerator-object-expected"></a>Numaralandırıcı nesne bekleniyor
@No__t_2 dışında bir türün nesnesi üzerinde **Numaralandırıcı. prototype. atEnd, Numaralandırıcı. prototype. Item, Numaralandırıcı. prototype. MoveFirst ya da** **Numaralandırıcı. prototype. MoveNext** metodunu çağırmaya çalıştınız. Bu tür çağrının nesnesinin `Enumerator` türünde olması gerekir. Bu kuralı kesen bir kod örneği aşağıda verilmiştir:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca `Enumerator` türündeki nesnelerde **Numaralandırıcı. prototype. atEnd**, **Numaralandırıcı. prototype. Item**, **Numaralandırıcı. prototype. MoveFirst**, ya da **Numaralandırıcı. prototype. MoveNext** yöntemlerini çağırır. Nesnenizin bir `Enumerator` nesnesi olup olmadığını öğrenmek için şunu kullanın:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Numaralandırıcı Nesnesi](../../javascript/reference/enumerator-object-javascript.md)