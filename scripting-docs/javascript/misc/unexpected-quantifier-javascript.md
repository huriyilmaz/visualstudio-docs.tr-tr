---
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
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861851"
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