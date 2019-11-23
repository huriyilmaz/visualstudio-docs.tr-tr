---
title: Throw sonrasında aynı kaynak satırındaki bir ifade gelmelidir | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572756"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw ardından aynı kaynak satırdaki bir ifade gelmelidir
`throw` anahtar sözcüğünü kullandınız, ancak aynı kaynak satırdaki bir ifadeyle izmedi. `throw` deyimi iki bölümden oluşur: `throw` anahtar sözcüğü ve sonra oluşturulacak ifade. Örneğin:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Bu iki bileşeni bölebilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `throw` anahtar sözcüğünün ve oluşturulacak ifadenin aynı satırda göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)   
 [throw deyimleri](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally Deyimi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)