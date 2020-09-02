---
title: Koşullu derleme kapalı | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816130"
---
# <a name="conditional-compilation-is-turned-off"></a>Koşullu derleme kapalı
Koşullu derleme değişkenini, önce koşullu derlemeyi açmadan kullanmaya çalıştınız. Koşullu derlemeyi açmak [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] derleyiciye, koşullu derleme değişkenleri olarak @ ile başlayan tanımlayıcıları yorumlamasını söyler. Bunu, koşullu kodunuzu ifadesiyle başlayarak yapabilirsiniz:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Aşağıdaki ifadeyi, koşullu kodunuzun başlangıcına ekleyin:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Koşullu derleme](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Koşullu derleme değişkenleri](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Ekstre](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Ekstre](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Ekstre](../../javascript/reference/at-set-statement-javascript.md)