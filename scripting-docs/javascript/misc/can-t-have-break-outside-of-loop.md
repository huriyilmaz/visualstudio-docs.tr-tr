---
description: Break anahtar sözcüğünü bir döngü dışında kullanmaya çalıştınız.
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570654"
---
# <a name="cant-have-break-outside-of-loop"></a>Döngü dışında 'break' olamaz
**Break** anahtar sözcüğünü bir döngü dışında kullanmaya çalıştınız. **Break** anahtar sözcüğü, bir döngüyü veya ifadeyi sonlandırmak için kullanılır `switch` . Bir döngünün veya deyimin gövdesine katıştırılması gerekir `switch` . Ancak, bir **etiket** break anahtar kelimesini izleyebilir.  
  
```js
break labelname;  
```  
  
 Yalnızca iç içe geçmiş döngüleri veya deyimleri kullanırken  `switch` ve en içteki olmayan bir döngüden ayırmak gerektiğinde break anahtar sözcüğünün etiketli biçimine ihtiyacınız vardır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **Break** anahtar sözcüğünün kapsayan bir döngü veya switch ifadesinin içinde göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Break ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Program akışını denetleme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Komut Dosyalarınızda Sorun Giderme](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
