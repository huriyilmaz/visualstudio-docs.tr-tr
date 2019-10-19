---
title: VBArray bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572510"
---
# <a name="vbarray-expected"></a>VBArray bekleniyor
Bir Visual Basic safeArray olmayan bir nesne (biri beklenirken) sağladınız.  
  
```js
new VBArray(safeArray);  
```  
  
 Vbarışınlar salt okunurdur ve doğrudan oluşturulamaz. SafeArray bağımsız değişkeni bir VBArray değeridir ve `VBArray` oluşturucusuna geçirilmeden önce bir VBArray değeri almış olmalıdır. Bu, yalnızca varolan bir ActiveX veya başka bir nesneden değeri alarak yapılabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **VBArray** yapıcısına yalnızca **VBArray** nesneleri geçirdiğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VBArray nesnesi](../../javascript/reference/vbarray-object-javascript.md)    
 [Dizileri Kullanma](../../javascript/advanced/using-arrays-javascript.md)