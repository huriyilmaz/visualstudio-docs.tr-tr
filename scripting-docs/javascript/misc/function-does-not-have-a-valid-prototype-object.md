---
title: İşlevin geçerli bir prototip nesnesi yok | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574597"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>İşlevin geçerli bir prototip nesnesi yok
Bir nesnenin belirli bir işlev sınıfından türetilmişse, ancak nesnenin `prototype` özelliğini `null` ya da bir dış nesne türü (her ikisi de geçerli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesneleri) olarak yeniden tanımladıysanız, **instanceof** öğesini kullanmaya çalıştınız. Dış nesne, ana bilgisayar nesne modelinden (örneğin, Internet Explorer 'ın belgesi veya pencere nesnesi) veya harici bir COM nesnesinden bir nesne olabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İşlevin `prototype` özelliğinin geçerli bir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesnesine başvurduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Işlev nesnesi](../../javascript/reference/function-object-javascript.md)    
 [prototype Özelliği (Nesne)](../../javascript/reference/prototype-property-object-javascript.md)