---
title: C++Sınıf Tasarımcısı yapılar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 65fb4738b3124daf48b501c6db416d3803da32ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748912"
---
# <a name="c-structures-in-class-designer"></a>C++Sınıf Tasarımcısı yapılar

**Sınıf Tasarımcısı** , C++ anahtar sözcüğü `struct` ile belirtilen yapıları destekler. Aşağıda bir örnek verilmiştir:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

@No__t_0 türünü kullanma hakkında daha fazla bilgi için bkz. [struct](/cpp/cpp/struct-cpp).

Sınıf C++ diyagramı içindeki bir yapı şekli, etiketin **Yapı** okuduğu ve yuvarlak köşeler yerine kare köşelere sahip olduğu durumlar dışında, bir sınıf şekli gibi görünür ve çalışacaktır.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Yapı|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodla çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)