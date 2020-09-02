---
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
ms.openlocfilehash: f5c52153da64ff477d89b09d4af17169da18e4e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817326"
---
# <a name="cannot-assign-to-this"></a>'this' nesnesine atanamaz
**Bu**değere bir değer atamaya çalıştınız. **Bu** , [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aşağıdakilerden birini ifade eden bir anahtar sözcüktür:

- Şu anda bir yöntemi yürüten nesne,

- geçerli bir yöntem yoksa (veya yöntem başka bir nesneye ait değilse) genel nesne.

Yöntemi, bir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nesnesi aracılığıyla çağrılan bir işlevdir. Bir yöntem içinde, **this** anahtar sözcüğü, yöntemin çağrıldığı nesnesine bir başvurudur ( **Yeni** işleçle sınıf oluşturucusu çağrılarak oluşturulan nesne olur).

Bir yöntemi içinde, **bunu** geçerli nesneye başvurmak için kullanabilirsiniz, ancak **buna**yeni bir değer atayamazsınız.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Bu**öğesine atamayı denemeyin. Örneklenmiş bir nesnenin bir özelliğine veya yöntemine erişmek için, nokta işlecini (örn. **Circle. Radius**) kullanın.

  > [!NOTE]
  > Kullanıcı tarafından oluşturulan **bir değişkene ad**belirtemezsiniz; Bu, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ayrılmış bir sözcüktür.

## <a name="see-also"></a>Ayrıca bkz.

- [this Deyimi](../../javascript/reference/this-statement-javascript.md)
- [Komut Dosyalarınızda Sorun Giderme](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)