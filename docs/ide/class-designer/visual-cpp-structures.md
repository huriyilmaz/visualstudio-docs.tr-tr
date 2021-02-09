---
title: Sınıf Tasarımcısı 'de C++ yapıları
description: Sınıf Tasarımcısı anahtar sözcük yapısı ile belirtilen C++ yapılarını nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3ca35f9e1c3c1340330ddbbe36ede540fe1e547d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879962"
---
# <a name="c-structures-in-class-designer"></a>Sınıf Tasarımcısı 'de C++ yapıları

**Sınıf Tasarımcısı** , anahtar sözcüğüyle belirtilen C++ yapılarını destekler `struct` . Aşağıda bir örnek verilmiştir:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Türünü kullanma hakkında daha fazla bilgi için `struct` bkz. [struct](/cpp/cpp/struct-cpp).

Bir sınıf diyagramında C++ yapısı şekli, etiketin **Yapı** okuduğu ve yuvarlak köşeler yerine kare köşelere sahip olması dışında bir sınıf şekli gibi görünür ve çalışacaktır.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Yapı|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ kodu ile çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [sýný](/cpp/cpp/struct-cpp)
