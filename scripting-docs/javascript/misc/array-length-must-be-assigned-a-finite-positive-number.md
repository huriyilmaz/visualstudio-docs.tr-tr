---
title: Dizi uzunluğuna sonlu pozitif bir sayı atanmalıdır | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e0016c7a0a6acb3f08121d8636ccdf848dcf201
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862807"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Dizi uzunluğuna sonsuz olmayan pozitif bir sayı atanmalıdır
Var olan bir **dizi** nesnesinin **length** özelliğini ayarlarken, pozitif sayı veya sıfır olmayan bir dizi uzunluğu belirttiniz. Bu hata **length** `Array` , negatif olan veya sayı olmayan () bir nesnenin Length özelliğine bir değer atadığınızda oluşur `NaN` . [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Kesir sayılarını otomatik olarak tam tamsayılara dönüştürdüğüne unutmayın.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Length özelliğine pozitif bir tam sayı atayın. En büyük tamsayı değeri (yaklaşık 4.000.000.000) dışında bir dizinin boyutu için üst sınır yoktur. Aşağıdaki örnek, bir **dizi** nesnesinin **length** özelliğini ayarlamak için doğru yolu gösterir.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dizileri kullanma](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)