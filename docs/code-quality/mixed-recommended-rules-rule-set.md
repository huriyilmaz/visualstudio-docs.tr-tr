---
title: Karışık Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
description: Visual Studio ' de karma Önerilen Kurallar kural kümesi hakkında bilgi edinin. Ortak dil çalışma zamanını destekleyen C++ projeleri için kuralların açıklamalarını inceleyin.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 999c41f50bc1ded593fd529e45acd876665303ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031659"
---
# <a name="mixed-recommended-rules-rule-set"></a>Karışık Önerilen Kurallar kural kümesi

Microsoft Mixed önerilen kurallar, olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere, ortak dil çalışma zamanını destekleyen C++ projelerinizde en yaygın ve kritik sorunlara odaklanmaktadır. Bu kural kümesi, [karışık minimum kurallar](mixed-minimum-rules-rule-set.md) kural kümesindeki tüm kuralları içerir.

Bu kuralı, ortak dil çalışma zamanını destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine ekleyin.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Başlatılmamış belleği kullanma|
|[C6011](/cpp/code-quality/c6011)|Null Işaretçisinin başvurusu|
|[C6029](/cpp/code-quality/c6029)|Işaretlenmemiş değer kullanımı|
|[C6031](/cpp/code-quality/c6031)|Dönüş değeri yoksayıldı|
|[C6053](/cpp/code-quality/c6053)|Çağrıdan sıfır sonlandırma|
|[C6054](/cpp/code-quality/c6054)|Sıfır sonlandırma eksik|
|[C6059](/cpp/code-quality/c6059)|Hatalı birleştirme|
|[C6063](/cpp/code-quality/c6063)|Biçimlendirme Işlevinde dize bağımsız değişkeni eksik|
|[C6064](/cpp/code-quality/c6064)|Biçimlendirme Işlevinde eksik tamsayı bağımsız değişkeni|
|[C6066](/cpp/code-quality/c6066)|Biçimlendirme Işlevinde eksik Işaretçi değişkeni|
|[C6067](/cpp/code-quality/c6067)|Biçimlendirme Işlevinde eksik dize Işaretçisi bağımsız değişkeni|
|[C6101](/cpp/code-quality/c6101)|Başlatılmamış bellek döndürülüyor|
|[C6200](/cpp/code-quality/c6200)|Dizin, arabellek üst sınırını aşıyor|
|[C6201](/cpp/code-quality/c6201)|Dizin yığın arabelleği üst sınırını aşıyor|
|[C6214](/cpp/code-quality/c6214)|HRESULT Ile BOOL arasında geçersiz atama|
|[C6215](/cpp/code-quality/c6215)|Geçersiz tür BOOL olarak HRESULT|
|[C6216](/cpp/code-quality/c6216)|Geçersiz Compiler-Inserted cast BOOL olarak HRESULT|
|[C6217](/cpp/code-quality/c6217)|NOT Ile geçersiz HRESULT testi|
|[C6220](/cpp/code-quality/c6220)|-1 Ile geçersiz HRESULT karşılaştırması|
|[C6226](/cpp/code-quality/c6226)|-1 Için geçersiz HRESULT ataması|
|[C6230](/cpp/code-quality/c6230)|Boole olarak geçersiz HRESULT kullanımı|
|[C6235](/cpp/code-quality/c6235)|Logical-Or Ile sıfır olmayan sabit|
|[C6236](/cpp/code-quality/c6236)|Sıfır olmayan sabit Ile Logical-Or|
|[C6237](/cpp/code-quality/c6237)|Logical-And, yan etkileri kaybediyor|
|[C6242](/cpp/code-quality/c6242)|Yerel geriye doğru Izleme zorlandı|
|[C6248](/cpp/code-quality/c6248)|NULL DACL oluşturuluyor|
|[C6250](/cpp/code-quality/c6250)|Yayımlanverilmemiş adres tanımlayıcıları|
|[C6255](/cpp/code-quality/c6255)|Korumasız alloca kullanımı|
|[C6258](/cpp/code-quality/c6258)|Sonlandırma Iş parçacığını kullanma|
|[C6259](/cpp/code-quality/c6259)|Bitwise-Or sınırlı anahtardaki ölü kod|
|[C6260](/cpp/code-quality/c6260)|Bayt aritmetiği kullanımı|
|[C6262](/cpp/code-quality/c6262)|Aşırı yığın kullanımı|
|[C6263](/cpp/code-quality/c6263)|Döngüde alloca kullanma|
|[C6268](/cpp/code-quality/c6268)|Dönüştürmede parantez eksik|
|[C6269](/cpp/code-quality/c6269)|İşaretçi başvurusu yoksayıldı|
|[C6270](/cpp/code-quality/c6270)|Biçimlendirme Işlevinde float bağımsız değişkeni eksik|
|[C6271](/cpp/code-quality/c6271)|Biçim Işlevine fazladan bağımsız değişken|
|[C6272](/cpp/code-quality/c6272)|Biçimlendirme Işlevinde kayan olmayan bağımsız değişken|
|[C6273](/cpp/code-quality/c6273)|Biçimlendirme Işlevinde tamsayı olmayan bağımsız değişken|
|[C6274](/cpp/code-quality/c6274)|Biçimlendirme Işlevinde karakter olmayan bağımsız değişken|
|[C6276](/cpp/code-quality/c6276)|Geçersiz dize dönüştürme|
|[C6277](/cpp/code-quality/c6277)|Geçersiz CreateProcess çağrısı|
|[C6278](/cpp/code-quality/c6278)|Array-New Scalar-Delete uyumsuzluğu|
|[C6279](/cpp/code-quality/c6279)|Scalar-New Array-Delete uyumsuzluğu|
|[C6280](/cpp/code-quality/c6280)|Bellek Allocation-Deallocation uyumsuzluğu|
|[C6281](/cpp/code-quality/c6281)|Bit düzeyinde Ilişki önceliği|
|[C6282](/cpp/code-quality/c6282)|Atama testin yerini alır|
|[C6283](/cpp/code-quality/c6283)|Temel Array-New Scalar-Delete uyumsuzluğu|
|[C6284](/cpp/code-quality/c6284)|Biçimlendirme Işlevine geçersiz nesne değişkeni|
|[C6285](/cpp/code-quality/c6285)|Sabitler Logical-Or|
|[C6286](/cpp/code-quality/c6286)|Sıfır olmayan Logical-Or yan etkileri kaybetme|
|[C6287](/cpp/code-quality/c6287)|Gereksiz test|
|[C6288](/cpp/code-quality/c6288)|Logical-And üzerinden karşılıklı ekleme false|
|[C6289](/cpp/code-quality/c6289)|Logical-Or üzerinden karşılıklı dışlama doğru|
|[C6290](/cpp/code-quality/c6290)|Logical-Not Bitwise-And önceliği|
|[C6291](/cpp/code-quality/c6291)|Logical-Not Bitwise-Or önceliği|
|[C6292](/cpp/code-quality/c6292)|Döngü en yüksek değerinden yukarı sayılır|
|[C6293](/cpp/code-quality/c6293)|Döngü en küçük değerden aşağı doğru sayılır|
|[C6294](/cpp/code-quality/c6294)|Döngü gövdesi hiç yürütülmedi|
|[C6295](/cpp/code-quality/c6295)|Sonsuz döngü|
|[C6296](/cpp/code-quality/c6296)|Döngü yalnızca bir kez yürütüldü|
|[C6297](/cpp/code-quality/c6297)|SHIFT 'e daha büyük boyuta dönüştürme sonucu|
|[C6299](/cpp/code-quality/c6299)|Bit alanını Boole karşılaştırmaya göre|
|[C6302](/cpp/code-quality/c6302)|Biçimlendirme Işlevine geçersiz karakter dizesi değişkeni|
|[C6303](/cpp/code-quality/c6303)|Biçimlendirme Işlevine geçersiz geniş karakter dizesi değişkeni|
|[C6305](/cpp/code-quality/c6305)|Eşleşmeyen boyut ve sayı kullanımı|
|[C6306](/cpp/code-quality/c6306)|Değişken bağımsız değişken Işlev çağrısı yanlış|
|[C6308](/cpp/code-quality/c6308)|Realloc sızıntısı|
|[C6310](/cpp/code-quality/c6310)|Geçersiz özel durum filtre sabiti|
|[C6312](/cpp/code-quality/c6312)|Özel durum yürütme döngüsüne devam et|
|[C6314](/cpp/code-quality/c6314)|Bitwise-Or önceliği|
|[C6317](/cpp/code-quality/c6317)|Tamamlayıcı değil|
|[C6318](/cpp/code-quality/c6318)|Özel durum aramaya devam et|
|[C6319](/cpp/code-quality/c6319)|Virgülle yoksayıldı|
|[C6324](/cpp/code-quality/c6324)|Dize karşılaştırma yerine dize kopyalama|
|[C6328](/cpp/code-quality/c6328)|Olası bağımsız değişken türü uyumsuzluğu|
|[C6331](/cpp/code-quality/c6331)|VirtualFree geçersiz bayrakları|
|[C6332](/cpp/code-quality/c6332)|VirtualFree geçersiz parametresi|
|[C6333](/cpp/code-quality/c6333)|VirtualFree geçersiz boyutu|
|[C6335](/cpp/code-quality/c6335)|Sızan Işlem tanıtıcısı|
|[C6381](/cpp/code-quality/c6381)|Kapatılmış bilgiler eksik|
|[C6383](/cpp/code-quality/c6383)|Element-Count Byte-Count arabellek taşması|
|[C6384](/cpp/code-quality/c6384)|İşaretçi boyutu bölümü|
|[C6385](/cpp/code-quality/c6385)|Okuma taşması|
|[C6386](/cpp/code-quality/c6386)|Yazma taşması|
|[C6387](/cpp/code-quality/c6387)|Geçersiz parametre değeri|
|[C6388](/cpp/code-quality/c6388)|Geçersiz parametre değeri|
|[C6500](/cpp/code-quality/c6500)|Geçersiz öznitelik özelliği|
|[C6501](/cpp/code-quality/c6501)|Çakışan öznitelik özellik değerleri|
|[C6503](/cpp/code-quality/c6503)|Başvurular null olamaz|
|[C6504](/cpp/code-quality/c6504)|Işaretçi olmayan üzerinde null|
|[C6505](/cpp/code-quality/c6505)|Void üzerinde MustCheck|
|[C6506](/cpp/code-quality/c6506)|Işaretçi olmayan veya dizide arabellek boyutu|
|[C6508](/cpp/code-quality/c6508)|Sabit üzerinde yazma erişimi|
|[C6509](/cpp/code-quality/c6509)|Ön koşul üzerinde kullanılan dönüş|
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
|[C6702](/cpp/code-quality/c6702)|Değer bir dize değeri değil|
|[C6703](/cpp/code-quality/c6703)|Değer bir sayı değil|
|[C6704](/cpp/code-quality/c6704)|Beklenmeyen Ek Açıklama İfadesi Hatası|
|[C6705](/cpp/code-quality/c6705)|Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşlenmiyor|
|[C6706](/cpp/code-quality/c6706)|Ek açıklama için Beklenmeyen Ek Açıklama Hatası|
|[C6995](/cpp/code-quality/c6995)|XML Günlük dosyası kaydedemedi|
|[C26100](/cpp/code-quality/c26100)|Yarış durumu|
|[C26101](/cpp/code-quality/c26101)|Kilitli işlem düzgün bir şekilde kullanılamadı|
|[C26110](/cpp/code-quality/c26110)|Çağıranın kilidi tutamama|
|[C26111](/cpp/code-quality/c26111)|Çağıranın kilidi serbest bırakılamama|
|[C26112](/cpp/code-quality/c26112)|Çağıran hiçbir kilidi tutamaz|
|[C26115](/cpp/code-quality/c26115)|Kilit bırakılamadı|
|[C26116](/cpp/code-quality/c26116)|Kilit alınama veya kilit alınamama|
|[C26117](/cpp/code-quality/c26117)|Yardımsız kilidi serbest bırakma|
|[C26140](/cpp/code-quality/c26140)|Eşzamanlılık SAL ek açıklaması hatası|
|[C28020](/cpp/code-quality/c28020)|İfade bu çağrıda doğru değil|
|[C28021](/cpp/code-quality/c28021)|Açıklama ekli parametre bir işaretçi olmalıdır|
|[C28022](/cpp/code-quality/c28022)|Bu işlevde işlev sınıfı, tanımlamak için kullanılan typedef'in işlev sınıflarını (es) eşleşmez.|
|[C28023](/cpp/code-quality/c28023)|Atanan veya geçirilen işlev, sınıflardan en az biri için bir İşlev \_ \_ sınıfı ek \_ açıklamasına sahip olmalı|
|[C28024](/cpp/code-quality/c28024)|Atanan işlev işaretçisine, işlev sınıfı (es) listesinde yer alan işlev sınıfıyla açıklama eklenir.|
|[C28039](/cpp/code-quality/c28039)|Gerçek parametrenin türü tam olarak türle eşleşmeli|
|[C28112](/cpp/code-quality/c28112)|Kilitli işlev aracılığıyla erişilen bir değişkene her zaman Interlocked işlevi aracılığıyla erişilir.|
|[C28113](/cpp/code-quality/c28113)|Kilitli işlev aracılığıyla yerel değişkene erişme|
|[C28125](/cpp/code-quality/c28125)|işlevi try/except bloğundan çağrılmış olmalı|
|[C28137](/cpp/code-quality/c28137)|Değişken bağımsız değişkeni bunun yerine bir (değişmez değer) sabiti olmalı|
|[C28138](/cpp/code-quality/c28138)|Sabit bağımsız değişken bunun yerine değişken olmalı|
|[C28159](/cpp/code-quality/c28159)|Bunun yerine başka bir işlev kullanmayı düşünün.|
|[C28160](/cpp/code-quality/c28160)|Hata ek açıklaması|
|[C28163](/cpp/code-quality/c28163)|işlevi hiçbir zaman try/except bloğundan çağrılmamalı|
|[C28164](/cpp/code-quality/c28164)|bağımsız değişkeni, bir nesnenin işaretçisini (işaretçi işaretçisi değil) beklediğiniz bir işleve geçirildi|
|[C28182](/cpp/code-quality/c28182)|NULL işaretçisine başvurulma. İşaretçi, başka bir işaretçiyle aynı NULL değeri içerir.|
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
|[C28253](/cpp/code-quality/c28253)|İşlev için tutarsız ek açıklama: parametresinde bu örnekte başka ek açıklamalar vardır.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() ek açıklamalarda desteklenmiyor|
|[C28262](/cpp/code-quality/c28262)|Ek açıklama için işlevde ek açıklamada söz dizimi hatası bulundu|
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
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1009](../code-quality/ca1009.md)|Olay işleyicileri doğru olarak bildirin|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Arabirim metotları alt türler tarafından çağrılabilmelidir|
|[CA1049](../code-quality/ca1049.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|P/Invokes'u NativeMethods sınıfına taşıyın|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Temel sınıf metotlarını gizlemeyin|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|IDisposable'ı doğru uygulayın|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Beklenmeyen konumlarda özel durum harekete geçirmeyin|
|[CA1301](../code-quality/ca1301.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403.md)|Otomatik yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404.md)|P/Invoke ardından hemen GetLastError çağırın|
|[CA1405](../code-quality/ca1405.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410.md)|COM kayıt metotları eşleşmelidir|
|[CA1415](../code-quality/ca1415.md)|P/Invoke'ları doğru bildirin|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Boş sonlandırıcıları kaldırın|
|[CA1900](../code-quality/ca1900.md)|Değer tür alanları taşınabilir olmalıdır|
|[CA1901](../code-quality/ca1901.md)|P/Invoke bildirimleri taşınabilir olmalıdır|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Zayıf kimliği olan nesneleri kilitlemeyin|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|SQL sorgularını güvenlik açıkları için inceleyin|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
|[CA2108](../code-quality/ca2108.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|
|[CA2111](../code-quality/ca2111.md)|İşaretçiler görünür olmamalıdır|
|[CA2112](../code-quality/ca2112.md)|Güvenli türler alanları açığa çıkarmamalıdır|
|[CA2114](../code-quality/ca2114.md)|Metot güvenliği türün bir üst kümesi olmalıdır|
|[CA2116](../code-quality/ca2116.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
|[CA2117](../code-quality/ca2117.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|
|[CA2122](../code-quality/ca2122.md)|Bağlantı talepleri olan metotları dolaylı olarak açığa çıkarmayın|
|[CA2123](../code-quality/ca2123.md)|Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır|
|[CA2124](../code-quality/ca2124.md)|Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın|
|[CA2126](../code-quality/ca2126.md)|Tür bağlantı talepleri kalıtım taleplerini gerektirir|
|[CA2131](../code-quality/ca2131.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|
|[CA2132](../code-quality/ca2132.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|
|[CA2133](../code-quality/ca2133.md)|Temsilciler tutarlı saydamlığı olan metotlara bağlanmalıdır|
|[CA2134](../code-quality/ca2134.md)|Metotlar taban metotları geçersiz kılarken tutarlı saydamlığı tutmalıdır|
|[CA2137](../code-quality/ca2137.md)|Saydam metotlar yalnızca doğrulanabilir IL içermelidir|
|[CA2138](../code-quality/ca2138.md)|Saydam metotlar SuppressUnmanagedCodeSecurity özniteliğine sahip metotları çağırmamalıdır|
|[CA2140](../code-quality/ca2140.md)|Saydam kod güvenlik kritik nesnelerine başvurmamalıdır|
|[CA2141](../code-quality/ca2141.md)|Saydam yöntemler LinkDemands'i karşılamamalı|
|[CA2146](../code-quality/ca2146.md)|Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147.md)|Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır|
|[CA2149](../code-quality/ca2149.md)|Saydam metotlar yerel kod içine çağırmamalıdır|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Yığın ayrıntılarını korumak için yeniden fırlatın|
|[CA2202](../code-quality/ca2202.md)|Nesneleri birden çok kez atmayın|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Değer türü statik alanları satır içi başlatın|
|[CA2212](../code-quality/ca2212.md)|Servis verilen bileşenleri WebMethod ile işaretlemeyin|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Atılabilen alanlar atılmalıdır|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Atılabilir türler sonlandırıcıyı bildirmelidir|
|[CA2220](../code-quality/ca2220.md)|Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Serileştirme oluşturucularını uygulayın|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|
|[CA2232](../code-quality/ca2232.md)|Windows Forms giriş noktalarını STAThread ile işaretleyin|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Tüm serileştirilebilir olmayan alanları işaretleyin|
|[CA2236](../code-quality/ca2236.md)|ISerializable türler üzerinde taban sınıf metotlarını çağırın|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|ISerializable türleri SerializableAttribute ile işaretleyin|
|[CA2238](../code-quality/ca2238.md)|Serileştirme metotlarını doğru uygulayın|
|[CA2240](../code-quality/ca2240.md)|ISerializable'ı doğru uygulayın|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|NaN için doğru test edin|