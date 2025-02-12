---
title: 'Hata ayıklama F # | Microsoft Docs'
description: 'Visual Studio, diğer yönetilen dillerin hatalarını ayıklama ile karşılaştırıldığında, F # hatası ayıklama arasındaki farkların listesini gözden geçirin.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 48bbd10fa01d048e19d80095658045a2e64e411c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636742"
---
# <a name="debugging-f"></a>Hata ayıklama F\#
F # hatası ayıklamak, birkaç özel durum dışında yönetilen herhangi bir dilde hata ayıklamaya benzer:

- **Oto** penceresi, F # değişkenlerini görüntülemez.

- F # için Düzenle ve devam et desteklenmez. Hata ayıklama oturumu sırasında F # kodu düzenlenme olasılığı vardır, ancak bu kaçınılmalıdır. Hata ayıklama oturumu sırasında kod değişiklikleri uygulanmadığı için, hata ayıklama sırasında F # kodu düzenlenmesiyle kaynak kodu ve hata ayıklanan kod arasında uyuşmazlık olur.

- Hata ayıklayıcı F # ifadelerini tanımıyor. F # hata ayıklama sırasında bir hata ayıklayıcı penceresine veya bir iletişim kutusuna ifade girmek için, ifadeyi C# sözdizimine çevirmeniz gerekir. Bir F # ifadesini C# ' a çevirdığınızda, C# ' nin eşitlik için karşılaştırma işleci olarak = = kullandığını ve F # ' ın tek bir = kullandığını unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
