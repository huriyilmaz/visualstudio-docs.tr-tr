---
title: Geçersiz yeniden değiştirici bağımsız değişkeni | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 452af60c37e4a56996438cc2957e9b69ccee98ef
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816832"
---
# <a name="invalid-replacer-argument"></a>Geçersiz değiştirici bağımsız değişken
`JSON.stringify`Geçerli olmayan bir bağımsız değişkenle Invoke yapılmaya çalışıldı. `replacer`Bağımsız değişken bir işlev veya dizi olmalıdır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `replacer`Bağımsız değişkeni bir işlev veya dizi olarak değiştirin.  
  
## <a name="example"></a>Örnek  
 Bu örnekteki kod, bir `memberfilter` işlev veya dizi yerine bir nesne olduğundan, bir çalışma zamanı hatasına neden olur.  
  
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
 [JSON. Parse Işlevi](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript Çalışma zamanı Hataları](../../javascript/reference/javascript-run-time-errors.md)