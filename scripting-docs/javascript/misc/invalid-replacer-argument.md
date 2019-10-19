---
title: Geçersiz yeniden değiştirici bağımsız değişkeni | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573804"
---
# <a name="invalid-replacer-argument"></a>Geçersiz değiştirici bağımsız değişken
Geçerli olmayan bir bağımsız değişkenle `JSON.stringify` çağırma girişiminde bulunuldu. @No__t_0 bağımsız değişkeni bir işlev veya dizi olmalıdır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- @No__t_0 bağımsız değişkenini bir işlev veya dizi olarak değiştirin.  
  
## <a name="example"></a>Örnek  
 Bu örnekteki kod, `memberfilter` bir işlev veya dizi yerine bir nesne olduğundan, bir çalışma zamanı hatasına neden olur.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [JSON nesnesi](../../javascript/reference/json-object-javascript.md)    
 [JSON. Parse işlevi](../../javascript/reference/json-parse-function-javascript.md)    
 [JavaScript Çalışma zamanı Hataları](../../javascript/reference/javascript-run-time-errors.md)