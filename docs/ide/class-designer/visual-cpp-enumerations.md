---
title: Sınıf Tasarımcısı C++ numaralandırmalar
description: Sınıf Tasarımcısı C++ enum ve kapsamlı numaralandırma sınıfı türlerini nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b12d270884ca9877d6c1c80780a9ae96324f3af4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903461"
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

Bir sınıf diyagramında C++ sabit listesi şekli bir yapı şekli gibi görünür ve çalışıyor, ancak etiket **enum** veya **enum sınıfını** okuduğu, mavi yerine pembe ve sol ve üst kenar boşluklarında renkli bir kenarlığa sahip. Hem numaralandırma şekilleri hem de yapı şekillerinin kare köşeleri vardır.

Türünü kullanma hakkında daha fazla bilgi için `enum` bkz. [numaralandırmalar](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Ayrıca bkz.

- [C++ kodu ile çalışma](working-with-visual-cpp-code.md)
- [Listelemeler](/cpp/cpp/enumerations-cpp)
