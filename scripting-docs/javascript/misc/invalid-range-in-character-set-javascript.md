---
title: Karakter kümesinde geçersiz Aralık (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29f28f0ceeb6bd1bf0a8f28438afd803d3a9a9ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576629"
---
# <a name="invalid-range-in-character-set-javascript"></a>Geçersiz karakter kümesi aralığı (JavaScript)
Geçersiz karakter kümesi aralığı olan bir normal ifade oluşturmaya çalıştınız. Karakter kümeleri yalnızca-z veya 0-9 gibi tek karakterlerden oluşmalıdır. bir karakter kümesinde \w gibi karakter sınıfları dahil edilemez. Aralıktaki ilk karakter, aralıktaki ikinci karakterden önce de gelmelidir. Örneğin:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Normal ifade karakter kümesini oluşturmak için yalnızca tek karakterler kullanın ve doğru sırada olduklarından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Normal Ifade nesnesi](../../javascript/reference/regular-expression-object-javascript.md)   
 [Normal Ifade sözdizimi (JavaScript)](https://msdn.microsoft.com/library/1400241x)