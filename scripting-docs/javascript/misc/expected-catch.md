---
description: Özel durum işleme try bloğunu kullandınız, ancak ilişkili catch ifadesini yazmadınız.
title: "' Catch ' bekleniyor | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5cf6087ff5a299c575ac4f2cd5eb8a3e206b7e0
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571044"
---
# <a name="expected-catch"></a>'catch' bekleniyor.
Özel durum işleme **TRY** bloğunu kullandınız, ancak ilişkili **catch** ifadesini yazmadınız. Özel durum işleme mekanizması, başarısız olabilecek kodun yanı ve bir özel durum oluşursa, bir **TRY** bloğunun içine sarmalanması gereken kodu gerektirir. Özel durumlar **throw** deyimi kullanılarak **TRY** bloğunun içinden oluşturulur ve bir veya daha fazla **catch** deyimi ile **TRY** bloğunun dışında yakalanır.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- İlişkili **catch** bloğunu ekleyin.  
  
- **Catch** bloğu yerine **finally** bloğu kullanmayı deneyin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [deneyin... yakala... finally ekstresi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Hata Nesnesi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)
