---
title: Döngü dışında ' Break ' olamaz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817664"
---
# <a name="cant-have-break-outside-of-loop"></a>Döngü dışında 'break' olamaz
**Break** anahtar sözcüğünü bir döngü dışında kullanmaya çalıştınız. **Break** anahtar sözcüğü, bir döngüyü veya ifadeyi sonlandırmak için kullanılır `switch` . Bir döngünün veya deyimin gövdesine katıştırılması gerekir `switch` . Ancak, bir **etiket** break anahtar kelimesini izleyebilir.  
  
```js
break labelname;  
```  
  
 Yalnızca iç içe geçmiş döngüleri veya deyimleri kullanırken **break** `switch` ve en içteki olmayan bir döngüden ayırmak gerektiğinde break anahtar sözcüğünün etiketli biçimine ihtiyacınız vardır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **Break** anahtar sözcüğünün kapsayan bir döngü veya switch ifadesinin içinde göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Break ekstresi](../../javascript/reference/break-statement-javascript.md)   
 [Program akışını denetleme](../../javascript/controlling-program-flow-javascript.md)   
 [Komut Dosyalarınızda Sorun Giderme](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)