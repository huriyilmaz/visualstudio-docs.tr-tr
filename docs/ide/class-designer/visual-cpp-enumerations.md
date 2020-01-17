---
title: C++Sınıf Tasarımcısı numaralandırmalar
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114191"
---
# <a name="c-enumerations-in-class-designer"></a>C++Sınıf Tasarımcısı numaralandırmalar

**Sınıf Tasarımcısı** `enum` C++ ve kapsamlı `enum class` türlerini destekler. Aşağıda bir örnek verilmiştir:

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

Bir C++ sınıf diyagramındaki sabit listesi şekli bir yapı şekli gibi görünür ve bu şekilde çalışıyor, etiket **enum** veya **enum sınıfını**okuduğu, mavi yerine pembe ve sol ve üst kenar boşluklarında renkli bir kenarlığa sahip olur. Hem numaralandırma şekilleri hem de yapı şekillerinin kare köşeleri vardır.

`enum` türünü kullanma hakkında daha fazla bilgi için bkz. [numaralandırmalar](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodla çalışma](working-with-visual-cpp-code.md)
- [Sabit Listeleri](/cpp/cpp/enumerations-cpp)
