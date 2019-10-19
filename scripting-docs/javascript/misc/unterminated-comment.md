---
title: Sonlandırılmamış açıklama | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 22bda5d6baabe8874d7514c137ddbcb3e11eb23b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572514"
---
# <a name="unterminated-comment"></a>Sonlandırılmayan açıklama
Çok satırlı bir açıklama bloğuna başladınız, ancak bunu düzgün bir şekilde sonlandıramadınız. Çoklu satır açıklamaları bir "/*" bileşimiyle başlar ve ters "\*/" birleşimi ile biter. Aşağıda bir örnek verilmiştir:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- "*/" İle çok satırlı açıklamaları sonlandırıldığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Açıklama Deyimleri](../../javascript/reference/comment-statements-javascript.md)