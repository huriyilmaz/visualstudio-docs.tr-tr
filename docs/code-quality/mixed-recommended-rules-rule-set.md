---
title: Karışık Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c29e27160b50a53995b7542680256bfd4e2d8f2
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600042"
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
|[C6216](/cpp/code-quality/c6216)|Geçersiz derleyici ile ekli atama BOOL 'A dönüştürüldü|
|[C6217](/cpp/code-quality/c6217)|NOT Ile geçersiz HRESULT testi|
|[C6220](/cpp/code-quality/c6220)|-1 Ile geçersiz HRESULT karşılaştırması|
|[C6226](/cpp/code-quality/c6226)|-1 Için geçersiz HRESULT ataması|
|[C6230](/cpp/code-quality/c6230)|Boole olarak geçersiz HRESULT kullanımı|
|[C6235](/cpp/code-quality/c6235)|Mantıksal or Ile sıfır olmayan sabit|
|[C6236](/cpp/code-quality/c6236)|Sıfır olmayan sabit Ile mantıksal or|
|[C6237](/cpp/code-quality/c6237)|Mantıksal-ve yan etkileri olan sıfır|
|[C6242](/cpp/code-quality/c6242)|Yerel geriye doğru Izleme zorlandı|
|[C6248](/cpp/code-quality/c6248)|NULL DACL oluşturuluyor|
|[C6250](/cpp/code-quality/c6250)|Yayımlanverilmemiş adres tanımlayıcıları|
|[C6255](/cpp/code-quality/c6255)|Korumasız alloca kullanımı|
|[C6258](/cpp/code-quality/c6258)|Sonlandırma Iş parçacığını kullanma|
|[C6259](/cpp/code-quality/c6259)|Bit düzeyinde veya sınırlı anahtarda ölü kod|
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
|[C6278](/cpp/code-quality/c6278)|Dizi-yeni skaler-silme uyumsuzluğu|
|[C6279](/cpp/code-quality/c6279)|Skaler-yeni dizi-silme uyumsuzluğu|
|[C6280](/cpp/code-quality/c6280)|Bellek ayırma-ayırmayı kaldırma uyumsuzluğu|
|[C6281](/cpp/code-quality/c6281)|Bit düzeyinde Ilişki önceliği|
|[C6282](/cpp/code-quality/c6282)|Atama testin yerini alır|
|[C6283](/cpp/code-quality/c6283)|İlkel dizi-yeni skaler-silme uyumsuzluğu|
|[C6284](/cpp/code-quality/c6284)|Biçimlendirme Işlevine geçersiz nesne değişkeni|
|[C6285](/cpp/code-quality/c6285)|Sabitler mantıksal or|
|[C6286](/cpp/code-quality/c6286)|Sıfır olmayan mantıksal veya kayıp yan etkileri|
|[C6287](/cpp/code-quality/c6287)|Gereksiz test|
|[C6288](/cpp/code-quality/c6288)|Mantıksal and üzerinde karşılıklı Içerme yanlış|
|[C6289](/cpp/code-quality/c6289)|Mantıksal or üzerinde karşılıklı dışlama doğru|
|[C6290](/cpp/code-quality/c6290)|Mantıksal değil bit düzeyinde and önceliği|
|[C6291](/cpp/code-quality/c6291)|Mantıksal değil bit düzeyinde OR önceliği|
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
|[C6314](/cpp/code-quality/c6314)|Bit düzeyinde OR önceliği|
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
|[C6383](/cpp/code-quality/c6383)|Öğe-sayım bayt sayısı arabellek taşması|
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
|[C28183](/cpp/code-quality/c28183)|Bağımsız değişken bir değer olabilir ve İşaretçisinde bulunan değerin bir kopyasıdır|
|[C28193](/cpp/code-quality/c28193)|Değişken incelenmesi gereken bir değer tutuyor|
|[C28196](/cpp/code-quality/c28196)|Gereksinim karşılanmıyor. (İfade true olarak değerlendirilmez.)|
|[C28202](/cpp/code-quality/c28202)|Statik olmayan üyeye geçersiz başvuru|
|[C28203](/cpp/code-quality/c28203)|Sınıf üyesine belirsiz başvuru.|
|[C28205](/cpp/code-quality/c28205)|\_\_ \_ \_ \_ Hatalı bir bağlamda kullanılan başarılı veya hatalı|
|[C28206](/cpp/code-quality/c28206)|Sol işlenen bir yapıya işaret ediyor, '-> ' kullanın|
|[C28207](/cpp/code-quality/c28207)|Sol işlenen bir struct, '. ' kullanın|
|[C28209](/cpp/code-quality/c28209)|Sembol bildiriminin çakışan bir bildirimi vardır|
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
|[C28244](/cpp/code-quality/c28244)|İşlev için ek açıklama, ayrıştırılamayan bir parametre/dış ek açıklamaya sahiptir|
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
|[C28306](/cpp/code-quality/c28306)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28307](/cpp/code-quality/c28307)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28350](/cpp/code-quality/c28350)|Ek açıklama koşullu olarak uygulanabilir olmayan bir durum tanımlar.|
|[C28351](/cpp/code-quality/c28351)|Ek açıklama, koşulda bir dinamik değerin (bir değişken) kullanılamayacağını açıklar.|
|[CA1001](../code-quality/ca1001.md)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1009](../code-quality/ca1009.md)|Olay işleyicileri doğru olarak bildirin|
|[CA1016](../code-quality/ca1016.md)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|
|[CA1033](../code-quality/ca1033.md)|Arabirim metotları alt türler tarafından çağrılabilmelidir|
|[CA1049](../code-quality/ca1049.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|
|[CA1060](../code-quality/ca1060.md)|P/Invokes'u NativeMethods sınıfına taşıyın|
|[CA1061](../code-quality/ca1061.md)|Temel sınıf metotlarını gizlemeyin|
|[CA1063](../code-quality/ca1063.md)|IDisposable'ı doğru uygulayın|
|[CA1065](../code-quality/ca1065.md)|Beklenmeyen konumlarda özel durum harekete geçirmeyin|
|[CA1301](../code-quality/ca1301.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](../code-quality/ca1401.md)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403.md)|Otomatik yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404.md)|P/Invoke ardından hemen GetLastError çağırın|
|[CA1405](../code-quality/ca1405.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410.md)|COM kayıt metotları eşleşmelidir|
|[CA1415](../code-quality/ca1415.md)|P/Invoke'ları doğru bildirin|
|[CA1821](../code-quality/ca1821.md)|Boş sonlandırıcıları kaldırın|
|[CA1900](../code-quality/ca1900.md)|Değer tür alanları taşınabilir olmalıdır|
|[CA1901](../code-quality/ca1901.md)|P/Invoke bildirimleri taşınabilir olmalıdır|
|[CA2002](../code-quality/ca2002.md)|Zayıf kimliği olan nesneleri kilitlemeyin|
|[CA2100](../code-quality/ca2100.md)|SQL sorgularını güvenlik açıkları için inceleyin|
|[CA2101](../code-quality/ca2101.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
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
|[CA2141](../code-quality/ca2141.md)|Saydam yöntemler bağlantı taleplerini karşılamamalıdır|
|[CA2146](../code-quality/ca2146.md)|Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147.md)|Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır|
|[CA2149](../code-quality/ca2149.md)|Saydam metotlar yerel kod içine çağırmamalıdır|
|[CA2200](../code-quality/ca2200.md)|Yığın ayrıntılarını korumak için yeniden fırlatın|
|[CA2202](../code-quality/ca2202.md)|Nesneleri birden çok kez atmayın|
|[CA2207](../code-quality/ca2207.md)|Değer türü statik alanları satır içi başlatın|
|[CA2212](../code-quality/ca2212.md)|Servis verilen bileşenleri WebMethod ile işaretlemeyin|
|[CA2213](../code-quality/ca2213.md)|Atılabilen alanlar atılmalıdır|
|[CA2214](../code-quality/ca2214.md)|Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın|
|[CA2216](../code-quality/ca2216.md)|Atılabilir türler sonlandırıcıyı bildirmelidir|
|[CA2220](../code-quality/ca2220.md)|Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır|
|[CA2229](../code-quality/ca2229.md)|Serileştirme oluşturucularını uygulayın|
|[CA2231](../code-quality/ca2231.md)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|
|[CA2232](../code-quality/ca2232.md)|Windows Forms giriş noktalarını STAThread ile işaretleyin|
|[CA2235](../code-quality/ca2235.md)|Tüm serileştirilebilir olmayan alanları işaretleyin|
|[CA2236](../code-quality/ca2236.md)|ISerializable türler üzerinde taban sınıf metotlarını çağırın|
|[CA2237](../code-quality/ca2237.md)|ISerializable türleri SerializableAttribute ile işaretleyin|
|[CA2238](../code-quality/ca2238.md)|Serileştirme metotlarını doğru uygulayın|
|[CA2240](../code-quality/ca2240.md)|ISerializable'ı doğru uygulayın|
|[CA2241](../code-quality/ca2241.md)|Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın|
|[CA2242](../code-quality/ca2242.md)|NaN için doğru test edin|