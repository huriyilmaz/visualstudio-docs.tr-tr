---
title: Kod Analizi ipuçları için _Analysis_assume kullanma
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
ms.openlocfilehash: 9933a013ed4f2df0978fb66e3aff87b4cdc024f9
ms.sourcegitcommit: c6af923c1f485959d751b23ab3f03541013fc4a7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925957"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>Nasıl yapılır: _Analysis_assume kullanarak ek kod bilgileri belirtme

Analiz işleminin ve uyarıların azaltılmasına yardımcı olacak C/C++ kod için kod analizi aracına yönelik ipuçları sağlayabilirsiniz. Ek bilgi sağlamak için aşağıdaki işlevi kullanın:

`_Analysis_assume(`  `expr`  `)`

`expr`-doğru olarak değerlendirilmesi için kabul edilen herhangi bir ifade.

Kod Analizi Aracı, ifade tarafından temsil edilen koşulun işlevin göründüğü noktada doğru olduğunu varsayar ve örneğin bir değişkene atama yaparak ifade değiştirilene kadar doğru kalır.

> [!NOTE]
> `_Analysis_assume` kod iyileştirmeyi etkilemez. Kod Analizi Aracı dışında `_Analysis_assume`, işlem olmadan tanımlanır.

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
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [__assume](/cpp/intrinsics/assume)
