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
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815337"
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
 [Normal Ifade nesnesi](../../javascript/reference/regular-expression-object-javascript.md)   
 [Normal Ifade sözdizimi (JavaScript)](https://msdn.microsoft.com/library/1400241x)