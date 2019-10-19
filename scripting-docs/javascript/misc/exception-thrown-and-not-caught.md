---
title: Özel durum oluştu ve yakalanmadı | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572860"
---
# <a name="exception-thrown-and-not-caught"></a>Oluşan özel durum yakalanmadı
Kodunuzda bir `throw` ifadesini eklemiş olursunuz, ancak bir **TRY** bloğu içine alınmıştı veya hatayı yakalamak için ilişkili bir **catch** bloğu yoktu. Özel durumlar **throw** ifadesiyle **TRY** bloğunun içinden oluşturulur ve **catch** ifadesiyle **TRY** bloğunun dışında yakalanır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bir **TRY** bloğunda özel durum oluşturabilecek kodu tırnak içine alın ve buna karşılık gelen bir **catch** bloğu olduğundan emin olun.  
  
- Catch deyiminizde özel durum biçiminin doğru olduğundan emin olun.  
  
- Özel durum yeniden oluşturulursa, başka bir karşılık gelen catch ifadesinin bulunduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)    
 [throw deyimleri](../../javascript/reference/throw-statement-javascript.md)    
 [try...catch...finally Deyimi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)