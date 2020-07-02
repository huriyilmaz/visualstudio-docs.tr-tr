---
title: Sonlandırılmamış açıklama | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814810"
---
# <a name="unterminated-comment"></a>Sonlandırılmayan açıklama
Çok satırlı bir açıklama bloğuna başladınız, ancak bunu düzgün bir şekilde sonlandıramadınız. Çoklu satır açıklamaları bir "/*" bileşimiyle başlar ve ters " \* /" birleşimi ile biter. Aşağıda bir örnek verilmiştir:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- "*/" İle çok satırlı açıklamaları sonlandırıldığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Açıklama Deyimleri](../../javascript/reference/comment-statements-javascript.md)