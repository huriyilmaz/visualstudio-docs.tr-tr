---
title: Dizi uzunluğuna sonlu pozitif bir sayı atanmalıdır | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: cff9c8c42199e106cca5f6f2808866e46a26afe2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576074"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Dizi uzunluğuna sonsuz olmayan pozitif bir sayı atanmalıdır
Var olan bir **dizi** nesnesinin **length** özelliğini ayarlarken, pozitif sayı veya sıfır olmayan bir dizi uzunluğu belirttiniz. Negatif olan veya sayı olmayan bir `Array` nesnesinin **length** özelliğine bir değer atadığınızda bu hata oluşur (`NaN`). @No__t_0 kesir sayılarını otomatik olarak tam tamsayılara dönüştürdüğüne unutmayın.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Length özelliğine pozitif bir tam sayı atayın. En büyük tamsayı değeri (yaklaşık 4.000.000.000) dışında bir dizinin boyutu için üst sınır yoktur. Aşağıdaki örnek, bir **dizi** nesnesinin **length** özelliğini ayarlamak için doğru yolu gösterir.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dizileri Kullanma](../../javascript/advanced/using-arrays-javascript.md)