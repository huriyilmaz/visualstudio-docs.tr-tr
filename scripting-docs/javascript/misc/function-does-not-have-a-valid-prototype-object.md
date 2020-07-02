---
title: İşlevin geçerli bir prototip nesnesi yok | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817365"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>İşlevin geçerli bir prototip nesnesi yok
Bir nesnenin belirli bir **instanceof** işlev sınıfından türetilmişse, ancak nesnenin `prototype` özelliğini ya da `null` bir dış nesne türü (her ikisi de geçerli nesneler) olarak yeniden tanımladıysanız, instanceof öğesini kullanmaya çalıştınız [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Dış nesne, ana bilgisayar nesne modelinden (örneğin, Internet Explorer 'ın belgesi veya pencere nesnesi) veya harici bir COM nesnesinden bir nesne olabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İşlevin `prototype` özelliğinin geçerli bir nesneye başvurduğundan emin olun [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İşlev nesnesi](../../javascript/reference/function-object-javascript.md)   
 [prototype Özelliği (Nesne)](../../javascript/reference/prototype-property-object-javascript.md)