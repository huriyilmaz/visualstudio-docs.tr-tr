---
title: Sınıf Tasarımcıc++ Yapıları
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa8014835df2b5b2bd3dc68e2aaf0b079e001e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590690"
---
# <a name="c-structures-in-class-designer"></a>Sınıf Tasarımcıc++ yapıları

**Sınıf Tasarımcısı,** anahtar kelimeyle `struct`birlikte bildirilen C++ yapılarını destekler. Aşağıda bir örnek verilmiştir:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

`struct` Türü kullanma hakkında daha fazla bilgi için [bkz.](/cpp/cpp/struct-cpp)

Sınıf diyagramındaki C++ yapı şekli, etiketin **Struct'u** okuması ve yuvarlatılmış köşeler yerine kare köşeleri olması dışında sınıf şekli gibi görünür ve çalışır.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`struct StructureName {};`|**Yapı Adı**<br /><br /> Yapı|

## <a name="see-also"></a>Ayrıca bkz.

- [C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Structs](/cpp/cpp/classes-and-structs-cpp)
- [Yapı](/cpp/cpp/struct-cpp)
