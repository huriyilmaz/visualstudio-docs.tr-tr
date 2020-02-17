---
title: 'Nasıl yapılır: __analysis_assume kullanarak ek kod bilgileri belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277979"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>Nasıl yapılır: __analysis_assume Kullanarak Ek Kod Bilgileri Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiz işleminin ve uyarıların azaltılmasına yardımcı olacak C/C++ kod için kod analizi aracına yönelik ipuçları sağlayabilirsiniz. Ek bilgi sağlamak için aşağıdaki işlevi kullanın:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-doğru olarak değerlendirilmesi için kabul edilen herhangi bir ifade.  
  
 Kod Analizi Aracı, ifade tarafından temsil edilen koşulun işlevin göründüğü noktada doğru olduğunu varsayar ve örneğin bir değişkene atama yaparak ifade değiştirilene kadar doğru kalır.  
  
> [!NOTE]
> `__analysis_assume` kod iyileştirmeyi etkilemez. Kod Analizi Aracı dışında `__analysis_assume`, işlem olmadan tanımlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kod analizi Uyarı [C6388](../code-quality/c6388.md)düzeltmek için `__analysis_assume` kullanır:  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
