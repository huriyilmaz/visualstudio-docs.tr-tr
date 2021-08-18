---
title: Sınıf Tasarımcısı'de C++ Sınıf Tasarımcısı
description: C++ enum Sınıf Tasarımcısı kapsamlı enum sınıf türlerini nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: b4ab0dc47f9113e17b36617b432df1ffe5f0153e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109506"
---
# <a name="c-enumerations-in-class-designer"></a>Sınıf Tasarımcısı'de C++ numara Sınıf Tasarımcısı

**Sınıf Tasarımcısı** C++ ve `enum` kapsamlı türleri `enum class` destekler. Aşağıda bir örnek verilmiştir:

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

Sınıf diyagramında C++ numaralama şekli, yapı şekli gibi görünür ve çalışır; tek fark etiketin **Enum** veya **Enum** sınıfını okuması, mavi yerine pembe olması ve sol ve üst kenar boşluklarında renkli bir kenarlık olmasıdır. Hem numaralama şekilleri hem de yapı şekilleri köşe köşelerine sahiptir.

türünü kullanma hakkında daha fazla `enum` bilgi için [bkz. Numaralar.](/cpp/cpp/enumerations-cpp)

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Listelemeler](/cpp/cpp/enumerations-cpp)
