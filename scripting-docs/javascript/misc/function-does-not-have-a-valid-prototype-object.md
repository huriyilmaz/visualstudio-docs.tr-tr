---
description: Bir nesnenin belirli bir işlev sınıfından türetilmişse, ancak nesnenin prototip özelliğini null ya da bir dış nesne türü (her ikisi de geçerli JavaScript nesneleri) olarak yeniden tanımladıysanız, instanceof öğesini kullanmaya çalıştınız.
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
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571421"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>İşlevin geçerli bir prototip nesnesi yok
Bir nesnenin belirli bir  işlev sınıfından türetilmişse, ancak nesnenin `prototype` özelliğini ya da `null` bir dış nesne türü (her ikisi de geçerli nesneler) olarak yeniden tanımladıysanız, instanceof öğesini kullanmaya çalıştınız [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] . Dış nesne, ana bilgisayar nesne modelinden (örneğin, Internet Explorer 'ın belgesi veya pencere nesnesi) veya harici bir COM nesnesinden bir nesne olabilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İşlevin `prototype` özelliğinin geçerli bir nesneye başvurduğundan emin olun [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [İşlev nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype Özelliği (Nesne)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
