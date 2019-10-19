---
title: "' This ' öğesine atanamaz | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 73baa77cc63e3a43ac30e70f66081bbc7ade3020
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572356"
---
# <a name="cannot-assign-to-this"></a>'this' nesnesine atanamaz
**Bu**değere bir değer atamaya çalıştınız. **Bu** , aşağıdakilerden birini ifade eden bir [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] anahtar kelimedir:

- Şu anda bir yöntemi yürüten nesne,

- geçerli bir yöntem yoksa (veya yöntem başka bir nesneye ait değilse) genel nesne.

Bir yöntem, bir nesne aracılığıyla çağrılan [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] işlevdir. Bir yöntem içinde, **this** anahtar sözcüğü, yöntemin çağrıldığı nesnesine bir başvurudur ( **Yeni** işleçle sınıf oluşturucusu çağrılarak oluşturulan nesne olur).

Bir yöntemi içinde, **bunu** geçerli nesneye başvurmak için kullanabilirsiniz, ancak **buna**yeni bir değer atayamazsınız.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Bu**öğesine atamayı denemeyin. Örneklenmiş bir nesnenin bir özelliğine veya yöntemine erişmek için, nokta işlecini (örn. **Circle. Radius**) kullanın.

  > [!NOTE]
  > Kullanıcı tarafından oluşturulan **bir değişkene ad**belirtemezsiniz; [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ayrılmış bir sözcüktür.

## <a name="see-also"></a>Ayrıca bkz.

- [this Deyimi](../../javascript/reference/this-statement-javascript.md)
- [Komut Dosyalarınızda Sorun Giderme](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)