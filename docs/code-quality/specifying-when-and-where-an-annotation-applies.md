---
title: Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 37bee4665040b8792cdc0fa521fc75cbfe9ae1de
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018350"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme
Ek açıklama koşullu olduğunda, çözümleyiciye belirtmek için diğer ek açıklamalar gerekebilir.  Örneğin, bir işlevin zaman uyumlu veya zaman uyumsuz olabilecek bir değişkeni varsa, işlev aşağıdaki gibi davranır: Zaman uyumlu durumda, her zaman başarılı olur ancak zaman uyumsuz durumda, hemen başarısız olmazsa bir hata bildirir. İşlev zaman uyumlu olarak çağrıldığında, sonuç değerinin denetlenmesi, döndürülmeyeceği için kod Çözümleyicisi 'ne değer vermez.  Ancak, işlev zaman uyumsuz olarak çağrıldığında ve işlev sonucu denetlenirse, ciddi bir hata oluşabilir. Bu örnekte, denetlemeyi etkinleştirmek için, bu makalede daha sonra açıklanan `_When_` ek açıklamasını kullanabileceğiniz bir durum gösterilmektedir.

## <a name="structural-annotations"></a>Yapısal ek açıklamaları
Ek açıklamaların ne zaman ve nerede uygulanacağını denetlemek için aşağıdaki yapısal ek açıklamaları kullanın.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`, lvalue veren bir ifadedir. @No__t-0 ' daki ek açıklamalar `expr` tarafından adlandırılan nesneye uygulanır. @No__t-@no__t 0 ' daki her bir ek açıklama için, ek açıklamanın ön koşul olarak yorumlanması ve koşul sonrası olarak yorumlanması durumunda koşul sonrası olarak yorumlanır.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`, lvalue veren bir ifadedir. @No__t-0 ' daki ek açıklamalar `expr` tarafından adlandırılan nesneye uygulanır. @No__t-@no__t 0 ' daki her bir ek açıklama için, ek açıklama ön koşul olarak yorumlanır ve ek açıklama koşul sonrası olarak yorumlandığında koşul sonrası olarak yorumlanır.<br /><br /> `iter`, ek açıklamanın kapsamına alınmış bir değişkenin adıdır (`anno-list` dahil). `iter` örtük bir tür `long` ' dir. Herhangi bir kapsayan kapsamda aynı adlandırılmış değişkenler değerlendirmeden gizlenir.<br /><br /> `elem-count`, bir tamsayı sonucunu veren bir ifadedir.|
|`_Group_(anno-list)`|@No__t-0 ' daki ek açıklamalar, her bir ek açıklamaya uygulanan Grup ek açıklaması için geçerli olan herhangi bir niteleyiciye sahip olarak kabul edilir.|
|`_When_(expr, anno-list)`|`expr`, `bool` ' e dönüştürülebileceği bir ifadedir. Sıfır dışında (`true`), `anno-list` ' de belirtilen ek açıklamalar geçerli kabul edilir.<br /><br /> Varsayılan olarak, `anno-list` ' daki her bir ek açıklama için, ek açıklama bir önkoşulun ise ve ek açıklama bir koşul ise çıktı değerlerini kullanarak, `expr`, giriş değerlerini kullanma olarak yorumlanır. Varsayılan değeri geçersiz kılmak için, giriş değerlerinin kullanılması gerektiğini göstermek üzere bir koşulu değerlendirirken `_Old_` iç öğesini kullanabilirsiniz. **Not:**  @No__t-0 ' ın kullanımının sonucu olarak değişebilir bir değer (örneğin, `*pLength` —) kullanılırken farklı ek açıklamalar etkinleştirilebilir. bu nedenle, önkoşullardan `expr` ' nin değerlendirilen sonucu, koşul sonrası tarafından değerlendirilen sonuçtan farklı olabilir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [C/C++ Kod Hatalarını Azaltmak için SAL Ek Açıklamalarını Kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL'yi Anlama](../code-quality/understanding-sal.md)
- [İşlev Parametrelerini ve Dönüş Değerlerini Açıklama](../code-quality/annotating-function-parameters-and-return-values.md)
- [İşlev Davranışını Yorumlama](../code-quality/annotating-function-behavior.md)
- [Yapıları ve Sınıfları Yorumlama](../code-quality/annotating-structs-and-classes.md)
- [Kilitlenme Davranışını Yorumlama](../code-quality/annotating-locking-behavior.md)
- [İç İşlevler](../code-quality/intrinsic-functions.md)
- [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)