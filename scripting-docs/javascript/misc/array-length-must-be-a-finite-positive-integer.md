---
title: Dizi uzunluğu sonlu pozitif bir tamsayı olmalıdır | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69494f1485a97ff4f2c98cf2493e5d0bc5b8aa9f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576086"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Dizi uzunluğu sonlu pozitif bir tamsayı olmalıdır
**Dizi** oluşturucusunu, tam sayı olmayan bir bağımsız değişkenle çağırırsınız (tam sayılar sıfır ve pozitif tamsayılar kümesinden oluşur).  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca yeni bir `Array` nesnesi oluşturulurken pozitif tamsayılar kullanın. Tamsayı olmayan tek bir öğe içeren bir dizi oluşturmak istiyorsanız bunu iki adımlı bir işlemde yapın. Önce bir öğesi olan bir dizi oluşturun, ardından değeri ilk öğeye (dizi [0]) yerleştirin. Aşağıda bu hatayı üreten bir örnek verilmiştir.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Aşağıdaki örnek, tek bir sayısal öğe içeren bir diziyi belirtmenin doğru yolunu göstermektedir.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     En büyük tamsayı değeri (yaklaşık 4.000.000.000) dışında bir dizinin boyutu için üst sınır yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dizileri Kullanma](../../javascript/advanced/using-arrays-javascript.md)