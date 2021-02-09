---
title: Karışık Minimum Kurallar kural kümesi
ms.date: 11/04/2016
description: Visual Studio 'da karma minimum Kurallar kural kümesi hakkında bilgi edinin. Ortak dil çalışma zamanını destekleyen C++ projeleri için kuralların açıklamalarını inceleyin.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54ba61f3d4f82a5db25d0079193955a5569afa8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867886"
---
# <a name="mixed-minimum-rules-rule-set"></a>Karışık Minimum Kurallar kural kümesi

Microsoft Mixed minimum kuralları, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere, ortak dil çalışma zamanını destekleyen C++ projelerindeki en kritik sorunlara odaklanmaktadır.

Bu kuralı, ortak dil çalışma zamanını destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine ekleyin.

|Kural|Description|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Başlatılmamış belleği kullanma|
|[C6011](/cpp/code-quality/c6011)|Null Işaretçisinin başvurusu|
|[C6029](/cpp/code-quality/c6029)|Işaretlenmemiş değer kullanımı|
|[C6053](/cpp/code-quality/c6053)|Çağrıdan sıfır sonlandırma|
|[C6059](/cpp/code-quality/c6059)|Hatalı birleştirme|
|[C6063](/cpp/code-quality/c6063)|Biçimlendirme Işlevinde dize bağımsız değişkeni eksik|
|[C6064](/cpp/code-quality/c6064)|Biçimlendirme Işlevinde eksik tamsayı bağımsız değişkeni|
|[C6066](/cpp/code-quality/c6066)|Biçimlendirme Işlevinde eksik Işaretçi değişkeni|
|[C6067](/cpp/code-quality/c6067)|Biçimlendirme Işlevinde eksik dize Işaretçisi bağımsız değişkeni|
|[C6101](/cpp/code-quality/c6101)|Başlatılmamış bellek döndürülüyor|
|[C6200](/cpp/code-quality/c6200)|Dizin, arabellek üst sınırını aşıyor|
|[C6201](/cpp/code-quality/c6201)|Dizin yığın arabelleği üst sınırını aşıyor|
|[C6270](/cpp/code-quality/c6270)|Biçimlendirme Işlevinde float bağımsız değişkeni eksik|
|[C6271](/cpp/code-quality/c6271)|Biçim Işlevine fazladan bağımsız değişken|
|[C6272](/cpp/code-quality/c6272)|Biçimlendirme Işlevinde kayan olmayan bağımsız değişken|
|[C6273](/cpp/code-quality/c6273)|Biçimlendirme Işlevinde tamsayı olmayan bağımsız değişken|
|[C6274](/cpp/code-quality/c6274)|Biçimlendirme Işlevinde karakter olmayan bağımsız değişken|
|[C6276](/cpp/code-quality/c6276)|Geçersiz dize dönüştürme|
|[C6277](/cpp/code-quality/c6277)|Geçersiz CreateProcess çağrısı|
|[C6284](/cpp/code-quality/c6284)|Biçimlendirme Işlevine geçersiz nesne değişkeni|
|[C6290](/cpp/code-quality/c6290)|Logical-Not Bitwise-And önceliği|
|[C6291](/cpp/code-quality/c6291)|Logical-Not Bitwise-Or önceliği|
|[C6302](/cpp/code-quality/c6302)|Biçimlendirme Işlevine geçersiz karakter dizesi değişkeni|
|[C6303](/cpp/code-quality/c6303)|Biçimlendirme Işlevine geçersiz geniş karakter dizesi değişkeni|
|[C6305](/cpp/code-quality/c6305)|Eşleşmeyen boyut ve sayı kullanımı|
|[C6306](/cpp/code-quality/c6306)|Değişken bağımsız değişken Işlev çağrısı yanlış|
|[C6328](/cpp/code-quality/c6328)|Olası bağımsız değişken türü uyumsuzluğu|
|[C6385](/cpp/code-quality/c6385)|Okuma taşması|
|[C6386](/cpp/code-quality/c6386)|Yazma taşması|
|[C6387](/cpp/code-quality/c6387)|Geçersiz parametre değeri|
|[C6500](/cpp/code-quality/c6500)|Geçersiz öznitelik özelliği|
|[C6501](/cpp/code-quality/c6501)|Çakışan öznitelik özellik değerleri|
|[C6503](/cpp/code-quality/c6503)|Başvurular null olamaz|
|[C6504](/cpp/code-quality/c6504)|Işaretçi olmayan üzerinde null|
|[C6505](/cpp/code-quality/c6505)|Void üzerinde MustCheck|
|[C6506](/cpp/code-quality/c6506)|Işaretçi olmayan veya dizide arabellek boyutu|
|[C6508](/cpp/code-quality/c6508)|Sabit üzerinde yazma erişimi|
|[C6509](/cpp/code-quality/c6509)|Ön koşul üzerinde kullanılan dönüş|
|[C6510](/cpp/code-quality/c6510)|Işaretçili olmayan boş değer sonlandırıldı|
|[C6511](/cpp/code-quality/c6511)|MustCheck Evet veya Hayır olmalıdır|
|[C6513](/cpp/code-quality/c6513)|Arabellek boyutu olmadan öğe boyutu|
|[C6514](/cpp/code-quality/c6514)|Arabellek boyutu, dizi boyutunu aşıyor|
|[C6515](/cpp/code-quality/c6515)|Işaretçi olmayan ara bellek boyutu|
|[C6516](/cpp/code-quality/c6516)|Öznitelikte özellik yok|
|[C6517](/cpp/code-quality/c6517)|Okunabilir olmayan arabellekte geçerli boyut|
|[C6518](/cpp/code-quality/c6518)|Yazılabilir olmayan arabellekte yazılabilir boyut|
|[C6522](/cpp/code-quality/c6522)|Geçersiz boyut dize türü|
|[C6525](/cpp/code-quality/c6525)|Geçersiz boyut dizesine ulaşılamıyor konumu|
|[C6527](/cpp/code-quality/c6527)|Geçersiz ek açıklama: ' gereksiz Srelease ' özelliği void türünün değerleri üzerinde kullanılamaz|
|[C6530](/cpp/code-quality/c6530)|Tanınmayan biçim dizesi stili|
|[C6540](/cpp/code-quality/c6540)|Bu işlev üzerinde öznitelik ek açıklamaları kullanımı, var olan tüm __declspec ek açıklamalarını geçersiz kılar|
|[C6551](/cpp/code-quality/c6551)|Geçersiz boyut belirtimi: ifade ayrıştırılamıyor|
|[C6552](/cpp/code-quality/c6552)|Geçersiz Deref = veya Notref =: ifade ayrıştırılamıyor|
|[C6701](/cpp/code-quality/c6701)|Değer geçerli bir Evet/Hayır/belki değeri değil|
|[C6702](/cpp/code-quality/c6702)|Değer bir dize değeri değil|
|[C6703](/cpp/code-quality/c6703)|Değer bir sayı değil|
|[C6704](/cpp/code-quality/c6704)|Beklenmeyen ek açıklama Ifadesi hatası|
|[C6705](/cpp/code-quality/c6705)|Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşleşmiyor|
|[C6706](/cpp/code-quality/c6706)|Ek açıklama için beklenmeyen ek açıklama hatası|
|[C28021](/cpp/code-quality/c28021)|Açıklama eklenen parametrenin bir işaretçi olması gerekir|
|[C28182](/cpp/code-quality/c28182)|NULL işaretçiyle başvuruluyor. İşaretçi, başka bir işaretçi ile aynı NULL değeri içeriyor.|
|[C28202](/cpp/code-quality/c28202)|Statik olmayan üyeye geçersiz başvuru|
|[C28203](/cpp/code-quality/c28203)|Sınıf üyesine belirsiz başvuru.|
|[C28205](/cpp/code-quality/c28205)|\_\_ \_ \_ \_ Hatalı bir bağlamda kullanılan başarılı veya hatalı|
|[C28206](/cpp/code-quality/c28206)|Sol işlenen bir yapıya işaret ediyor, '-> ' kullanın|
|[C28207](/cpp/code-quality/c28207)|Sol işlenen bir struct, '. ' kullanın|
|[C28210](/cpp/code-quality/c28210)|__On_failure bağlamı için ek açıklamalar açık bir ön bağlamda olmamalıdır|
|[C28211](/cpp/code-quality/c28211)|SAL_context için beklenen statik bağlam adı|
|[C28212](/cpp/code-quality/c28212)|Ek açıklama için beklenen işaretçi ifadesi|
|[C28213](/cpp/code-quality/c28213)|\_ \_ Decl \_ ek açıklamalarını kullan \_ ek açıklaması, önceki bir bildirime göre başvurulmadan başvurmak için kullanılmalıdır.|
|[C28214](/cpp/code-quality/c28214)|Öznitelik parametresi adları P1 olmalıdır... P9 olmalıdır|
|[C28215](/cpp/code-quality/c28215)|Typedüzeltmesini zaten bir tür düzeltmesine sahip olan bir parametreye uygulanamaz|
|[C28216](/cpp/code-quality/c28216)|CheckReturn ek açıklaması yalnızca belirli işlev parametresi için Sonkoşulları için geçerlidir.|
|[C28217](/cpp/code-quality/c28217)|İşlev için, ek açıklamanın parametre sayısı dosyada bulunan ile eşleşmiyor|
|[C28218](/cpp/code-quality/c28218)|İşlev parametresi için ek açıklamanın parametresi dosyada bulunan ile eşleşmiyor|
|[C28219](/cpp/code-quality/c28219)|Ek açıklamada parametre ek açıklaması için beklenen numaralandırma üyesi|
|[C28220](/cpp/code-quality/c28220)|Ek açıklamada parametre ek açıklaması için beklenen tamsayı ifadesi|
|[C28221](/cpp/code-quality/c28221)|Ek açıklamada parametre için beklenen dize ifadesi|
|[C28222](/cpp/code-quality/c28222)|\_ek açıklama için __yes, _No veya \_ _maybe bekleniyor|
|[C28223](/cpp/code-quality/c28223)|Ek açıklama, parametre için beklenen belirteç/tanımlayıcı bulunamadı|
|[C28224](/cpp/code-quality/c28224)|Ek açıklama parametre gerektiriyor|
|[C28225](/cpp/code-quality/c28225)|Ek açıklamada gerekli parametrelerin doğru sayısı bulunamadı|
|[C28226](/cpp/code-quality/c28226)|Ek açıklama aynı zamanda bir PrimOp olamaz (geçerli bildirimde)|
|[C28227](/cpp/code-quality/c28227)|Ek açıklama aynı zamanda bir PrimOp olamaz (önceki bildirime bakın)|
|[C28228](/cpp/code-quality/c28228)|Ek açıklama parametresi: ek açıklamalarda tür kullanılamaz|
|[C28229](/cpp/code-quality/c28229)|Ek açıklama parametreleri desteklemiyor|
|[C28230](/cpp/code-quality/c28230)|Parametre türünün üyesi yok.|
|[C28231](/cpp/code-quality/c28231)|Ek açıklama yalnızca dizide geçerlidir|
|[C28232](/cpp/code-quality/c28232)|herhangi bir ek açıklamaya ön, post veya deref uygulanmadı|
|[C28233](/cpp/code-quality/c28233)|bir bloğa ön, sonrası veya deref uygulandı|
|[C28234](/cpp/code-quality/c28234)|__at ifadesi geçerli işleve uygulanmıyor|
|[C28235](/cpp/code-quality/c28235)|İşlev bir ek açıklama olarak tek başına kullanılamaz|
|[C28236](/cpp/code-quality/c28236)|Ek açıklama bir ifadede kullanılamaz|
|[C28237](/cpp/code-quality/c28237)|Parametresindeki ek açıklama artık desteklenmiyor|
|[C28238](/cpp/code-quality/c28238)|Parametresindeki ek açıklamanın birden fazla değeri, stringValue ve longValue 'ı vardır. Paramn = xxx kullanın|
|[C28239](/cpp/code-quality/c28239)|Parametresindeki ek açıklamanın değeri, stringValue veya longValue; ve Paramn = xxx. Yalnızca paramn = xxx kullanın|
|[C28240](/cpp/code-quality/c28240)|Parametresindeki ek açıklamanın param2 vardır ancak Param1 yok|
|[C28241](/cpp/code-quality/c28241)|Parametre üzerindeki işlev için ek açıklama tanınmıyor|
|[C28243](/cpp/code-quality/c28243)|Parametresindeki işlev için ek açıklama, ek açıklama eklenmiş olarak daha fazla başvuru gerektiriyor|
|[C28245](/cpp/code-quality/c28245)|İşlev açıklamasına yönelik ek açıklama ' this ' öğesini üye olmayan bir işlev üzerinde Tates|
|[C28246](/cpp/code-quality/c28246)|İşlevin parametre ek açıklaması, parametrenin türü ile eşleşmiyor|
|[C28250](/cpp/code-quality/c28250)|İşlev için tutarsız ek açıklama: önceki örnekte hata var.|
|[C28251](/cpp/code-quality/c28251)|İşlev için tutarsız ek açıklama: Bu örnekte hata var.|
|[C28252](/cpp/code-quality/c28252)|İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.|
|[C28253](/cpp/code-quality/c28253)|İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<> () ek açıklamalarda desteklenmez|
|[C28262](/cpp/code-quality/c28262)|Ek açıklama için işlevde bir sözdizimi hatası bulundu|
|[C28263](/cpp/code-quality/c28263)|Iç ek açıklamanın koşullu ek açıklamasında söz dizimi hatası bulundu|
|[C28267](/cpp/code-quality/c28267)|Ek açıklamalarda bir söz dizimi hatası bulundu.|
|[C28272](/cpp/code-quality/c28272)|İşlevi için ek açıklama, incelenirken parametresi, işlev bildirimiyle tutarsız|
|[C28273](/cpp/code-quality/c28273)|İşlev için, ipuçları işlev bildirimiyle tutarsız|
|[C28275](/cpp/code-quality/c28275)|\_Makro \_ değeri parametresi \_ null|
|[C28279](/cpp/code-quality/c28279)|Sembol için, eşleşen bir ' End ' olmadan bir ' begin' bulundu|
|[C28280](/cpp/code-quality/c28280)|Sembol için, eşleşen bir ' begin' olmadan bir ' End ' bulundu|
|[C28282](/cpp/code-quality/c28282)|Biçim dizeleri ön koşullarda olmalıdır|
|[C28285](/cpp/code-quality/c28285)|İşlev için, parametrede söz dizimi hatası|
|[C28286](/cpp/code-quality/c28286)|İşlev için, sonda yakınında sözdizimi hatası|
|[C28287](/cpp/code-quality/c28287)|İşlev için, \_ at \_ () ek açıklamasında söz dizimi hatası (Tanınmayan parametre adı)|
|[C28288](/cpp/code-quality/c28288)|İşlev için, \_ at \_ () ek açıklamasında söz dizimi hatası (geçersiz parametre adı)|
|[C28289](/cpp/code-quality/c28289)|İşlev için: ReadableTo veya WritableTo parametre olarak bir limit-spec içermiyordu|
|[C28290](/cpp/code-quality/c28290)|işlev için ek açıklama, gerçek parametre sayısından daha fazla dışlar içeriyor|
|[C28291](/cpp/code-quality/c28291)|deref düzey 0 ' da null/NotNull Post işlevi için anlamsız bir küçüktür.|
|[C28300](/cpp/code-quality/c28300)|İşleç için uyumsuz türlerin ifade işlenenleri|
|[C28301](/cpp/code-quality/c28301)|İşlevin ilk bildirimi için ek açıklama yok.|
|[C28302](/cpp/code-quality/c28302)|\_Ek açıklamada ek bir deref \_ işleci bulundu.|
|[C28303](/cpp/code-quality/c28303)|\_Ek açıklamada belirsiz bir deref \_ işleci bulundu.|
|[C28304](/cpp/code-quality/c28304)|Belirtece hatalı yerleştirilmiş \_ Notref \_ işleci bulundu.|
|[C28305](/cpp/code-quality/c28305)|Belirteç ayrıştırılırken bir hata bulundu.|
|[C28350](/cpp/code-quality/c28350)|Ek açıklama koşullu olarak uygulanabilir olmayan bir durum tanımlar.|
|[C28351](/cpp/code-quality/c28351)|Ek açıklama, koşulda bir dinamik değerin (bir değişken) kullanılamayacağını açıklar.|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Boş sonlandırıcıları kaldırın|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Atılabilen alanlar atılmalıdır|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|