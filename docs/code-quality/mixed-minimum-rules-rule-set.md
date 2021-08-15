---
title: Karışık Minimum Kurallar kural kümesi
ms.date: 11/04/2016
description: Visual Studio'da Karma Minimum Kurallar kural kümesi hakkında Visual Studio. Ortak Dil Çalışma Zamanı'nın destekçisi C++ projeleri için kuralların açıklamalarını görme.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 16bfe7655eec38e2f5630950b10034f6d4d7a42b71744493f0ff9cd12a936310
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240724"
---
# <a name="mixed-minimum-rules-rule-set"></a>Karışık Minimum Kurallar kural kümesi

Microsoft Karma Minimum Kuralları, olası güvenlik açıkları ve uygulama kilitlenmeleri de dahil olmak üzere Ortak Dil Çalışma Zamanı'nın destekçisi olan C++ projelerinde en kritik sorunlara odaklanır.

Bu kural kümesi, Ortak Dil Çalışma Zamanı'nın destekçisi olan C++ projeleriniz için oluşturdukları herhangi bir özel kural kümesine dahil edin.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uninitialized Memory kullanma|
|[C6011](/cpp/code-quality/c6011)|Null İşaretçiyi Başvurudan Çıkararak|
|[C6029](/cpp/code-quality/c6029)|Denetlenmeyen değerin kullanımı|
|[C6053](/cpp/code-quality/c6053)|Çağrıdan Sıfır Sonlandırma|
|[C6059](/cpp/code-quality/c6059)|Hatalı Concatenation|
|[C6063](/cpp/code-quality/c6063)|İşlevi Biçimlendirmek için Eksik Dize Bağımsız Değişkeni|
|[C6064](/cpp/code-quality/c6064)|İşlevi Biçimlendirmek için Tamsayı Bağımsız Değişkeni Eksik|
|[C6066](/cpp/code-quality/c6066)|İşlevi Biçimlendirmek için İşaretçi Bağımsız Değişkeni Eksik|
|[C6067](/cpp/code-quality/c6067)|İşlevi Biçimlendirmek için Dize İşaretçisi Bağımsız Değişkeni Eksik|
|[C6101](/cpp/code-quality/c6101)|Uninitialized memory döndüren|
|[C6200](/cpp/code-quality/c6200)|Dizin Arabellek Üst Sınırını Aşıyor|
|[C6201](/cpp/code-quality/c6201)|Dizin Yığın Arabelleği Üst Sınırını Aşıyor|
|[C6270](/cpp/code-quality/c6270)|İşlevi Biçimlendirmek için Kayan Bağımsız Değişken Eksik|
|[C6271](/cpp/code-quality/c6271)|İşlevi Biçimlendirmek için Ek Bağımsız Değişken|
|[C6272](/cpp/code-quality/c6272)|İşlevi Biçimlendirmek için Float Olmayan Bağımsız Değişken|
|[C6273](/cpp/code-quality/c6273)|İşlevi Biçimlendirmek için Tamsayı Olmayan Bağımsız Değişken|
|[C6274](/cpp/code-quality/c6274)|İşlevi Biçimlendirmek için Karakter Olmayan Bağımsız Değişken|
|[C6276](/cpp/code-quality/c6276)|Geçersiz Dize Yayma|
|[C6277](/cpp/code-quality/c6277)|Geçersiz CreateProcess Çağrısı|
|[C6284](/cpp/code-quality/c6284)|İşlevi Biçimlendirmek için Geçersiz Nesne Bağımsız Değişkeni|
|[C6290](/cpp/code-quality/c6290)|Logical-Not Bitwise-And Önceliği|
|[C6291](/cpp/code-quality/c6291)|Logical-Not Bitwise-Or Önceliği|
|[C6302](/cpp/code-quality/c6302)|İşlevi Biçimlendirmek için Geçersiz Karakter Dizesi Bağımsız Değişkeni|
|[C6303](/cpp/code-quality/c6303)|İşlevi Biçimlendirmek için Geçersiz Geniş Karakter Dizesi Bağımsız Değişkeni|
|[C6305](/cpp/code-quality/c6305)|Eşleşmeyen Boyut ve Sayı Kullanımı|
|[C6306](/cpp/code-quality/c6306)|Yanlış Değişken Bağımsız Değişken İşlev Çağrısı|
|[C6328](/cpp/code-quality/c6328)|Olası Bağımsız Değişken Türü Eşleşmemesi|
|[C6385](/cpp/code-quality/c6385)|Fazla Çalıştırmayı Okuma|
|[C6386](/cpp/code-quality/c6386)|Yazma Taşması|
|[C6387](/cpp/code-quality/c6387)|Geçersiz Parametre Değeri|
|[C6500](/cpp/code-quality/c6500)|Geçersiz Öznitelik Özelliği|
|[C6501](/cpp/code-quality/c6501)|Çakışan Öznitelik Özellik Değerleri|
|[C6503](/cpp/code-quality/c6503)|Başvurular Null Olamaz|
|[C6504](/cpp/code-quality/c6504)|İşaretçi OlmayanLarda Null|
|[C6505](/cpp/code-quality/c6505)|MustCheck On Void|
|[C6506](/cpp/code-quality/c6506)|İşaretçi olmayan veya dizide arabellek boyutu|
|[C6508](/cpp/code-quality/c6508)|Sabitte Yazma Erişimi|
|[C6509](/cpp/code-quality/c6509)|Önkoşulda Kullanılan Dönüş|
|[C6510](/cpp/code-quality/c6510)|İşaretçi OlmayanDa Null Sonlandırıldı|
|[C6511](/cpp/code-quality/c6511)|MustCheck Evet veya Hayır olmalı|
|[C6513](/cpp/code-quality/c6513)|Arabellek Boyutu Olmadan Öğe Boyutu|
|[C6514](/cpp/code-quality/c6514)|Arabellek Boyutu Dizi Boyutunu Aşıyor|
|[C6515](/cpp/code-quality/c6515)|İşaretçi olmayanlarda arabellek boyutu|
|[C6516](/cpp/code-quality/c6516)|Öznitelikte Özellik Yok|
|[C6517](/cpp/code-quality/c6517)|Okunamaz arabellekte geçerli boyut|
|[C6518](/cpp/code-quality/c6518)|Yazılamaz Arabellekte Yazılabilir Boyut|
|[C6522](/cpp/code-quality/c6522)|Geçersiz Boyut Dize Türü|
|[C6525](/cpp/code-quality/c6525)|Geçersiz Boyut DizesiNe Erişilemez Konumu|
|[C6527](/cpp/code-quality/c6527)|Geçersiz ek açıklama: Geçersiz türdeki değerlerde 'NeedsRelease' özelliği kullanılamaz|
|[C6530](/cpp/code-quality/c6530)|Tanınmayan Biçim Dizesi Stili|
|[C6540](/cpp/code-quality/c6540)|Bu işlevde öznitelik ek açıklamalarının kullanımı, mevcut ek açıklamalarının __declspec geçersiz kılınacak|
|[C6551](/cpp/code-quality/c6551)|Geçersiz boyut belirtimi: ifade ayrıştırılamaz|
|[C6552](/cpp/code-quality/c6552)|Geçersiz Deref= veya Notref=: ifade ayrıştırılamaz|
|[C6701](/cpp/code-quality/c6701)|Değer geçerli bir Evet/Hayır/Belki değeri değil|
|[C6702](/cpp/code-quality/c6702)|Değer bir dize değeri değildir|
|[C6703](/cpp/code-quality/c6703)|Değer bir sayı değil|
|[C6704](/cpp/code-quality/c6704)|Beklenmeyen Ek Açıklama İfadesi Hatası|
|[C6705](/cpp/code-quality/c6705)|Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşlenmiyor|
|[C6706](/cpp/code-quality/c6706)|Ek açıklama için Beklenmeyen Ek Açıklama Hatası|
|[C28021](/cpp/code-quality/c28021)|Açıklama ekli parametre bir işaretçi olmalıdır|
|[C28182](/cpp/code-quality/c28182)|NULL işaretçisine başvurulma. İşaretçi, başka bir işaretçiyle aynı NULL değeri içerir.|
|[C28202](/cpp/code-quality/c28202)|Statik olmayan üyeye geçersiz başvuru|
|[C28203](/cpp/code-quality/c28203)|Sınıf üyesine belirsiz başvuru.|
|[C28205](/cpp/code-quality/c28205)|\_Geçersiz \_ bağlamda kullanılan Başarılı veya \_ \_ \_ Başarısız|
|[C28206](/cpp/code-quality/c28206)|Sol işlenen bir yapıya yöneliktir, '->' kullanın|
|[C28207](/cpp/code-quality/c28207)|Sol işlenen bir yapıdır, '.' kullanın.|
|[C28210](/cpp/code-quality/c28210)|Uygulama bağlamının __on_failure açık ön bağlamda yer almaması gerekir|
|[C28211](/cpp/code-quality/c28211)|SAL_context için statik bağlam adı bekleniyor|
|[C28212](/cpp/code-quality/c28212)|Ek açıklama için işaretçi ifadesi bekleniyor|
|[C28213](/cpp/code-quality/c28213)|Decl \_ \_ ek \_ açıklamalarını kullan ek \_ açıklaması, değişiklik yapmadan, önceki bir bildirime başvuru yapmak için kullanılmalıdır.|
|[C28214](/cpp/code-quality/c28214)|Öznitelik parametre adları p1... p9|
|[C28215](/cpp/code-quality/c28215)|Typefix zaten typefix olan bir parametreye uygulanamaz|
|[C28216](/cpp/code-quality/c28216)|checkReturn ek açıklaması yalnızca belirli işlev parametresinin sonkoşulları için geçerlidir.|
|[C28217](/cpp/code-quality/c28217)|İşlev için, ek açıklamaya eklenecek parametre sayısı dosyada bulunan değerle eşle değil|
|[C28218](/cpp/code-quality/c28218)|İşlev parametresi için, ek açıklamanın parametresi dosyasında bulunanla eşle değil|
|[C28219](/cpp/code-quality/c28219)|Ek açıklama içinde parametresinin ek açıklaması için beklenen numaralama üyesi|
|[C28220](/cpp/code-quality/c28220)|Ek açıklama içinde parametresinin ek açıklaması için tamsayı ifadesi bekleniyor|
|[C28221](/cpp/code-quality/c28221)|Ek açıklamada parametresi için dize ifadesi bekleniyor|
|[C28222](/cpp/code-quality/c28222)|__yes, _no \_ veya _maybe için \_ beklenen ek açıklamalar|
|[C28223](/cpp/code-quality/c28223)|Ek açıklama, parametre için beklenen Belirteç/tanımlayıcı bulamıyorum|
|[C28224](/cpp/code-quality/c28224)|Ek açıklama için parametreler gerekir|
|[C28225](/cpp/code-quality/c28225)|Ek açıklamada doğru sayıda gerekli parametre bulamıyorum|
|[C28226](/cpp/code-quality/c28226)|Ek açıklama aynı zamanda bir PrimOp (geçerli bildirimde) olamaz|
|[C28227](/cpp/code-quality/c28227)|Ek açıklama aynı zamanda bir PrimOp olamaz (önceki bildirime bakın)|
|[C28228](/cpp/code-quality/c28228)|Ek açıklama parametresi: ek açıklamalarda tür kullanılamaz|
|[C28229](/cpp/code-quality/c28229)|Ek açıklama parametreleri desteklemez|
|[C28230](/cpp/code-quality/c28230)|Parametre türünün üyesi yok.|
|[C28231](/cpp/code-quality/c28231)|Ek açıklama yalnızca dizide geçerlidir|
|[C28232](/cpp/code-quality/c28232)|herhangi bir ek açıklamaya pre, post veya deref uygulanmadı|
|[C28233](/cpp/code-quality/c28233)|bir bloğuna uygulanan pre, post veya deref|
|[C28234](/cpp/code-quality/c28234)|__at ifadesi geçerli işlev için geçerli değil|
|[C28235](/cpp/code-quality/c28235)|İşlev ek açıklama olarak tek başına olamaz|
|[C28236](/cpp/code-quality/c28236)|Ek açıklama bir ifadede kullanılamaz|
|[C28237](/cpp/code-quality/c28237)|parametresinde ek açıklama artık desteklenmiyor|
|[C28238](/cpp/code-quality/c28238)|parametresinde ek açıklama birden fazla değer, stringValue ve longValue içerir. paramn=xxx kullanın|
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