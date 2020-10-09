---
title: Kodu çözülecek URI geçerli bir kodlama değil | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ea642cece501804b6ee2efaac778c3b8d520fc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861868"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Kodu çözülecek URI geçerli bir kodlamada değil
Yanlış biçimlendirilmiş bir URI 'yi (Tekdüzen Kaynak tanımlayıcısı) çözmeye çalıştınız. URI 'Ler özel bir sözdizimine sahiptir; bir URI 'de kullanılmadan önce, alfasayısal olmayan çoğu karakter kodlanmalıdır. `encodeURI` `encodeURIComponent` Normal bir DIZEDEN bir URI oluşturmak için ve yöntemlerini kullanabilirsiniz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
 Bütün bir URI, bileşen ve ayırıcıların sırasından oluşur. Genel form:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Açılı ayraçlar içindeki adlar bileşenleri temsil eder ve ":", "/", ";" ve "?", ayırıcı olarak kullanılan ayrılmış karakterlerdir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yalnızca geçerli URI 'Leri çözmeye çalışırken emin olun. Normal dizelerin kodunu çözemezsiniz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , çünkü bunlar geçersiz karakterler içeriyor olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [decodeURI Işlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent İşlevi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)