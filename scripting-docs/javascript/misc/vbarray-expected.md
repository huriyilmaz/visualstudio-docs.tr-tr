---
title: VBArray bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b4e6521e5d363c21311b19e2ecc1679981acac3
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862701"
---
# <a name="vbarray-expected"></a>VBArray bekleniyor
Bir Visual Basic safeArray olmayan bir nesne (biri beklenirken) sağladınız.  
  
```js
new VBArray(safeArray);  
```  
  
 Vbarışınlar salt okunurdur ve doğrudan oluşturulamaz. SafeArray bağımsız değişkeni bir VBArray değeridir ve oluşturucuya geçirilmeden önce bir VBArray değeri almış olmalıdır `VBArray` . Bu, yalnızca varolan bir ActiveX veya başka bir nesneden değeri alarak yapılabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **VBArray** yapıcısına yalnızca **VBArray** nesneleri geçirdiğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VBArray nesnesi](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/VBArray)   
 [Dizileri kullanma](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)