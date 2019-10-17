---
title: İşlev Davranışını Yorumlama
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: b77379d0bb9dbd80f01eadf5209353b3fd12eb1c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446300"
---
# <a name="annotating-function-behavior"></a>İşlev Davranışını Yorumlama
[İşlev parametrelerine ve dönüş değerlerine](../code-quality/annotating-function-parameters-and-return-values.md)açıklama eklemek için, tüm işlevin özelliklerine ek açıklama ekleyebilirsiniz.

## <a name="function-annotations"></a>İşlev ek açıklamaları
Aşağıdaki ek açıklamalar işlev için bir bütün olarak uygulanır ve nasıl davrandığını veya neyin doğru olmasını beklediğini açıklamaktadır.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Tek başına hedeflenmemiştir; Bunun yerine, `_When_` ek açıklaması ile birlikte kullanılacak bir koşul vardır. Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> @No__t-0 parametresi, bazı işlevlerin bildiriminde bir `_Function_class_` ek açıklamasında da görüntülenen rastgele bir dizedir.  `_Called_from_function_class_`, şu anda çözümlenmekte olan işleve aynı `name` değeri olan `_Function_class_` kullanılarak açıklanmışsa sıfır olmayan bir değer döndürür. Aksi takdirde, sıfır döndürür.|
|`_Check_return_`|Bir dönüş değeri ve çağıranın bunu incelemesi gerektiğini belirten bir açıklama. İşlev void bağlamda çağrılırsa, denetleyici bir hata bildirir.|
|`_Function_class_(name)`|@No__t-0 parametresi, Kullanıcı tarafından atanan rastgele bir dizedir.  Diğer ad alanlarından farklı bir ad alanında bulunur. Bir işlev, işlev işaretçisi veya — en çok usetam — bir işlev işaretçisi türü bir veya daha fazla işlev sınıfına ait olarak belirlenebilir.|
|`_Raises_SEH_exception_`|Her zaman yapılandırılmış bir özel durum işleyicisi (SEH) özel durumu oluşturan ve `_When_` ve `_On_failure_` koşullara tabi olan bir işlevi annotates. Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|İsteğe bağlı olarak, `_When_` ve `_On_failure_` koşullara tabi bir SEH özel durumu oluşturabilen bir işlevi annotates.|
|`_Must_inspect_result_`|Dönüş değeri, parametreler ve Globals 'ler dahil olmak üzere herhangi bir çıkış değerini öğretme.  Açıklamalı nesnede bulunan değer daha sonra incelenemediği çözümleyici bir hata bildirir. "Denetleme", bir koşullu ifadede kullanılıp kullanılmadığını, bir çıkış parametresine veya genel 'e atandığını veya bir parametre olarak geçtiğini içerir.  Dönüş değerleri için `_Must_inspect_result_` `_Check_return_` ' i gerektirir.|
|`_Use_decl_annotations_`|Başlıktaki ek açıklamaların listesi yerine bir işlev tanımında (işlev gövdesi olarak da bilinir) kullanılabilir.  @No__t-0 kullanıldığında, aynı işlev için kapsam içi üst bilgisinde görünen ek açıklamalar, `_Use_decl_annotations_` ek açıklamasına sahip tanımda de mevcuttur gibi kullanılır.|

## <a name="successfailure-annotations"></a>Başarı/başarısızlık ek açıklamaları
Bir işlev başarısız olabilir ve ne zaman, işlev başarılı olduğunda sonuçları tamamlanmamış veya sonuçlardan farklı olabilir.  Aşağıdaki listedeki ek açıklamalar başarısızlık davranışını ifade etmenin yollarını sağlar.  Bu ek açıklamaları kullanmak için, bunları başarıyı tespit etmek üzere etkinleştirmeniz gerekir. Bu nedenle, @no__t 0 ek açıklaması gereklidir.  @No__t-0 ve `HRESULT` ' in, bunlara yerleşik bir @no__t 2 ek açıklaması zaten olduğunu fark edin; Ancak, `NTSTATUS` veya `HRESULT` ' te kendi `_Success_` ek açıklamanızı belirtirseniz, yerleşik ek açıklamayı geçersiz kılar.

|Ek Açıklama|Açıklama|
|----------------|-----------------|
|`_Always_(anno_list)`|@No__t-0; eşdeğeri diğer bir deyişle, `anno_list` ' deki ek açıklamalar işlevin başarılı olup olmadığını uygular.|
|`_On_failure_(anno_list)`|Yalnızca `_Success_` ' ı, bir typedef üzerinde açıkça veya örtük olarak `_Return_type_success_` aracılığıyla işlevine açıklama eklemek için de kullanılır. @No__t-0 ek açıklaması bir işlev parametresi veya dönüş değeri üzerinde olduğunda, `anno_list` ' deki (Anno) her ek açıklama `_When_(!expr, anno)` olarak kodlanmış gibi davranır; burada `expr`, gereken `_Success_` ek açıklamasına parametre olur. Bu, `_Success_` ' ın tüm koşullar `_On_failure_` için geçerli olmadığı anlamına gelir.|
|`_Return_type_success_(expr)`|Bir typedef 'e uygulanabilir. Bu türü döndüren ve açık olarak `_Success_` olmayan tüm işlevlere `_Success_(expr)` gibi açıklandığını gösterir. `_Return_type_success_` bir işlevde veya bir işlev işaretçisi typedef üzerinde kullanılamaz.|
|`_Success_(expr)`|`expr`, rvalue veren bir ifadedir. @No__t-0 ek açıklaması bir işlev bildiriminde veya tanımında olduğunda, işlevdeki ve koşul sonrasındaki her ek açıklama (`anno`), `_When_(expr, anno)` olarak kodlanmış gibi davranır. @No__t-0 ek açıklaması, parametreleri veya dönüş türü üzerinde değil yalnızca bir işlevde kullanılabilir. Bir işlevde en fazla bir `_Success_` ek açıklaması olabilir ve herhangi bir `_When_`, `_At_` veya `_Group_` olamaz. Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ Kod Hatalarını Azaltmak için SAL Ek Açıklamalarını Kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL'yi Anlama](../code-quality/understanding-sal.md)
- [İşlev Parametrelerini ve Dönüş Değerlerini Açıklama](../code-quality/annotating-function-parameters-and-return-values.md)
- [Yapıları ve Sınıfları Yorumlama](../code-quality/annotating-structs-and-classes.md)
- [Kilitlenme Davranışını Yorumlama](../code-quality/annotating-locking-behavior.md)
- [Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [İç İşlevler](../code-quality/intrinsic-functions.md)
- [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
