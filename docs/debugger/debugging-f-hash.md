---
title: 'Hata ayıklama F # | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738262"
---
# <a name="debugging-f"></a>Hata ayıklama F\#
F # hatası ayıklamak, birkaç özel durum dışında yönetilen herhangi bir dilde hata ayıklamaya benzer:

- **Oto** penceresi, F # değişkenlerini görüntülemez.

- F # için Düzenle ve devam et desteklenmez. Hata ayıklama oturumu sırasında F # kodu düzenlenme olasılığı vardır, ancak bu kaçınılmalıdır. Hata ayıklama oturumu sırasında kod değişiklikleri uygulanmadığı için, hata ayıklama sırasında F # kodu düzenlenmesiyle kaynak kodu ve hata ayıklanan kod arasında uyuşmazlık olur.

- Hata ayıklayıcı F # ifadelerini tanımıyor. F # hata ayıklama sırasında bir hata ayıklayıcı penceresine veya bir iletişim kutusuna ifade girmek için, ifadeyi C# sözdizimine çevirmeniz gerekir. Bir F # ifadesini C# ' a çevirdığınızda, C# ' nin eşitlik için karşılaştırma işleci olarak = = kullandığını ve F # ' ın tek bir = kullandığını unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
