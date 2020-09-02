---
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
ms.openlocfilehash: 28eec125914f0207fbdf79a39ea2140dd74d6d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816234"
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
 [Nesne nesnesi](../../javascript/reference/object-object-javascript.md)   
 [Nesneler ve Diziler](../../javascript/objects-and-arrays-javascript.md)