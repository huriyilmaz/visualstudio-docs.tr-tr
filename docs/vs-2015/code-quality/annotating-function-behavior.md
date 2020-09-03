---
title: Işlev davranışına açıklama ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7ebda5933f73e2511932f8968104327a56ee7606
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277874"
---
# <a name="annotating-function-behavior"></a>İşlev Davranışını Yorumlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[İşlev parametrelerine ve dönüş değerlerine](../code-quality/annotating-function-parameters-and-return-values.md)açıklama eklemek için, tüm işlevin özelliklerine ek açıklama ekleyebilirsiniz.  
  
## <a name="function-annotations"></a>İşlev ek açıklamaları  
 Aşağıdaki ek açıklamalar işlev için bir bütün olarak uygulanır ve nasıl davrandığını veya neyin doğru olmasını beklediğini açıklamaktadır.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Called_from_function_class_(name)`|Tek başına hedeflenmemiştir; Bunun yerine, ek açıklamayla birlikte kullanılacak bir koşul vardır `_When_` . Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name`Parametresi, `_Function_class_` bazı işlevlerin bildirimindeki ek açıklamada de görünen rastgele bir dizedir.  `_Called_from_function_class_` Şu anda çözümlenmekte olan işleve `_Function_class_` aynı değere sahip olan ' i kullanarak açıklanmışsa sıfır dışında bir değer döndürür `name` ; Aksi takdirde, sıfır döndürür.|  
|`_Check_return_`|Bir dönüş değeri ve çağıranın bunu incelemesi gerektiğini belirten bir açıklama. İşlev void bağlamda çağrılırsa, denetleyici bir hata bildirir.|  
|`_Function_class_(name)`|`name`Parametresi, Kullanıcı tarafından atanan rastgele bir dizedir.  Diğer ad alanlarından farklı bir ad alanında bulunur. Bir işlev, işlev işaretçisi veya — en çok usetam — bir işlev işaretçisi türü bir veya daha fazla işlev sınıfına ait olarak belirlenebilir.|  
|`_Raises_SEH_exception_`|Her zaman yapılandırılmış bir özel durum işleyicisi (SEH) özel durumu, konu ve koşullara tabi olan bir işlevi annotates `_When_` `_On_failure_` . Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|İsteğe bağlı olarak bir SEH özel durumu, konu ve koşullara tabi olabilecek bir işlevi annotates `_When_` `_On_failure_` .|  
|`_Must_inspect_result_`|Dönüş değeri, parametreler ve Globals 'ler dahil olmak üzere herhangi bir çıkış değerini öğretme.  Açıklamalı nesnede bulunan değer daha sonra incelenemediği çözümleyici bir hata bildirir. "Denetleme", bir koşullu ifadede kullanılıp kullanılmadığını, bir çıkış parametresine veya genel 'e atandığını veya bir parametre olarak geçtiğini içerir.  Dönüş değerleri için, şunu `_Must_inspect_result_` gösterir `_Check_return_` .|  
|`_Use_decl_annotations_`|Başlıktaki ek açıklamaların listesi yerine bir işlev tanımında (işlev gövdesi olarak da bilinir) kullanılabilir.  `_Use_decl_annotations_`Kullanıldığında, aynı işlev için kapsam içi üst bilgisinde görünen ek açıklamalar, ek açıklamasına sahip tanımda de mevcuttur gibi kullanılır `_Use_decl_annotations_` .|  
  
## <a name="successfailure-annotations"></a>Başarı/başarısızlık ek açıklamaları  
 Bir işlev başarısız olabilir ve ne zaman, işlev başarılı olduğunda sonuçları tamamlanmamış veya sonuçlardan farklı olabilir.  Aşağıdaki listedeki ek açıklamalar başarısızlık davranışını ifade etmenin yollarını sağlar.  Bu ek açıklamaları kullanmak için, bunları başarıyı tespit etmek üzere etkinleştirmeniz gerekir. Bu nedenle, `_Success_` ek açıklama gereklidir.  `NTSTATUS`Ve `HRESULT` içinde yerleşik olarak bulunan bir ek açıklamanın zaten olduğunu fark edin `_Success_` ; ancak, `_Success_` veya üzerinde kendi ek açıklamanızı `NTSTATUS` belirtirseniz `HRESULT` , yerleşik ek açıklamayı geçersiz kılar.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|`_Always_(anno_list)`|Eşdeğerdir `anno_list _On_failure_(anno_list)` ; diğer bir deyişle, içindeki ek açıklamalar `anno_list` işlevin başarılı olup olmadığını uygular.|  
|`_On_failure_(anno_list)`|Yalnızca, `_Success_` bir typedef üzerinde açıkça veya örtük olarak işlev üzerine eklemek için de kullanıldığında kullanılır `_Return_type_success_` . `_On_failure_`Ek açıklama bir işlev parametresi veya dönüş değeri üzerinde olduğunda, `anno_list` (Anno) içindeki her ek açıklama olarak kodlanmış gibi davranır `_When_(!expr, anno)` , burada `expr` parametre gerekli `_Success_` ek açıklamanın parametresidir. Bu, ' nin `_Success_` tüm koşullar için geçerli olmadığı anlamına gelir `_On_failure_` .|  
|`_Return_type_success_(expr)`|Bir typedef 'e uygulanabilir. Bu türü döndüren ve açıkça sahip olmayan tüm işlevlere sahip `_Success_` oldukları gibi açıklama eklenmiş olduğunu gösterir `_Success_(expr)` . `_Return_type_success_` bir işlevde veya bir işlev işaretçisi typedef üzerinde kullanılamaz.|  
|`_Success_(expr)`|`expr` , rvalue veren bir ifadedir. `_Success_`Ek açıklama bir işlev bildiriminde veya tanımında olduğunda, `anno` işlevdeki ve koşul sonrasındaki her ek açıklama () olarak kodlanmış gibi davranır `_When_(expr, anno)` . `_Success_`Ek açıklama, parametreleri veya dönüş türü üzerinde değil, yalnızca bir işlevde kullanılabilir. Bir işlevde en fazla bir `_Success_` ek açıklama olabilir ve herhangi bir `_When_` , veya içinde olamaz `_At_` `_Group_` . Daha fazla bilgi için bkz. [bir ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 'ı anlama](../code-quality/understanding-sal.md)   
 [Işlev parametrelerine ve dönüş değerlerine açıklama ekleme](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Yapı ve sınıflara açıklama ekleme](../code-quality/annotating-structs-and-classes.md)   
 [Kilitleme davranışına açıklama ekleme](../code-quality/annotating-locking-behavior.md)   
 [Ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç Işlevler](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
