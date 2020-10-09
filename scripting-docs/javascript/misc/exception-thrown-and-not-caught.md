---
title: Özel durum oluştu ve yakalanmadı | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862758"
---
# <a name="exception-thrown-and-not-caught"></a>Oluşan özel durum yakalanmadı
Kodunuza bir ifade eklemiş olursunuz `throw` , ancak bir **TRY** bloğu içine dahil değildir veya hatayı yakalamak için ilişkili bir **catch** bloğu yoktu. Özel durumlar **throw** ifadesiyle **TRY** bloğunun içinden oluşturulur ve **catch** ifadesiyle **TRY** bloğunun dışında yakalanır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bir **TRY** bloğunda özel durum oluşturabilecek kodu tırnak içine alın ve buna karşılık gelen bir **catch** bloğu olduğundan emin olun.  
  
- Catch deyiminizde özel durum biçiminin doğru olduğundan emin olun.  
  
- Özel durum yeniden oluşturulursa, başka bir karşılık gelen catch ifadesinin bulunduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [deneyin... yakala... finally ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)