---
title: Dizi uzunluğu sonlu pozitif bir tamsayı olmalıdır | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: c0b827e0cef5cd6c6ea4aeaddc9f32f02004c214
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862214"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Dizi uzunluğu sonlu pozitif bir tamsayı olmalıdır
**Dizi** oluşturucusunu, tam sayı olmayan bir bağımsız değişkenle çağırırsınız (tam sayılar sıfır ve pozitif tamsayılar kümesinden oluşur).  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca yeni bir nesne oluştururken pozitif tamsayılar kullanın `Array` . Tamsayı olmayan tek bir öğe içeren bir dizi oluşturmak istiyorsanız bunu iki adımlı bir işlemde yapın. Önce bir öğesi olan bir dizi oluşturun, ardından değeri ilk öğeye (dizi [0]) yerleştirin. Aşağıda bu hatayı üreten bir örnek verilmiştir.  
  
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
 [Dizileri kullanma](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)