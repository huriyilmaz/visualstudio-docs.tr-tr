---
title: Yerel Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
description: Visual Studio Önerilen Kurallar kural kümesi hakkında bilgi öğrenin. Yerel kodda güvenlik, sağlamlık ve diğer kritik sorunlar için kuralların açıklamalarına bakın.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: f9af762c5ba47139419415afd97309a40071d5945db1731baaa77dd2632491c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363215"
---
# <a name="native-recommended-rules-rule-set"></a>Yerel Önerilen Kurallar kural kümesi

Yerel Önerilen Kurallar, yerel kodda olası güvenlik açıkları ve uygulama kilitlenmeleri gibi en kritik ve yaygın sorunlara odaklanır. Bu kural kümesi, Yerel Minimum Kurallar kural [kümesinde yer alan tüm kuralları](native-minimum-rules-rule-set.md) içerir.

Bu kural kümesi, yerel projeler için oluşturmak istediğiniz özel kural kümelerini içerir.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uninitialized Memory kullanma|
|[C6011](/cpp/code-quality/c6011)|Null İşaretçiyi Başvurudan Çıkararak|
|[C6029](/cpp/code-quality/c6029)|Denetlenmeyen değerin kullanımı|
|[C6031](/cpp/code-quality/c6031)|Dönüş Değeri Yoksayıldı|
|[C6053](/cpp/code-quality/c6053)|Çağrıdan Sıfır Sonlandırma|
|[C6054](/cpp/code-quality/c6054)|Sıfır Sonlandırma Eksik|
|[C6059](/cpp/code-quality/c6059)|Hatalı Concatenation|
|[C6063](/cpp/code-quality/c6063)|İşlevi Biçimlendirmek için Eksik Dize Bağımsız Değişkeni|
|[C6064](/cpp/code-quality/c6064)|İşlevi Biçimlendirmek için Tamsayı Bağımsız Değişkeni Eksik|
|[C6066](/cpp/code-quality/c6066)|İşlevi Biçimlendirmek için İşaretçi Bağımsız Değişkeni Eksik|
|[C6067](/cpp/code-quality/c6067)|İşlevi Biçimlendirmek için Dize İşaretçisi Bağımsız Değişkeni Eksik|
|[C6101](/cpp/code-quality/c6101)|Uninitialized memory döndüren|
|[C6200](/cpp/code-quality/c6200)|Dizin Arabellek Üst Sınırını Aşıyor|
|[C6201](/cpp/code-quality/c6201)|Dizin Yığın Arabelleği Üst Sınırını Aşıyor|
|[C6214](/cpp/code-quality/c6214)|GEÇERSIZ HRESULT'un BOOL'a atfı|
|[C6215](/cpp/code-quality/c6215)|Geçersiz BOOL'den HRESULT'a|
|[C6216](/cpp/code-quality/c6216)|GEÇERSIZ Compiler-Inserted BOOL'u HRESULT'a attırma|
|[C6217](/cpp/code-quality/c6217)|NOT ile geçersiz HRESULT testi|
|[C6220](/cpp/code-quality/c6220)|Geçersiz HRESULT ile -1 karşılaştırması|
|[C6226](/cpp/code-quality/c6226)|-1'e geçersiz HRESULT ataması|
|[C6230](/cpp/code-quality/c6230)|Geçersiz HRESULT Boole Olarak Kullanma|
|[C6235](/cpp/code-quality/c6235)|Logical-Or ile Sıfır Olmayan Sabit|
|[C6236](/cpp/code-quality/c6236)|Logical-Or Olmayan Sabitle|
|[C6237](/cpp/code-quality/c6237)|Sıfır ve Logical-And Yan Etkileri Kaybeder|
|[C6242](/cpp/code-quality/c6242)|Yerel Geriye Doğru Zorlamalı|
|[C6248](/cpp/code-quality/c6248)|Null DACL oluşturma|
|[C6250](/cpp/code-quality/c6250)|Tanınmayan Adres Tanımlayıcıları|
|[C6255](/cpp/code-quality/c6255)|Alloca Korumasız Kullanımı|
|[C6258](/cpp/code-quality/c6258)|İş Parçacığını Sonlandırmayı Kullanma|
|[C6259](/cpp/code-quality/c6259)|Sınırlı Anahtarda Bitwise-Or Kod|
|[C6260](/cpp/code-quality/c6260)|Byte Aritmetik Kullanımı|
|[C6262](/cpp/code-quality/c6262)|Aşırı Yığın Kullanımı|
|[C6263](/cpp/code-quality/c6263)|Alloca In Loop Kullanma|
|[C6268](/cpp/code-quality/c6268)|Dökümde Eksik Parantezler|
|[C6269](/cpp/code-quality/c6269)|İşaretçi Başvuru yok sayılır|
|[C6270](/cpp/code-quality/c6270)|İşlevi Biçimlendirmek için Kayan Bağımsız Değişken Eksik|
|[C6271](/cpp/code-quality/c6271)|İşlevi Biçimlendirmek için Ek Bağımsız Değişken|
|[C6272](/cpp/code-quality/c6272)|İşlevi Biçimlendirmek için Float Olmayan Bağımsız Değişken|
|[C6273](/cpp/code-quality/c6273)|İşlevi Biçimlendirmek için Tamsayı Olmayan Bağımsız Değişken|
|[C6274](/cpp/code-quality/c6274)|İşlevi Biçimlendirmek için Karakter Olmayan Bağımsız Değişken|
|[C6276](/cpp/code-quality/c6276)|Geçersiz Dize Yayma|
|[C6277](/cpp/code-quality/c6277)|Geçersiz CreateProcess Çağrısı|
|[C6278](/cpp/code-quality/c6278)|Array-New Scalar-Delete Eşleşmesi|
|[C6279](/cpp/code-quality/c6279)|Scalar-New Array-Delete Eşleşmesi|
|[C6280](/cpp/code-quality/c6280)|Bellek Allocation-Deallocation Eşleşmesi|
|[C6281](/cpp/code-quality/c6281)|BitSel İlişki Önceliği|
|[C6282](/cpp/code-quality/c6282)|Atama Testin Yerini Aldı|
|[C6283](/cpp/code-quality/c6283)|İlkel Array-New Scalar-Delete Eşleşmesi|
|[C6284](/cpp/code-quality/c6284)|İşlevi Biçimlendirmek için Geçersiz Nesne Bağımsız Değişkeni|
|[C6285](/cpp/code-quality/c6285)|Logical-Or Sabitleri|
|[C6286](/cpp/code-quality/c6286)|Sıfır Olmayan Logical-Or Etkileri Kaybetme|
|[C6287](/cpp/code-quality/c6287)|Yedekli Test|
|[C6288](/cpp/code-quality/c6288)|Logical-And Karşılıklı Dahil Etme Yanlış|
|[C6289](/cpp/code-quality/c6289)|Logical-Or Karşılıklı Dışlama Doğru|
|[C6290](/cpp/code-quality/c6290)|Logical-Not Bitwise-And Önceliği|
|[C6291](/cpp/code-quality/c6291)|Logical-Not Bitwise-Or Önceliği|
|[C6292](/cpp/code-quality/c6292)|Döngü Sayısı En FazlaDan Yukarı|
|[C6293](/cpp/code-quality/c6293)|Döngü Sayısı En DüşükTen Aşağı|
|[C6294](/cpp/code-quality/c6294)|Döngü Gövdesi Hiçbir Zaman Yürütülmz|
|[C6295](/cpp/code-quality/c6295)|Sonsuz Döngü|
|[C6296](/cpp/code-quality/c6296)|Yalnızca Bir Kez Yürütülen Döngü|
|[C6297](/cpp/code-quality/c6297)|Kaydırmanın daha büyük boyuta geçiş sonucu|
|[C6299](/cpp/code-quality/c6299)|Bitfield'den Boole'a Karşılaştırma|
|[C6302](/cpp/code-quality/c6302)|İşlevi Biçimlendirmek için Geçersiz Karakter Dizesi Bağımsız Değişkeni|
|[C6303](/cpp/code-quality/c6303)|İşlevi Biçimlendirmek için Geçersiz Geniş Karakter Dizesi Bağımsız Değişkeni|
|[C6305](/cpp/code-quality/c6305)|Eşleşmeyen Boyut ve Sayı Kullanımı|
|[C6306](/cpp/code-quality/c6306)|Yanlış Değişken Bağımsız Değişken İşlev Çağrısı|
|[C6308](/cpp/code-quality/c6308)|Realloc Sızıntısı|
|[C6310](/cpp/code-quality/c6310)|Geçersiz Özel Durum Filtresi Sabiti|
|[C6312](/cpp/code-quality/c6312)|Özel Durum Devam Yürütme Döngüsü|
|[C6314](/cpp/code-quality/c6314)|Bitwise-Or Önceliği|
|[C6317](/cpp/code-quality/c6317)|Tamamlayıcı Değil|
|[C6318](/cpp/code-quality/c6318)|Özel Durum Devam Arama|
|[C6319](/cpp/code-quality/c6319)|Virgülle Yoksayıldı|
|[C6324](/cpp/code-quality/c6324)|Dize Karşılaştırması Yerine Dize Kopyalama|
|[C6328](/cpp/code-quality/c6328)|Olası Bağımsız Değişken Türü Eşleşmemesi|
|[C6331](/cpp/code-quality/c6331)|VirtualFree Geçersiz Bayraklar|
|[C6332](/cpp/code-quality/c6332)|VirtualFree Geçersiz Parametresi|
|[C6333](/cpp/code-quality/c6333)|VirtualFree Geçersiz Boyut|
|[C6335](/cpp/code-quality/c6335)|İşlem Tanıtıcısı Sızdırıyor|
|[C6381](/cpp/code-quality/c6381)|Kapatma Bilgileri Eksik|
|[C6383](/cpp/code-quality/c6383)|Element-Count Byte-Count Arabellek Taşması|
|[C6384](/cpp/code-quality/c6384)|İşaretçi Boyutu Bölümü|
|[C6385](/cpp/code-quality/c6385)|Fazla Çalıştırmayı Okuma|
|[C6386](/cpp/code-quality/c6386)|Yazma Taşması|
|[C6387](/cpp/code-quality/c6387)|Geçersiz Parametre Değeri|
|[C6388](/cpp/code-quality/c6388)|Geçersiz Parametre Değeri|
|[C6500](/cpp/code-quality/c6500)|Geçersiz Öznitelik Özelliği|
|[C6501](/cpp/code-quality/c6501)|Çakışan Öznitelik Özellik Değerleri|
|[C6503](/cpp/code-quality/c6503)|Başvurular Null Olamaz|
|[C6504](/cpp/code-quality/c6504)|İşaretçi OlmayanLarda Null|
|[C6505](/cpp/code-quality/c6505)|MustCheck On Void|
|[C6506](/cpp/code-quality/c6506)|İşaretçi olmayan veya dizide arabellek boyutu|
|[C6508](/cpp/code-quality/c6508)|Sabitte Yazma Erişimi|
|[C6509](/cpp/code-quality/c6509)|Önkoşulda Kullanılan Dönüş|
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
|[C6995](/cpp/code-quality/c6995)|XML günlük dosyası kaydedilemedi|
|[C26100](/cpp/code-quality/c26100)|Yarış durumu|
|[C26101](/cpp/code-quality/c26101)|Kenetlenmiş işlem düzgün şekilde kullanılamıyor|
|[C26110](/cpp/code-quality/c26110)|Çağıran kilidi tutamıyor|
|[C26111](/cpp/code-quality/c26111)|Çağıran kilidi serbest bırakamıyor|
|[C26112](/cpp/code-quality/c26112)|Çağıran herhangi bir kilit tutamaz|
|[C26115](/cpp/code-quality/c26115)|Kilit bırakılamıyor|
|[C26116](/cpp/code-quality/c26116)|Kilit alınamıyor veya beklet|
|[C26117](/cpp/code-quality/c26117)|Tutulmayan kilit bırakılıyor|
|[C26140](/cpp/code-quality/c26140)|Eşzamanlılık SAL ek açıklaması hatası|
|[C26441](/cpp/code-quality/C26441)|NO_UNNAMED_GUARDS|
|[C26444](/cpp/code-quality/c26444)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](/cpp/code-quality/C26498)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](/cpp/code-quality/c28020)|İfade bu çağrıda doğru değil|
|[C28021](/cpp/code-quality/c28021)|Açıklama eklenen parametrenin bir işaretçi olması gerekir|
|[C28022](/cpp/code-quality/c28022)|Bu işlevdeki işlev sınıfı (es), kendisini tanımlamak için kullanılan typedef üzerindeki işlev sınıfları ile eşleşmiyor.|
|[C28023](/cpp/code-quality/c28023)|Atanan veya geçirilen işlev, \_ \_ \_ en az bir sınıf (es) için bir işlev sınıfı ek açıklamasına sahip olmalıdır|
|[C28024](/cpp/code-quality/c28024)|Atanmakta olan işlev işaretçisine işlev sınıfı (es) listesinde bulunmayan işlev sınıfıyla açıklama eklenir.|
|[C28039](/cpp/code-quality/c28039)|Gerçek parametre türü, türle tam olarak eşleşmelidir|
|[C28112](/cpp/code-quality/c28112)|Birbirine kenetlenmiş bir işlev aracılığıyla erişilen bir değişkene, her zaman birbirine kenetlenmiş bir işlev aracılığıyla erişilmesi gerekir.|
|[C28113](/cpp/code-quality/c28113)|Birbirine kenetlenmiş bir işlev aracılığıyla yerel bir değişkene erişme|
|[C28125](/cpp/code-quality/c28125)|İşlev bir try/except bloğu içinden çağrılmalıdır|
|[C28137](/cpp/code-quality/c28137)|Değişken bağımsız değişkeni bunun yerine bir (sabit değer) sabit olmalıdır|
|[C28138](/cpp/code-quality/c28138)|Sabit bağımsız değişken bunun yerine değişken olmalıdır|
|[C28159](/cpp/code-quality/c28159)|Bunun yerine başka bir işlev kullanmayı düşünün.|
|[C28160](/cpp/code-quality/c28160)|Hata ek açıklaması|
|[C28163](/cpp/code-quality/c28163)|İşlev bir try/except bloğunun içinden asla çağrılmamalıdır|
|[C28164](/cpp/code-quality/c28164)|Bağımsız değişken bir nesneye işaretçi bekleyen bir işleve geçiriliyor (bir işaretçiye işaretçi değil)|
|[C28182](/cpp/code-quality/c28182)|NULL işaretçiyle başvuruluyor. İşaretçi, başka bir işaretçi ile aynı NULL değeri içeriyor.|
|[C28183](/cpp/code-quality/c28183)|bağımsız değişkeni bir değer olabilir ve işaretçide bulunan değerin bir kopyasıdır|
|[C28193](/cpp/code-quality/c28193)|değişkeni, incelenmesi gereken bir değeri tutar|
|[C28196](/cpp/code-quality/c28196)|Gereksinim karşılanmaz. (İfade true olarak değerlendirilmez.)|
|[C28202](/cpp/code-quality/c28202)|Statik olmayan üyeye geçersiz başvuru|
|[C28203](/cpp/code-quality/c28203)|Sınıf üyesine belirsiz başvuru.|
|[C28205](/cpp/code-quality/c28205)|\_Geçersiz \_ bağlamda kullanılan Başarılı veya \_ \_ \_ Başarısız|
|[C28206](/cpp/code-quality/c28206)|Sol işlenen bir yapıya yöneliktir, '->' kullanın|
|[C28207](/cpp/code-quality/c28207)|Sol işlenen bir yapıdır, '.' kullanın.|
|[C28209](/cpp/code-quality/c28209)|Sembolün bildirimi çakışan bir bildirime sahip|
|[C28210](/cpp/code-quality/c28210)|Uygulama bağlamının __on_failure açık ön bağlamda yer almaması gerekir|
|[C28211](/cpp/code-quality/c28211)|SAL_context için statik bağlam adı bekleniyor|
|[C28212](/cpp/code-quality/c28212)|Ek açıklama için işaretçi ifadesi bekleniyor|
|[C28213](/cpp/code-quality/c28213)|Decl \_ \_ ek \_ açıklamalarını kullan ek \_ açıklaması, değişiklik yapmadan, önceki bir bildirime başvuru yapmak için kullanılmalıdır.|
|[C28214](/cpp/code-quality/c28214)|Öznitelik parametre adları p1... p9|
|[C28215](/cpp/code-quality/c28215)|Typefix zaten typefix olan bir parametreye uygulanamaz|
|[C28216](/cpp/code-quality/c28216)|checkReturn ek açıklaması yalnızca belirli işlev parametresinin sonkoşulları için geçerlidir.|
|[C28217](/cpp/code-quality/c28217)|İşlev için, ek açıklamaya eklenecek parametre sayısı dosyada bulunanla eşle değil|
|[C28218](/cpp/code-quality/c28218)|İşlev parametresi için, ek açıklamanın parametresi dosyasında bulunanla eşle değil|
|[C28219](/cpp/code-quality/c28219)|Ek açıklama içinde parametresinin ek açıklaması için beklenen numaralama üyesi|
|[C28220](/cpp/code-quality/c28220)|Ek açıklama içinde parametresinin ek açıklaması için tamsayı ifadesi bekleniyor|
|[C28221](/cpp/code-quality/c28221)|Ek açıklamada parametresi için dize ifadesi bekleniyor|
|[C28222](/cpp/code-quality/c28222)|__yes, _no \_ veya _maybe için \_ beklenen ek açıklamalar|
|[C28223](/cpp/code-quality/c28223)|Ek açıklama, parametre için beklenen Belirteç/tanımlayıcı bulamıyorum|
|[C28224](/cpp/code-quality/c28224)|Ek açıklama için parametreler gerekir|
|[C28225](/cpp/code-quality/c28225)|Ek açıklamada doğru sayıda gerekli parametre bulamıyorum|
|[C28226](/cpp/code-quality/c28226)|Ek açıklama aynı zamanda bir PrimOp olamaz (geçerli bildirimde)|
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
|[C28239](/cpp/code-quality/c28239)|parametredeki ek açıklamanın hem değeri, stringValue hem de longValue değeri vardır; and paramn=xxx. Yalnızca paramn=xxx kullanın|
|[C28240](/cpp/code-quality/c28240)|parametresinde ek açıklama param2'ye sahip ancak param1 yok|
|[C28241](/cpp/code-quality/c28241)|parametresinde işlevin ek açıklaması tanınmıyor|
|[C28243](/cpp/code-quality/c28243)|parametresinde işlevin ek açıklaması, açıklama ek açıklamasının izin veren gerçek türe göre daha fazla başvuru gerektirir|
|[C28244](/cpp/code-quality/c28244)|İşlevin ek açıklaması, ayrılamaz bir parametreye/dış ek açıklamaya sahiptir|
|[C28245](/cpp/code-quality/c28245)|İşlevin ek açıklaması, üye olmayan bir işlevde 'this' ek açıklamasını verir|
|[C28246](/cpp/code-quality/c28246)|İşlev için parametre ek açıklaması, parametrenin türüyle eşle değil|
|[C28250](/cpp/code-quality/c28250)|İşlev için tutarsız ek açıklama: Önceki örnekte bir hata var.|
|[C28251](/cpp/code-quality/c28251)|İşlev için tutarsız ek açıklama: Bu örnekte bir hata var.|
|[C28252](/cpp/code-quality/c28252)|İşlev için tutarsız ek açıklama: parametresinde bu örnekte başka ek açıklamalar vardır.|
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
|[C28306](/cpp/code-quality/c28306)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28307](/cpp/code-quality/c28307)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28350](/cpp/code-quality/c28350)|Ek açıklama koşullu olarak uygulanabilir olmayan bir durum tanımlar.|
|[C28351](/cpp/code-quality/c28351)|Ek açıklama, koşulda bir dinamik değerin (bir değişken) kullanılamayacağını açıklar.|