---
title: Sınıf Tasarımcısı C++ numaralandırmalar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: ee56850c05e4b06ea4325ec238e56e99b38978d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114191"
---
# <a name="c-enumerations-in-class-designer"></a>Sınıf Tasarımcısı C++ numaralandırmalar

**Sınıf Tasarımcısı** C++ `enum` ve kapsamlı `enum class` türleri destekler. Aşağıda bir örnek verilmiştir:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Bir sınıf diyagramında C++ sabit listesi şekli bir yapı şekli gibi görünür ve çalışıyor, ancak etiket **enum** veya **enum sınıfını**okuduğu, mavi yerine pembe ve sol ve üst kenar boşluklarında renkli bir kenarlığa sahip. Hem numaralandırma şekilleri hem de yapı şekillerinin kare köşeleri vardır.

Türünü kullanma hakkında daha fazla bilgi için `enum` bkz. [numaralandırmalar](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Ayrıca bkz.

- [C++ kodu ile çalışma](working-with-visual-cpp-code.md)
- [Listelemeler](/cpp/cpp/enumerations-cpp)
