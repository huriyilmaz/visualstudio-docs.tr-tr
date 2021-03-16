---
description: Yanlış bir Unicode kaçış sırası oluşturdunuz.
title: Onaltılık basamak bekleniyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 107ce2dd4f9a65a0a04b8e2ec773367ffae4ce81
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570433"
---
# <a name="expected-hexadecimal-digit"></a>Beklenen onaltılık basamak
Yanlış bir Unicode kaçış sırası oluşturdunuz. Unicode kaçış dizileri, tam olarak dört onaltılık basamakla (daha fazla ve daha az olmadan), \u ile başlar. Unicode onaltılık basamaklar yalnızca 0-9 rakamları, büyük harf A-F ve küçük harf a-f karakterleri içerebilir. Aşağıdaki örnekte, doğru biçimlendirilmiş bir Unicode kaçış sırası gösterilmektedir.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Unicode onaltılık rakamların \u ile başlayıp, yalnızca 0-9 sayılarını, büyük harf A-F harflerini, küçük harf a-f; ve dört basamakla gruplandırılır.  
  
    > [!NOTE]
    > Bir dizede, \u değişmez metnini kullanmak istiyorsanız, \\ ilk ters eğik çizgiden kaçınmak için iki ters eğik çizgi (\u) kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Veri türleri](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
