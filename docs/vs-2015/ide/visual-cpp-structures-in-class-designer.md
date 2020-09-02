---
title: Sınıf Tasarımcısı Visual C++ yapıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646759"
---
# <a name="visual-c-structures-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Yapılandırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı, anahtar sözcüğüyle belirtilen C++ yapılarını destekler `struct` . Aşağıda bir örnek verilmiştir:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Türünü kullanma hakkında daha fazla bilgi için `struct` bkz. [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Bir sınıf diyagramında C++ yapısı şekli, etiketin **Yapı** okuduğu ve yuvarlak köşeler yerine kare köşelere sahip olması dışında bir sınıf şekli gibi görünür ve çalışacaktır.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Yapı|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual C++ Code (sınıf Tasarımcısı)](../ide/working-with-visual-cpp-code-class-designer.md) [sınıfları ve yapıları](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [yapısı](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) ile çalışma
