---
description: Throw anahtar sözcüğünü kullandınız, ancak aynı kaynak satırdaki bir ifadeyle izmedi.
title: Throw sonrasında aynı kaynak satırındaki bir ifade gelmelidir | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570719"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw ardından aynı kaynak satırdaki bir ifade gelmelidir
`throw`Anahtar sözcüğünü kullandınız, ancak aynı kaynak satırdaki bir ifadeyle izmedi. `throw`Deyim iki bölümden oluşur: `throw` anahtar sözcüğü ve sonra oluşturulacak ifade. Örnek:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Bu iki bileşeni bölebilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `throw`Anahtar sözcüğünün ve oluşturulacak ifadenin aynı satırda göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [deneyin... yakala... finally ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
