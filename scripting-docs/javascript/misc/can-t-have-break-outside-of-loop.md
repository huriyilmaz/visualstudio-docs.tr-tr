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
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862806"
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
 [Break ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Program akışını denetleme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Komut Dosyalarınızda Sorun Giderme](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)