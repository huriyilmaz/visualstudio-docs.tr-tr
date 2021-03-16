---
description: Numaralandırıcı dışında bir türün nesnesi üzerinde Numaralandırıcı. prototype. atEnd, Numaralandırıcı. prototype. Item, Numaralandırıcı. prototype. moveFirst ya da Numaralandırıcı. prototype. moveNext metodunu çağırmaya çalıştınız.
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
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571057"
---
# <a name="enumerator-object-expected"></a>Numaralandırıcı nesne bekleniyor
**Numaralandırıcı. prototype. atEnd, Numaralandırıcı. prototype. Item, Numaralandırıcı. prototype. MoveFirst, ya da** **Numaralandırıcı. prototype. MoveNext** metodunu dışında bir türün nesnesi üzerinde çağırmaya çalıştınız `Enumerator` . Bu tür çağrının nesnesinin türünde olması gerekir `Enumerator` . Bu kuralı kesen bir kod örneği aşağıda verilmiştir:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca türündeki nesnelerde **Numaralandırıcı. prototype. atEnd**, **Numaralandırıcı. prototype. Item**, **Numaralandırıcı. prototype. MoveFirst** ya da **Numaralandırıcı. prototype. MoveNext** yöntemlerini çağırır `Enumerator` . Nesnenizin bir nesne olup olmadığını öğrenmek için `Enumerator` şunu kullanın:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Numaralandırıcı Nesnesi](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
