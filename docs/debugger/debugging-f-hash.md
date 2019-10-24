---
title: Hata F# ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7bc3934136f0966439bec2e4368488e52099602
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738262"
---
# <a name="debugging-f"></a>F \# hatalarını ayıklama
Hata F# ayıklama, birkaç özel durum dışında yönetilen herhangi bir dilde hata ayıklamaya benzer:

- **Oto** penceresinde değişkenler görüntülenmez F# .

- İçin F#Düzenle ve devam et desteklenmez. Hata F# ayıklama oturumu sırasında kodun düzenlenme olasılığı vardır, ancak bu kaçınılmalıdır. Hata ayıklama oturumu sırasında kod değişiklikleri uygulanmadığından, hata ayıklama sırasında F# kodun düzenlenebilmesi, kaynak kodu ve hata ayıklanan kod arasında uyuşmazlık oluşmasına neden olur.

- Hata ayıklayıcı ifadeleri tanımıyor F# . Hata ayıklayıcı penceresinde veya hata ayıklama sırasında F# bir iletişim kutusunda ifade girmek için, ifadeyi C# sözdizimine çevirmeniz gerekir. Bir F# ifadeyi içine C#çevirdığınızda, eşitlik için karşılaştırma işleci olarak = C# = kullandığını ve tek bir = F# kullandığını unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
