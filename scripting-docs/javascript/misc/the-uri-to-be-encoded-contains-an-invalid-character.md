---
title: Kodlanacak URI geçersiz karakter içeriyor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 310db785041de0beb0ebbba0cdd9b7c356397bc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862381"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Kodlanacak URI geçersiz karakter içeriyor
Bir dizeyi URI (Tekdüzen Kaynak tanımlayıcısı) olarak kodlamaya çalıştınız, ancak geçersiz karakterler içeriyor. Çoğu karakter, URI 'lere dönüştürülecek dizelerin içinde geçerli olsa da bazı Unicode karakter dizileri geçersizdir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kodlanacak dizenin yalnızca geçerli Unicode dizileri içerdiğinden emin olun. Bütün bir URI, bileşen ve ayırıcıların sırasından oluşur. Açılı ayraçlar içindeki adlar bileşenleri temsil eder ve ":", "/", ";" ve "?", ayırıcı olarak kullanılan ayrılmış karakterlerdir. Genel form:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [encodeURI Işlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent İşlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)