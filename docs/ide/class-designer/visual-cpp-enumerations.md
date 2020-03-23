---
title: Sınıf Tasarımcıc++ Eumerations
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114191"
---
# <a name="c-enumerations-in-class-designer"></a>Sınıf Tasarımcısı'nda C++ eumerasyonları

**Sınıf Tasarımcısı** C++ `enum` ve `enum class` kapsamlı türleri destekler. Aşağıda bir örnek verilmiştir:

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

Sınıf diyagramındaki C++ numaralandırma şekli, etiketin **Enum** veya **Enum sınıfını**okuması dışında bir yapı şekli gibi görünür ve çalışır, mavi yerine pembedir ve sol ve üst kenar boşluklarında renkli bir kenarlık vardır. Hem numaralandırma şekilleri hem de yapı şekilleri kare köşelidir.

`enum` Türü kullanma hakkında daha fazla bilgi [için, Bkz.](/cpp/cpp/enumerations-cpp)

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Numaralandırma](/cpp/cpp/enumerations-cpp)
