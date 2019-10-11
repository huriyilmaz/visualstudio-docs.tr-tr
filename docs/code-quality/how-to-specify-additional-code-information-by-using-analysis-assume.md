---
title: Kod çözümleme ipuçları için _Analysis_varsay kullan
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 186ea6ac58736098720d60c644c30801073b7453
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018724"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Nasıl Yapılır: __Analysis_assume Kullanarak Ek Kod Bilgileri Belirtme

Analiz işleminin ve uyarıların azaltılmasına yardımcı olacak C/C++ kod için kod analizi aracına yönelik ipuçları sağlayabilirsiniz. Ek bilgi sağlamak için aşağıdaki işlevi kullanın:

`_Analysis_assume(`  `expr`  `)`

`expr`-true olarak değerlendirilme kabul edilen herhangi bir ifade.

Kod Analizi Aracı, ifade tarafından temsil edilen koşulun işlevin göründüğü noktada doğru olduğunu varsayar ve örneğin bir değişkene atama yaparak ifade değiştirilene kadar doğru kalır.

> [!NOTE]
> `_Analysis_assume`, kod iyileştirmeyi etkilemez. Kod Analizi aracının dışında, `_Analysis_assume`, işlem dışı olarak tanımlanır.

## <a name="example"></a>Örnek

Aşağıdaki kod, kod analizi Uyarı [C6388](../code-quality/c6388.md)düzeltmek için `_Analysis_assume` kullanır:

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [__assume](/cpp/intrinsics/assume)
