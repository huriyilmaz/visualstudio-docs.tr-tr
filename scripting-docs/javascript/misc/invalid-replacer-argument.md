---
description: JSON çağırma girişimi, geçerli olmayan bir bağımsız değişkenle JSON. stringbelirt çağrısı yapıldı.
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
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570901"
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
 [JSON nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse Işlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript Çalışma zamanı Hataları](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
