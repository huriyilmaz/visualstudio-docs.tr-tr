---
description: Normal ifade arama düzeniniz oluştururken, geçersiz yineleme faktörüyle bir model öğesi oluşturdunuz.
title: Beklenmeyen nicelik belirteci (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9351f9306cea9e3f6346b007d6fe05c1d7bbf319
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571967"
---
# <a name="unexpected-quantifier-javascript"></a>Beklenmeyen niceleyici (JavaScript)
Normal ifade arama düzeniniz oluştururken, geçersiz yineleme faktörüyle bir model öğesi oluşturdunuz. Örneğin, model  
  
```js
/^+/  
```  
  
 ^ (girişin başında) öğesi bir yineleme faktörüyle sahip olmadığından geçersizdir. Aşağıdaki tabloda, yineleme faktörleri olmayan öğeler listelenmektedir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|^|Giriş başlangıcı|  
|$|Giriş sonu|  
|\b|Sözcük sınırı|  
|\B|Sözcük olmayan sınır|  
|*|Sıfır veya daha fazla tekrar|  
|+|Bir veya daha fazla tekrarda|  
|?|Sıfır veya bir tekrarda|  
|No|n tekrarları|  
|{n,}|n veya daha fazla tekrar|  
|{n, d}|N-k tekrarları, dahil|  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Arama deseninin öğesi yalnızca geçerli yineleme faktörleri içerdiğinden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Normal Ifade nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Normal Ifade sözdizimi (JavaScript)](/previous-versions/1400241x(v=vs.100))
