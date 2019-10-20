---
title: Sınıf Tasarımcısında Visual C++ Numaralandırmaları
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
ms.openlocfilehash: b5df17176839dccf0fbe0c42f164bde6b3e39f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631131"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Sınıf Tasarımcısı C++ görsel numaralandırmalar

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

- [Visual C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sabit Listeleri](/cpp/cpp/enumerations-cpp)