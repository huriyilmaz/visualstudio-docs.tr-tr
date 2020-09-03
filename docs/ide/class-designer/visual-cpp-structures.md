---
title: Sınıf Tasarımcısı 'de C++ yapıları
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590690"
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
