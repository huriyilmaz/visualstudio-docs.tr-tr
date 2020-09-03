---
title: Bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1eb32aa7d87da75ebf37b27aa1d425adb85f8c9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278460"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ek açıklama koşullu olduğunda, çözümleyiciye belirtmek için diğer ek açıklamalar gerekebilir.  Örneğin, bir işlevin zaman uyumlu veya zaman uyumsuz olabilecek bir değişkeni varsa, işlev şu şekilde davranır: zaman uyumlu durumda, her zaman başarılı olur, ancak zaman uyumsuz durumda, hemen başarısız olmazsa bir hata bildirir. İşlev zaman uyumlu olarak çağrıldığında, sonuç değerinin denetlenmesi, döndürülmeyeceği için kod Çözümleyicisi 'ne değer vermez.  Ancak, işlev zaman uyumsuz olarak çağrıldığında ve işlev sonucu denetlenirse, ciddi bir hata oluşabilir. Bu örnekte, `_When_` denetlemeyi etkinleştirmek için ek açıklamayı (Bu makalede daha sonra açıklanan) kullanabileceğiniz bir durum gösterilmektedir.  
  
## <a name="structural-annotations"></a>Yapısal ek açıklamaları  
 Ek açıklamaların ne zaman ve nerede uygulanacağını denetlemek için aşağıdaki yapısal ek açıklamaları kullanın.  
  
|Ek Açıklama|Description|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` , lvalue veren bir ifadedir. İçindeki ek açıklamalar `anno-list` tarafından adlandırılan nesnesine uygulanır `expr` . İçindeki her ek açıklama için, `anno-list` `expr` ek açıklama ön koşul olarak yorumlandığında ön koşul olarak yorumlanır ve ek açıklama koşul sonrası olarak yorumlandığında koşul sonrası olarak yorumlanır.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` , lvalue veren bir ifadedir. İçindeki ek açıklamalar `anno-list` tarafından adlandırılan nesnesine uygulanır `expr` . İçindeki her ek açıklama için, `anno-list` `expr` ek açıklamanın ön koşul olarak yorumlanması durumunda ve ek açıklama koşul sonrası olarak yorumlandığında koşul sonrası olarak yorumlanır.<br /><br /> `iter` , ek açıklamanın (dahil) kapsamına alınmış bir değişkenin adıdır `anno-list` . `iter` örtük bir tür içerir `long` . Herhangi bir kapsayan kapsamda aynı adlandırılmış değişkenler değerlendirmeden gizlenir.<br /><br /> `elem-count` , bir tamsayı değerlendiren bir ifadedir.|  
|`_Group_(anno-list)`|İçindeki ek açıklamalar `anno-list` her bir ek açıklama için geçerli olan Grup ek açıklamasına uygulanan herhangi bir niteleyiciye sahip olarak kabul edilir.|  
|`_When_(expr, anno-list)`|`expr` , öğesine dönüştürülebileceği bir ifadedir `bool` . Sıfır olmayan ( `true` ) olduğunda, içinde belirtilen ek açıklamalar `anno-list` geçerli kabul edilir.<br /><br /> Varsayılan olarak, içindeki her ek açıklama için, `anno-list` `expr` ek açıklama bir önkoşulun ise ve ek açıklama bir koşul ise çıktı değerlerini kullanarak giriş değerlerini kullanma olarak yorumlanır. Varsayılan değeri geçersiz kılmak için, `_Old_` giriş değerlerinin kullanılması gerektiğini göstermek üzere bir koşulu değerlendirirken iç öğesini kullanabilirsiniz. **Note:**  `_When_` Bir değişebilir değerin (örneğin, `*pLength` ), önkoşul olarak değerlendirilen sonucu, `expr` koşul sonrası tarafından değerlendirilen sonuçtan farklı olabileceğinden, buna dahil olan farklı ek açıklamalar etkinleştirilebilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 'ı anlama](../code-quality/understanding-sal.md)   
 [Işlev parametrelerine ve dönüş değerlerine açıklama ekleme](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md)   
 [Yapı ve sınıflara açıklama ekleme](../code-quality/annotating-structs-and-classes.md)   
 [Kilitleme davranışına açıklama ekleme](../code-quality/annotating-locking-behavior.md)   
 [İç Işlevler](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
