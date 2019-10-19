---
title: Değer bağımsız değişkeninde döngüsel başvuru desteklenmiyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572342"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Değer bağımsız değişkeninde döngüsel başvuru desteklenmez
Geçerli olmayan bir değerle `JSON.stringify` çağırma girişiminde bulunuldu. @No__t_0 bağımsız değişkeni, bir dizi veya nesne, döngüsel bir başvuru içerir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bağımsız değişkenden döngüsel başvuruyu kaldırın.  
  
## <a name="example"></a>Örnek  
 Bu örnekteki kod bir çalışma zamanı hatasına neden olur çünkü `john` `mary` bir başvuruya sahiptir ve `mary` `john` bir başvuruya sahiptir. döngüsel başvuruyu kaldırmak için, `brother` özelliği `mary` nesnesinden veya `john` nesnesinden `sister` özelliğinden kaldırın ya da ayarını kaldırın.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [JSON nesnesi](../../javascript/reference/json-object-javascript.md)    
 [JSON. Parse işlevi](../../javascript/reference/json-parse-function-javascript.md)    
 [JavaScript Çalışma zamanı Hataları](../../javascript/reference/javascript-run-time-errors.md)