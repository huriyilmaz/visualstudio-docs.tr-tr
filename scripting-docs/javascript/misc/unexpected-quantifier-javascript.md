---
title: Beklenmeyen nicelik belirteci (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572527"
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