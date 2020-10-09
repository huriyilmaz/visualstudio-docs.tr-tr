---
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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862656"
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