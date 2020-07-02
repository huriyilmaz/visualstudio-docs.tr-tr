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
ms.openlocfilehash: 09ab257e6c473e2747a24559200e7b1f432d5687
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815285"
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
 [VBArray nesnesi](../../javascript/reference/vbarray-object-javascript.md)   
 [Dizileri kullanma](../../javascript/advanced/using-arrays-javascript.md)