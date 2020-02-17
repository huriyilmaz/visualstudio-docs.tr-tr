---
title: İç Işlevler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: a0a6cd31cbc8cf73cfa2c7e9ee7c096fa56799b9
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277966"
---
# <a name="intrinsic-functions"></a>İç İşlevler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SAL içindeki bir ifade, yan etkileri olmayan birC++ ifade olan bir C/ifadesi olabilir; Örneğin, + +,--, ve işlev çağrılarının hepsi bu bağlamda yan etkilere sahiptir.  Ancak, SAL ifadelerde kullanılabilecek bazı işlev benzeri nesneler ve bazı ayrılmış semboller sağlar. Bunlar *iç işlevler*olarak adlandırılır.  
  
## <a name="general-purpose"></a>Genel Amaçlı  
 Aşağıdaki ınstrinsic işlev ek açıklamaları SAL için genel yardımcı program sağlar.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Curr_`|Şu anda açıklanmakta olan nesne için bir eş anlamlı.  `_At_` ek açıklaması kullanımda olduğunda, `_Curr_` `_At_`ilk parametresiyle aynıdır.  Aksi takdirde, ek açıklamanın sözcüksel olarak ilişkilendirildiği parametre veya tam işlev/dönüş değeridir.|  
|`_Inexpressible_(expr)`|Bir arabelleğin boyutunun, bir ek açıklama ifadesi kullanılarak temsil edilebilmesi için çok karmaşık olduğu, örneğin bir girdi veri kümesi tarayarak ve ardından seçilen Üyeler sayımının hesaplandığı bir durumu ifade eder.|  
|`_Nullterm_length_(param)`|`param`, arabellekteki ve null Sonlandırıcı içermeyen öğelerin sayısıdır. Toplama olmayan, void olmayan türdeki herhangi bir arabelleğe uygulanabilir.|  
|`_Old_(expr)`|Önkoşula göre değerlendirildiğinde `_Old_` `expr`giriş değerini döndürür.  Koşul sonrası değerlendirildiğinde, önkoşul ' de değerlendirildiğinden `expr` değeri döndürür.|  
|`_Param_(n)`|`n`TH parametresi, 1 ' den `n`ve `n` sabit bir integral sabiti sabittir. Parametre adlandırılmışsa, bu ek açıklama parametreye adına göre erişmek için aynıdır. **Not:** `n`, üç nokta tarafından tanımlanan konumsal parametrelere başvurabilir veya adların kullanıldığı işlev Prototiplerde kullanılabilir.|  
|`return`|C/C++ ayrılmış anahtar sözcüğü `return` bir işlevin dönüş değerini göstermek için Sal ifadesinde kullanılabilir.  Değer yalnızca gönderi durumunda kullanılabilir; Bu, ön durumunda kullanmak için bir sözdizimi hatasıdır.|  
  
## <a name="string-specific"></a>Dizeye özgü  
 Aşağıdaki iç işlev ek açıklamaları dizelerin düzenlenmesini etkinleştirir. Bu işlevlerin dört dördü de aynı amaca sahiptir: null Sonlandırıcı 'dan önce bulunan türdeki öğelerin sayısını döndürmek için. Farklılıklar, başvurulan öğelerdeki veri türleridir. Karakterlerden oluşan null ile sonlandırılmış bir arabelleğin uzunluğunu belirtmek isterseniz, önceki bölümde `_Nullterm_length_(param)` ek açıklamasını kullanın.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`, dizedeki, null Sonlandırıcı içermeyen öğe sayısıdır. Bu ek açıklama, karakter dizesi türleri için ayrılmıştır.|  
|`strlen(param)`|`param`, dizedeki, null Sonlandırıcı içermeyen öğe sayısıdır. Bu ek açıklama, karakter dizileri üzerinde kullanılmak üzere ayrılmıştır ve C çalışma zamanı işlevine [strlen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)benzerdir.|  
|`wcslen(param)`|`param`, bir null Sonlandırıcı (dahil değil) olan dizedeki öğelerin sayısıdır. Bu ek açıklama geniş karakter dizileri üzerinde kullanılmak üzere ayrılmıştır ve C çalışma zamanı işlevine [wcslen ()](https://msdn.microsoft.com/library/16462f2a-1e0f-4eb3-be55-bf1c83f374c2)benzerdir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CC++ /kod HATALARıNı azaltmak Için sal ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL  anlama](../code-quality/understanding-sal.md)  
 [Işlev parametrelerine ve dönüş değerlerine açıklama ekleme](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md)   
 [Yapı ve sınıflara açıklama ekleme](../code-quality/annotating-structs-and-classes.md)   
 [Kilitleme davranışına açıklama ekleme](../code-quality/annotating-locking-behavior.md)   
 [Ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
