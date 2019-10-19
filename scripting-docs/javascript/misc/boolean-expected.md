---
title: Boole bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576052"
---
# <a name="boolean-expected"></a>Boolean bekleniyor
@No__t_2 dışında bir türün nesnesinde **Boolean. prototype. ToString** veya **Boolean. prototype. değeri** metodunu çağırmaya çalıştınız. Bu tür çağrının nesnesinin `Boolean` türünde olması gerekir. Örneğin:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yalnızca Boole türündeki nesnelerde **Boolean. prototype. ToString** veya **Boolean. prototype.** bir yöntemi çağırın **.**

## <a name="see-also"></a>Ayrıca bkz.

- [Boole Nesnesi](../../javascript/reference/boolean-object-javascript.md)
- [Veri Türleri](../../javascript/data-types-javascript.md)
- [Program Akışı Denetimi](../../javascript/controlling-program-flow-javascript.md)
- [Verileri Kopyalama, Geçirme ve Karşılaştırma](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)