---
title: 'Hata ayıklama F # | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51a8e43268718421a90d051f0d4d9b6afa96980e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156679"
---
# <a name="debugging-f"></a>Hata ayıklama F\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

F # hatası ayıklamak, birkaç özel durum dışında yönetilen herhangi bir dilde hata ayıklamaya benzer:

- **Oto** penceresi, F # değişkenlerini görüntülemez.

- F # için Düzenle ve devam et desteklenmez. Hata ayıklama oturumu sırasında F # kodu düzenlenme olasılığı vardır, ancak bu kaçınılmalıdır. Hata ayıklama oturumu sırasında kod değişiklikleri uygulanmadığı için, hata ayıklama sırasında F # kodu düzenlenmesiyle kaynak kodu ve hata ayıklanan kod arasında uyuşmazlık olur.

- Hata ayıklayıcı F # ifadelerini tanımıyor. F # hata ayıklama sırasında bir hata ayıklayıcı penceresine veya bir iletişim kutusuna ifade girmek için, ifadeyi C# sözdizimine çevirmeniz gerekir. Bir F # ifadesini C# ' a çevirdığınızda, C# ' nin eşitlik için karşılaştırma işleci olarak = = kullandığını ve F # ' ın tek bir = kullandığını unutmayın.

## <a name="see-also"></a>Ayrıca Bkz.

- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
