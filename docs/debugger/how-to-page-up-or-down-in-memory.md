---
title: Bellekte nasıl çalışır veya küçültüme? | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79216ba29047101c9b9d2c6618cae013640542b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349425"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Nasıl Yapılır: Bellekte Sayfa Yukarı veya Aşağı Gitme

Bellek içeriğini bir **bellek** penceresinde veya **ayrıştırma** penceresinde görüntülediğinizde, bellek alanında yukarı veya aşağı taşımak için dikey kaydırma çubuğunu kullanabilirsiniz.

### <a name="to-page-up-or-down-in-memory"></a>Bellekte sayfa yukarı veya aşağı

1. Sayfa aşağı (daha yüksek bir bellek adresine taşı) için, kaydırma kutusunun altındaki dikey kaydırma çubuğuna tıklayın.

2. Sayfa yukarı (daha düşük bir bellek adresine taşı) için, kaydırma kutusunun üstündeki dikey kaydırma çubuğuna tıklayın.

   Dikey ScrollBar 'ın standart dışı bir şekilde çalıştığını da fark edeceksiniz. Modern bir bilgisayarın adres alanı çok büyük olduğundan, kaydırma çubuğu Thumb 'ı yakalayıp ve rastgele bir konuma sürükleyerek kaybedilmesi kolay hale gelir. Bu nedenle, kaydırma "springloaded" olur ve her zaman kaydırma çubuğunun merkezinde kalır. Yerel kod uygulamalarında, sayfa yukarı veya aşağı taşıyabilirsiniz, ancak serbestçe ilerlenemez.

   Yönetilen uygulamalarda, ayrıştırılmış derleme bir işlevle sınırlıdır ve normal şekilde kaydırma yapabilirsiniz.

   Pencerenin alt kısmında daha yüksek adreslerin göründüğünü fark edeceksiniz. Daha yüksek bir adresi görüntülemek için, aşağı taşımanız gerekir.

#### <a name="to-move-up-or-down-one-instruction"></a>Bir yönergeyi yukarı veya aşağı taşımak için

- Dikey kaydırma çubuğunun üst veya alt kısmındaki oka tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Bellek Pencereleri](../debugger/memory-windows.md)
- [Nasıl Yapılır: Ayrıştırılmış Kod Penceresini Kullanma](../debugger/how-to-use-the-disassembly-window.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)