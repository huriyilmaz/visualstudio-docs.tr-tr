---
title: Sınıf Tasarımcısında Visual C++ Yapılandırmaları
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
ms.openlocfilehash: da786e6f598b4b28aeb7758df41f54ea23c4185d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647590"
---
# <a name="visual-c-structures-in-class-designer"></a>Sınıf Tasarımcısı C++ görsel yapılar

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

- [Visual C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)