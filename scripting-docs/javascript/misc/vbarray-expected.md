---
description: Bir Visual Basic safeArray olmayan bir nesne (biri beklenirken) sağladınız.
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
ms.openlocfilehash: e344e24b3fbef7b7f119a36513c222e085328072
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572084"
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
