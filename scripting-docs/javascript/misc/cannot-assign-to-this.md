---
description: Bu değere bir değer atamaya çalıştınız.
title: "' This ' öğesine atanamaz | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c52118ee78b7ecb7efa94dd6d86cc4fb34c7d1f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571837"
---
# <a name="cannot-assign-to-this"></a>'this' nesnesine atanamaz
**Bu** değere bir değer atamaya çalıştınız. **Bu** , [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aşağıdakilerden birini ifade eden bir anahtar sözcüktür:

- Şu anda bir yöntemi yürüten nesne,

- geçerli bir yöntem yoksa (veya yöntem başka bir nesneye ait değilse) genel nesne.

Yöntemi, bir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesnesi aracılığıyla çağrılan bir işlevdir. Bir yöntem içinde, **this** anahtar sözcüğü, yöntemin çağrıldığı nesnesine bir başvurudur ( **Yeni** işleçle sınıf oluşturucusu çağrılarak oluşturulan nesne olur).

Bir yöntemi içinde, **bunu** geçerli nesneye başvurmak için kullanabilirsiniz, ancak **buna** yeni bir değer atayamazsınız.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Bu** öğesine atamayı denemeyin. Örneklenmiş bir nesnenin bir özelliğine veya yöntemine erişmek için, nokta işlecini (örn. **Circle. Radius**) kullanın.

  > [!NOTE]
  > Kullanıcı tarafından oluşturulan **bir değişkene ad** belirtemezsiniz; Bu, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ayrılmış bir sözcüktür.

## <a name="see-also"></a>Ayrıca bkz.

- [this Deyimi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/this)
- [Komut Dosyalarınızda Sorun Giderme](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
