---
title: İşlev Parametrelerini ve Dönüş Değerlerini Açıklama
ms.date: 07/11/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 1001b37509432a7ae95a565d90d972d2043fdeab
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72016012"
---
# <a name="annotating-function-parameters-and-return-values"></a>İşlev Parametrelerini ve Dönüş Değerlerini Açıklama
Bu makalede basit işlev parametreleri için ek açıklamaların tipik kullanımları ve yapı ve sınıf işaretçileri ve birçok arabellek türü açıklanmaktadır.  Bu makalede ayrıca ek açıklamalar için ortak kullanım desenleri gösterilmektedir. İşlevlerle ilgili ek ek açıklamalar için bkz. [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>İşaretçi parametreleri
Aşağıdaki tablodaki ek açıklamalar için, işaretçi parametresine açıklama eklendiğinde, işaretçi null ise çözümleyici bir hata bildirir.  Bu, işaretçiler için ve işaret edilen tüm veri öğeleri için geçerlidir.

**Ek açıklamalar ve açıklamalar**

- `_In_`

     Yapılar, yapılar, yapılara yönelik işaretçiler ve benzeri bir giriş parametresi olan annotates.  Açıkça basit dolandırıcıklar üzerinde kullanılabilir.  Parametrenin ön durumunda geçerli olması ve değiştirilmeyecektir.

- `_Out_`

     Yapıları, yapıları, yapılara yönelik işaretçileri ve benzeri bir çıkış parametresi olan annotates.  Bunu değer döndürmeyen bir nesneye uygulamayın — Örneğin, değere göre geçirilmiş bir skaler.  Parametrenin ön durumunda geçerli olması gerekmez, ancak durum sonrası için geçerli olmalıdır.

- `_Inout_`

     İşlev tarafından değiştirilecek bir parametreyi annotates.  Hem ön durum hem de durum durumunda geçerli olmalıdır, ancak çağrıdan önce ve sonra farklı değerlere sahip olduğu varsayılır. Değiştirilebilir bir değere uygulamanız gerekir.

- `_In_z_`

     Giriş olarak kullanılan null ile sonlandırılmış bir dize işaretçisi.  Dize, ön durumunda geçerli olmalıdır.  Zaten doğru ek açıklamaları olan `PSTR` çeşitleri tercih edilir.

- `_Inout_z_`

     Değiştirilecek, null ile sonlandırılmış bir karakter dizisine yönelik bir işaretçi.  Çağrıdan önce ve sonra geçerli olmalıdır, ancak değer değişmiş olarak kabul edilir.  Null Sonlandırıcı taşınabilir, ancak yalnızca orijinal null sonlandırıcısına kadar olan öğelere erişilebilir.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     İşlev tarafından okunan dizi için bir işaretçi.  Dizi, tümünün geçerli olması gereken `s` öğelerinin boyutudur.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_In_reads_z_(s)`

     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Null sonlandırıcıya kadar olan öğeler — veya null Sonlandırıcı yoksa `s`, ön durumda geçerli olmalıdır.  Boyut bayt olarak bilindiğinde, öğe boyutuna göre `s` ' ı ölçeklendirin.

- `_In_reads_or_z_(s)`

     Null sonlandırılmış veya bilinen bir boyut veya her ikisi içeren bir dizi işaretçisi. Null sonlandırıcıya kadar olan öğeler — veya null Sonlandırıcı yoksa `s`, ön durumda geçerli olmalıdır.  Boyut bayt olarak bilindiğinde, öğe boyutuna göre `s` ' ı ölçeklendirin.  (@No__t-0 ailesi için kullanılır.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     İşlev tarafından yazılacak `s` öğeleri (yanıt. bayt) dizisine yönelik bir işaretçi.  Dizi öğelerinin ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olan öğe sayısı belirtilmemiş olur.  Parametre türünde ek açıklamalar varsa, bunlar durum sonrası ' a uygulanır. Örneğin, aşağıdaki kodu göz önünde bulundurun.

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     Bu örnekte, çağıran, `p1` için `size` öğelerinin bir arabelleğini sağlar.  `MyStringCopy`, bu öğelerin bazılarını geçerli hale getirir. Daha da önemlisi, `PWSTR` ' deki `_Null_terminated_` ek açıklaması, durum sonrası `p1` ' nin null sonlandırıldığı anlamına gelir.  Bu şekilde, geçerli öğe sayısı hala iyi tanımlanmış, ancak belirli bir öğe sayısı gerekli değildir.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_Out_writes_z_(s)`

     @No__t-0 öğelerinin dizisine yönelik bir işaretçi.  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası 'de, mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler geçerli olmalıdır.  Boyut bayt olarak bilindiğinde, öğe boyutuna göre `s` ' ı ölçeklendirin.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Bir dizi için, hem okunan hem de işlevine yazılan bir işaretçi.  @No__t-0 öğelerinin boyutudur ve ön durum ve sonrası durumunda geçerli olur.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_Inout_updates_z_(s)`

     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler, hem ön durum hem de durum sonrası için geçerli olmalıdır.  Durum sonrası değeri, ön durumundaki değerden farklı olacak şekilde belirlenir; Bu, null Sonlandırıcı konumunu içerir. Boyut bayt olarak bilindiğinde, öğe boyutuna göre `s` ' ı ölçeklendirin.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     @No__t-0 öğelerinin dizisine yönelik bir işaretçi.  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası, @no__t -0-TH öğesine kadar olan öğelerin geçerli olması gerekir.  Boyut bayt olarak bilindiğinde, `s` ve `c` ' i öğe boyutuna göre ölçeklendirin ve şu şekilde tanımlanan `_bytes_` türevini kullanın:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Diğer bir deyişle, ön durumunda `s` ' a kadar olan arabellekte bulunan her öğe, son durum durumunda geçerlidir.  Örneğin:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     İşlev tarafından hem okunan hem yazılan dizi için bir işaretçi.  Bu, tümünün ön durumunda geçerli olması gereken `s` öğelerinin boyutudur ve `c` öğelerinin durum sonrası geçerli olması gerekir.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_Inout_updates_z_(s)`

     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler, hem ön durum hem de durum sonrası için geçerli olmalıdır.  Durum sonrası değeri, ön durumundaki değerden farklı olacak şekilde belirlenir; Bu, null Sonlandırıcı konumunu içerir. Boyut bayt olarak bilindiğinde, öğe boyutuna göre `s` ' ı ölçeklendirin.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     @No__t-0 öğelerinin dizisine yönelik bir işaretçi.  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası, @no__t -0-TH öğesine kadar olan öğelerin geçerli olması gerekir.  Boyut bayt olarak bilindiğinde, `s` ve `c` ' i öğe boyutuna göre ölçeklendirin ve şu şekilde tanımlanan `_bytes_` türevini kullanın:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Diğer bir deyişle, ön durumunda `s` ' a kadar olan arabellekte bulunan her öğe, son durum durumunda geçerlidir.  Örneğin:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     İşlev tarafından hem okunan hem yazılan dizi için bir işaretçi.  Bu, tümünün ön durumunda geçerli olması gereken `s` öğelerinin boyutudur ve `c` öğelerinin durum sonrası geçerli olması gerekir.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     @No__t-0 öğelerinin işlevi tarafından okunan ve yazılan dizi için bir işaretçi. Eşdeğer olarak tanımlanan:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Diğer bir deyişle, ön durumunda `s` ' a kadar olan arabellekte bulunan her öğe, ön durum ve sonrası durumunda geçerlidir.

     @No__t-0 değişkeni, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeleri yalnızca `wchar_t` kullanan benzer bir işlev olduğunda `_bytes_` türevini kullanır.

- `_In_reads_to_ptr_(p)`

     @No__t-0 @ no__t-1 @ no__t-2 ifadesi (yani, `p` eksi `_Curr_`) uygun dil standardı tarafından tanımlanan dizi için bir işaretçi.  @No__t-0 ' dan önceki öğelerin ön durumunda geçerli olması gerekir.

- `_In_reads_to_ptr_z_(p)`

     @No__t-0 @ no__t-1 @ no__t-2 ifadesi (yani, `p` eksi `_Curr_`) uygun dil standardı tarafından tanımlanan, null sonlandırılmış dizi işaretçisi.  @No__t-0 ' dan önceki öğelerin ön durumunda geçerli olması gerekir.

- `_Out_writes_to_ptr_(p)`

     @No__t-0 @ no__t-1 @ no__t-2 ifadesi (yani, `p` eksi `_Curr_`) uygun dil standardı tarafından tanımlanan dizi için bir işaretçi.  @No__t-0 ' dan önceki öğelerin ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olmalıdır.

- `_Out_writes_to_ptr_z_(p)`

     @No__t-0 @ no__t-1 @ no__t-2 ifadesi (yani, `p` eksi `_Curr_`) uygun dil standardı tarafından tanımlanan, null sonlandırılmış dizi işaretçisi.  @No__t-0 ' dan önceki öğelerin ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olmalıdır.

## <a name="optional-pointer-parameters"></a>İsteğe bağlı Işaretçi parametreleri

Bir işaretçi parametresi ek açıklaması `_opt_` içerdiğinde, parametrenin null olabileceğini gösterir. Aksi takdirde, ek açıklama `_opt_` içermeyen sürümle aynı şekilde çalışır. İşaretçi parametresi ek açıklamaların `_opt_` türevlerini listesi aşağıdadır:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Çıkış Işaretçisi parametreleri
Çıkış işaretçisi parametreleri, parametre ve işaret konumu üzerinde null olma durumunu belirsizliğini ortadan kaldırmak için özel bir gösterim gerektirir.

**Ek açıklamalar ve açıklamalar**

- `_Outptr_`

   Parametre null olamaz ve durum son durumunda, işaret edilen konum null olamaz ve geçerli olmalıdır.

- `_Outptr_opt_`

   Parametre null olabilir, ancak durum sonrası, noktadan sonra gelen konum null olamaz ve geçerli olmalıdır.

- `_Outptr_result_maybenull_`

   Parametre null olamaz ve durum son durumunda, işaret edilen konum null olabilir.

- `_Outptr_opt_result_maybenull_`

   Parametre null olabilir ve durum son durumunda, işaret edilen konum null olabilir.

  Aşağıdaki tabloda ek alt dizeler, ek açıklamanın anlamını daha fazla nitelemek için ek bir açıklama adına eklenir.  Çeşitli alt dizeler `_z`, `_COM_`, `_buffer_`, `_bytebuffer_` ve `_to_` ' dir.

> [!IMPORTANT]
> Not ettiğiniz arabirim COM ise, bu ek açıklamaların COM formunu kullanın. Diğer tür arabirimlerle COM ek açıklamalarını kullanmayın.

**Ek açıklamalar ve açıklamalar**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   Döndürülen işaretçinin `_Null_terminated_` ek açıklaması vardır.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Döndürülen işaretçinin COM semantiği vardır ve bu nedenle döndürülen işaretçinin null olduğu `_On_failure_` koşulunu taşır.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Döndürülen işaretçi `s` öğe veya bayt boyutundaki geçerli bir arabelleğe işaret ediyor.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Döndürülen işaretçi `s` öğe veya bayt boyutunda bir arabelleğe işaret eder; ilk `c` geçerli olur.

  Belirli arabirim kuralları, hata durumunda çıkış parametrelerinin null olduğunu varsayar.  Açık COM kodu hariç, aşağıdaki tablodaki formlar tercih edilir.  COM kodu için, önceki bölümde listelenen ilgili COM formlarını kullanın.

  **Ek açıklamalar ve açıklamalar**

- `_Result_nullonfailure_`

   Diğer ek açıklamaları değiştirir. İşlev başarısız olursa sonuç null olarak ayarlanır.

- `_Result_zeroonfailure_`

   Diğer ek açıklamaları değiştirir. İşlev başarısız olursa sonuç sıfır olarak ayarlanır.

- `_Outptr_result_nullonfailure_`

   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama isteğe bağlı olmayan bir parametre içindir.

- `_Outptr_opt_result_nullonfailure_`

   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama isteğe bağlı bir parametre içindir.

- `_Outref_result_nullonfailure_`

   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama bir başvuru parametresi içindir.

## <a name="output-reference-parameters"></a>Çıkış başvurusu parametreleri

Başvuru parametresinin ortak kullanımı çıkış parametrelerine yöneliktir.  Basit çıkış başvuru parametreleri için — örneğin, `int&` — `_Out_` doğru semantiğini sağlar.  Ancak, çıkış değeri bir işaretçisiyse — örneğin `int *&` — `_Outptr_ int **` gibi denk işaretçi ek açıklamaları doğru semantiğini sağlamaz.  İşaretçi türleri için çıkış başvurusu parametrelerinin semantiğini öz için, bu bileşik ek açıklamaları kullanın:

**Ek açıklamalar ve açıklamalar**

- `_Outref_`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz.

- `_Outref_result_maybenull_`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir.

- `_Outref_result_buffer_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. @No__t-0 öğelerinin geçerli arabelleğinin boyutunu gösterir.

- `_Outref_result_bytebuffer_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. @No__t-0 bayt boyutundaki geçerli arabelleğe işaret eder.

- `_Outref_result_buffer_to_(s, c)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. İlk `c` ' in geçerli olduğu `s` öğelerinden oluşan arabelleğe işaret eder.

- `_Outref_result_bytebuffer_to_(s, c)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. İlk `c` ' in geçerli olduğu `s` baytlık arabelleğe işaret eder.

- `_Outref_result_buffer_all_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. @No__t 0 geçerli öğelerin geçerli arabelleğini işaret eder.

- `_Outref_result_bytebuffer_all_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. Geçerli öğelerin @no__t geçerli arabelleğini işaret eder.

- `_Outref_result_buffer_maybenull_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. @No__t-0 öğelerinin geçerli arabelleğinin boyutunu gösterir.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. @No__t-0 bayt boyutundaki geçerli arabelleğe işaret eder.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. İlk `c` ' in geçerli olduğu `s` öğelerinden oluşan arabelleğe işaret eder.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. İlk `c` ' in geçerli olduğu `s` baytlık arabelleğe işaret eder.

- `_Outref_result_buffer_all_maybenull_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. @No__t 0 geçerli öğelerin geçerli arabelleğini işaret eder.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. Geçerli öğelerin @no__t geçerli arabelleğini işaret eder.

## <a name="return-values"></a>Dönüş Değerleri

Bir işlevin dönüş değeri `_Out_` parametresine benzer, ancak farklı bir de başvuru düzeyindedir ve işaretçi kavramını sonuca düşünmek zorunda kalmazsınız.  Aşağıdaki ek açıklamalar için, dönüş değeri, bir skalar, bir struct işaretçisi veya bir arabelleğin işaretçisi olan açıklamalı nesnedir. Bu ek açıklamalar karşılık gelen `_Out_` ek açıklaması ile aynı semantiğe sahiptir.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Biçim dizesi parametreleri

- `_Printf_format_string_`, parametrenin bir `printf` ifadesinde kullanılmak üzere bir biçim dizesi olduğunu gösterir.

     **Örnek**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`, parametrenin bir `scanf` ifadesinde kullanılmak üzere bir biçim dizesi olduğunu gösterir.

     **Örnek**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`, parametrenin bir `scanf_s` ifadesinde kullanılmak üzere bir biçim dizesi olduğunu gösterir.

     **Örnek**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Diğer yaygın ek açıklamalar

**Ek açıklamalar ve açıklamalar**

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametresi, alanı veya sonucu, `low` ile `hi` arasında (dahil) aralığındadır.  İlgili bir ön durum veya durum sonrası koşulları ile birlikte açıklamalı nesneye uygulanan `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` ile eşdeğerdir.

    > [!IMPORTANT]
    > Adlar "ın" ve "Out" içerse de, `_In_` ve `_Out_` semantiği bu ek açıklamalar için **uygulanmaz.**

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Açıklamalı değer tam olarak `expr` ' dır.  İlgili bir ön durum veya durum sonrası koşulları ile birlikte açıklamalı nesneye uygulanan `_Satisfies_(_Curr_ == expr)` ile eşdeğerdir.

- `_Struct_size_bytes_(size)`

     Bir struct veya Class bildirimi için geçerlidir.  Bu türdeki geçerli bir nesnenin, `size` tarafından verilen bayt sayısıyla, belirtilen tür ile daha büyük olabileceğini gösterir.  Örneğin:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     @No__t-1 türündeki `pM` parametresinin bayt cinsinden arabellek boyutu şu şekilde yapılır:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>İlgili Kaynaklar

[Kod Analizi ekip blogu](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Ayrıca Bkz.

- [C/C++ Kod Hatalarını Azaltmak için SAL Ek Açıklamalarını Kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [SAL'yi Anlama](../code-quality/understanding-sal.md)
- [İşlev Davranışını Yorumlama](../code-quality/annotating-function-behavior.md)
- [Yapıları ve Sınıfları Yorumlama](../code-quality/annotating-structs-and-classes.md)
- [Kilitlenme Davranışını Yorumlama](../code-quality/annotating-locking-behavior.md)
- [Açıklamanın Ne Zaman ve Nereye Uygulanacağını Belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [İç İşlevler](../code-quality/intrinsic-functions.md)
- [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)