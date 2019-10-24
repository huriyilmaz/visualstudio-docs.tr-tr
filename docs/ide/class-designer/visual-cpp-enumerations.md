---
title: C++Sınıf Tasarımcısı numaralandırmalar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a514d5eb4b7f79e2fd193c79de670b6dd9c14cb5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747989"
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

@No__t_0 türünü kullanma hakkında daha fazla bilgi için bkz. [numaralandırmalar](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodla çalışma](working-with-visual-cpp-code.md)
- [Sabit Listeleri](/cpp/cpp/enumerations-cpp)