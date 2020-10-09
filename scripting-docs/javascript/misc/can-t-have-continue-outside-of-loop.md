---
title: Döngü dışında ' Continue ' olamaz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14745c5789fe6c0350f83e46ee0e918f92789d96
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861978"
---
# <a name="cant-have-continue-outside-of-loop"></a>Döngü dışında 'continue' olamaz
**Continue** ifadesini bir döngünün dışında kullanmaya çalıştınız. **Continue** deyimleri yalnızca a gövdesi içinde kullanılabilir:  
  
- `do-while` gerçekleştirmek  
  
- `while` gerçekleştirmek  
  
- **for** döngüsü,  
  
- **for/in** döngüsü.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- **Continue** ifadesinin gövdesi içinde göründüğünden emin olun:  
  
  - `do-while` gerçekleştirmek  

  - `while` gerçekleştirmek  

  - **for** döngüsü,  

  - **for/in** döngüsü.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Continue bildirisi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/continue)   
 [Program akışını denetleme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Komut Dosyalarınızda Sorun Giderme](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)