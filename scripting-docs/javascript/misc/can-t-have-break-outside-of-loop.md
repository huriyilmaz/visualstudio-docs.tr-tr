---
title: Döngü dışında ' Break ' olamaz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576012"
---
# <a name="cant-have-break-outside-of-loop"></a>Döngü dışında 'break' olamaz
**Break** anahtar sözcüğünü bir döngü dışında kullanmaya çalıştınız. **Break** anahtar sözcüğü bir döngü veya `switch` ifadesini sonlandırmak için kullanılır. Döngü veya `switch` ifadesinin gövdesine katıştırılması gerekir. Ancak, bir **etiket** break anahtar kelimesini izleyebilir.  
  
```js
break labelname;  
```  
  
 Yalnızca iç içe geçmiş döngüler veya `switch` deyimlerini kullanırken ve en içteki olmayan bir döngüden ayırmak gerektiğinde **Break** anahtar sözcüğünün etiketli biçimine ihtiyacınız vardır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **Break** anahtar sözcüğünün kapsayan bir döngü veya switch ifadesinin içinde göründüğünden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Break ekstresi](../../javascript/reference/break-statement-javascript.md)    
 [Program Flow   denetleniyor](../../javascript/controlling-program-flow-javascript.md)  
 [Komut Dosyalarınızda Sorun Giderme](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)