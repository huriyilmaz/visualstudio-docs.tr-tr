---
description: Boolean. prototype. toString veya Boolean. prototype. bir yöntemi Boole dışında bir türün nesnesi üzerinde çağırmaya çalıştınız.
title: Boole bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571447"
---
# <a name="boolean-expected"></a>Boolean bekleniyor
Dışındaki bir türün nesnesi üzerinde **Boolean. prototype. ToString** veya **Boolean. prototype. değeri** metodunu çağırmaya çalıştınız `Boolean` . Bu tür çağrının nesnesinin türünde olması gerekir `Boolean` . Örnek:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yalnızca Boole türündeki nesnelerde **Boolean. prototype. ToString** veya **Boolean. prototype.** bir yöntemi çağırın **.**

## <a name="see-also"></a>Ayrıca bkz.

- [Boole Nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Veri türleri](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Program Akışı Denetimi](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Verileri Kopyalama, Geçirme ve Karşılaştırma](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
