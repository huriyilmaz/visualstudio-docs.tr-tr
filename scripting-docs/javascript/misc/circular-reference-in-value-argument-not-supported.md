---
title: Değer bağımsız değişkeninde döngüsel başvuru desteklenmiyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: aa753a4ba3e0254ed7de026653759bbdcfce0631
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862321"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Değer bağımsız değişkeninde döngüsel başvuru desteklenmez
`JSON.stringify`Geçerli olmayan bir değerle Invoke yapılmaya çalışıldı. `value`Bağımsız değişken, bir dizi veya nesne, döngüsel bir başvuru içerir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bağımsız değişkenden döngüsel başvuruyu kaldırın.  
  
## <a name="example"></a>Örnek  
 Bu örnekteki kod bir çalışma zamanı hatasına neden olur, çünkü `john` öğesine bir başvurusu vardır `mary` ve `mary` başvurusu vardır `john` . döngüsel başvuruyu kaldırmak için, `brother` `mary` nesneyi nesnesinden veya özelliğinden kaldırın ya da özellikten kaldırın `sister` `john` .  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [JSON nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [JSON. Parse Işlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript Çalışma zamanı Hataları](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)