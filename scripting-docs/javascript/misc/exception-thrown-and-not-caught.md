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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814596"
---
# <a name="exception-thrown-and-not-caught"></a>Oluşan özel durum yakalanmadı
Kodunuza bir ifade eklemiş olursunuz `throw` , ancak bir **TRY** bloğu içine dahil değildir veya hatayı yakalamak için ilişkili bir **catch** bloğu yoktu. Özel durumlar **throw** ifadesiyle **TRY** bloğunun içinden oluşturulur ve **catch** ifadesiyle **TRY** bloğunun dışında yakalanır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Bir **TRY** bloğunda özel durum oluşturabilecek kodu tırnak içine alın ve buna karşılık gelen bir **catch** bloğu olduğundan emin olun.  
  
- Catch deyiminizde özel durum biçiminin doğru olduğundan emin olun.  
  
- Özel durum yeniden oluşturulursa, başka bir karşılık gelen catch ifadesinin bulunduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata nesnesi](../../javascript/reference/error-object-javascript.md)   
 [throw ekstresi](../../javascript/reference/throw-statement-javascript.md)   
 [deneyin... yakala... finally ekstresi](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)