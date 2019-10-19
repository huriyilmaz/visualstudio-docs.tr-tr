---
title: Nesne bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 1611596d844d43ef72663154dc48791830dfe29f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573730"
---
# <a name="object-expected"></a>Nesne bekleniyor
@No__t_0 dışında bir türün nesnesi üzerinde bir yöntemi veya özelliği çağırmaya çalıştınız ya da bir `Object` gerektiğinde `Object` dışında bir türün bağımsız değişkenini geçirtiniz.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca `Object` türündeki nesnelerde yöntemi veya özelliği çağırın.  
  
- Nesne olmayan bir bağımsız değişken için hata oluşursa, `Object` türünde bir nesne geçirin.  
  
- @No__t_0 türünde bir nesne yerine tanımsız veya null başvurusunun döndürülüp çağrılmadığını denetleyin.  
  
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