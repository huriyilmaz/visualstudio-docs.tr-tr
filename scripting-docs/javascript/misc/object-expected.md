---
description: Nesne dışında bir türün nesnesi üzerinde bir yöntemi veya özelliği çağırmaya çalıştınız ya da bir nesne gerektiğinde nesne dışında bir türün bağımsız değişkenini geçirtiniz.
title: Nesne bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a62a68b8dd5289794086dad6858238db6cc4f449
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572071"
---
# <a name="object-expected"></a>Nesne bekleniyor
Öğesinden farklı bir türün bir nesnesi üzerinde bir yöntem veya özellik çağırmaya çalıştınız `Object` veya bir tür bağımsız değişkenini, `Object` gerekli olduğu zaman dışında başka bir türde geçirtiniz `Object` .  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca türündeki nesnelerde metodu veya özelliği çağırın `Object` .  
  
- Nesne olmayan bir bağımsız değişken için hata oluşursa, türünde bir nesne geçirin `Object` .  
  
- Türünde bir nesne yerine tanımsız veya null başvurusunun döndürülüp çağrılmadığını denetleyin `Object` .  
  
     Örneğin, aşağıdaki kodda myVar öğesinde bu hatayı alırsanız:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Bunun yerine, bu kodu kullanabilirsiniz:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nesne nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Nesneler ve Diziler](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
