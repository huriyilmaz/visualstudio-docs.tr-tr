---
title: Bellek Belleğinde Sayfa Yukarı veya Aşağı | Microsoft Docs
description: Bellek penceresinde bellek içeriğini görüntülemek için bellekte sayfa yukarı veya aşağı sayfalama veya bellekte hata ayıklama sırasında Farklı Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7838f6088764939a4a93c0c723c5e06e5c9ed8f51c2d5bedc1c522b00e7238fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379106"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Nasıl Yapılır: Bellekte Sayfa Yukarı veya Aşağı Gitme

Bellek penceresinde veya Ayır  penceresinde bellek  içeriklerini görüntüleye, bellek alanı içinde yukarı veya aşağı taşımak için dikey kaydırma çubuğunu kullanabilirsiniz.

### <a name="to-page-up-or-down-in-memory"></a>Bellekte sayfa yukarı veya aşağı sayfa

1. Sayfayı aşağı kaydırmak için (daha yüksek bir bellek adresine gidin), kaydırma kutusunun altındaki dikey kaydırma çubuğuna tıklayın.

2. Sayfa yukarı (daha düşük bir bellek adresine taşıma) için, başparmak üzerindeki dikey kaydırma çubuğuna tıklayın.

   Ayrıca dikey kaydırma çubuğunun standart olmayan bir şekilde çalışma olduğunu da fark edersiniz. Modern bir bilgisayarın adres alanı çok büyüktür ve kaydırma çubuğu başparmaklarını alıp rastgele bir konuma sürükleyerek kolayca kaybolabilirsiniz. Bu nedenle başparmak "springloaded" olur ve her zaman kaydırma çubuğunun merkezinde kalır. Yerel kod uygulamalarında sayfa yukarı veya aşağı kaydırabilirsiniz, ancak serbestçe kaydıramazsiniz.

   Yönetilen uygulamalarda, disassembly tek bir işlevle sınırlıdır ve normal şekilde kaydırabilirsiniz.

   Pencerenin alt kısmında daha yüksek adreslerin görüntü olduğunu fark vardır. Daha yüksek bir adresi görüntülemek için yukarı değil aşağı taşımalısiniz.

#### <a name="to-move-up-or-down-one-instruction"></a>Bir yönergeyi yukarı veya aşağı taşımak için

- Dikey kaydırma çubuğunun üst veya alt kısmında bulunan oka tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Bellek Pencereleri](../debugger/memory-windows.md)
- [Nasıl Yapılır: Ayrıştırılmış Kod Penceresini Kullanma](../debugger/how-to-use-the-disassembly-window.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)