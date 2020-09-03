---
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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815532"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw ardından aynı kaynak satırdaki bir ifade gelmelidir
`throw`Anahtar sözcüğünü kullandınız, ancak aynı kaynak satırdaki bir ifadeyle izmedi. `throw`Deyim iki bölümden oluşur: `throw` anahtar sözcüğü ve sonra oluşturulacak ifade. Örneğin:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Bu iki bileşeni bölebilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `throw`Anahtar sözcüğünün ve oluşturulacak ifadenin aynı satırda göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)   
 [throw ekstresi](../../javascript/reference/throw-statement-javascript.md)   
 [deneyin... yakala... finally ekstresi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)