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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817677"
---
# <a name="boolean-expected"></a>Boolean bekleniyor
Dışındaki bir türün nesnesi üzerinde **Boolean. prototype. ToString** veya **Boolean. prototype. değeri** metodunu çağırmaya çalıştınız `Boolean` . Bu tür çağrının nesnesinin türünde olması gerekir `Boolean` . Örneğin:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yalnızca Boole türündeki nesnelerde **Boolean. prototype. ToString** veya **Boolean. prototype.** bir yöntemi çağırın **.**

## <a name="see-also"></a>Ayrıca bkz.

- [Boole Nesnesi](../../javascript/reference/boolean-object-javascript.md)
- [Veri türleri](../../javascript/data-types-javascript.md)
- [Program Akışı Denetimi](../../javascript/controlling-program-flow-javascript.md)
- [Verileri Kopyalama, Geçirme ve Karşılaştırma](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)