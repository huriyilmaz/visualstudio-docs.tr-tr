---
title: Karışık Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ce642ee57112561ba687b7ebe962150ce4e268e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446540"
---
# <a name="mixed-recommended-rules-rule-set"></a>Karışık Önerilen Kurallar kural kümesi

Microsoft Mixed önerilen kurallar, C++ projelerinizde olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere ortak dil çalışma zamanını destekleyen en yaygın ve kritik sorunlara odaklanmaktadır. Bu kural kümesi, [karışık minimum kurallar](mixed-minimum-rules-rule-set.md) kural kümesindeki tüm kuralları içerir.

Bu kuralı, ortak dil çalışma zamanını destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine ekleyin.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Başlatılmamış belleği kullanma|
|[C6011](../code-quality/c6011.md)|Null Işaretçisinin başvurusu|
|[C6029](../code-quality/c6029.md)|Işaretlenmemiş değer kullanımı|
|[C6031](../code-quality/c6031.md)|Dönüş değeri yoksayıldı|
|[C6053](../code-quality/c6053.md)|Çağrıdan sıfır sonlandırma|
|[C6054](../code-quality/c6054.md)|Sıfır sonlandırma eksik|
|[C6059](../code-quality/c6059.md)|Hatalı birleştirme|
|[C6063](../code-quality/c6063.md)|Biçimlendirme Işlevinde dize bağımsız değişkeni eksik|
|[C6064](../code-quality/c6064.md)|Biçimlendirme Işlevinde eksik tamsayı bağımsız değişkeni|
|[C6066](../code-quality/c6066.md)|Biçimlendirme Işlevinde eksik Işaretçi değişkeni|
|[C6067](../code-quality/c6067.md)|Biçimlendirme Işlevinde eksik dize Işaretçisi bağımsız değişkeni|
|[C6101](../code-quality/c6101.md)|Başlatılmamış bellek döndürülüyor|
|[C6200](../code-quality/c6200.md)|Dizin, arabellek üst sınırını aşıyor|
|[C6201](../code-quality/c6201.md)|Dizin yığın arabelleği üst sınırını aşıyor|
|[C6214](../code-quality/c6214.md)|HRESULT Ile BOOL arasında geçersiz atama|
|[C6215](../code-quality/c6215.md)|Geçersiz tür BOOL olarak HRESULT|
|[C6216](../code-quality/c6216.md)|Geçersiz derleyici ile ekli atama BOOL 'A dönüştürüldü|
|[C6217](../code-quality/c6217.md)|NOT Ile geçersiz HRESULT testi|
|[C6220](../code-quality/c6220.md)|-1 Ile geçersiz HRESULT karşılaştırması|
|[C6226](../code-quality/c6226.md)|-1 Için geçersiz HRESULT ataması|
|[C6230](../code-quality/c6230.md)|Boole olarak geçersiz HRESULT kullanımı|
|[C6235](../code-quality/c6235.md)|Mantıksal or Ile sıfır olmayan sabit|
|[C6236](../code-quality/c6236.md)|Sıfır olmayan sabit Ile mantıksal or|
|[C6237](../code-quality/c6237.md)|Mantıksal-ve yan etkileri olan sıfır|
|[C6242](../code-quality/c6242.md)|Yerel geriye doğru Izleme zorlandı|
|[C6248](../code-quality/c6248.md)|NULL DACL oluşturuluyor|
|[C6250](../code-quality/c6250.md)|Yayımlanverilmemiş adres tanımlayıcıları|
|[C6255](../code-quality/c6255.md)|Korumasız alloca kullanımı|
|[C6258](../code-quality/c6258.md)|Sonlandırma Iş parçacığını kullanma|
|[C6259](../code-quality/c6259.md)|Bit düzeyinde veya sınırlı anahtarda ölü kod|
|[C6260](../code-quality/c6260.md)|Bayt aritmetiği kullanımı|
|[C6262](../code-quality/c6262.md)|Aşırı yığın kullanımı|
|[C6263](../code-quality/c6263.md)|Döngüde alloca kullanma|
|[C6268](../code-quality/c6268.md)|Dönüştürmede parantez eksik|
|[C6269](../code-quality/c6269.md)|İşaretçi başvurusu yoksayıldı|
|[C6270](../code-quality/c6270.md)|Biçimlendirme Işlevinde float bağımsız değişkeni eksik|
|[C6271](../code-quality/c6271.md)|Biçim Işlevine fazladan bağımsız değişken|
|[C6272](../code-quality/c6272.md)|Biçimlendirme Işlevinde kayan olmayan bağımsız değişken|
|[C6273](../code-quality/c6273.md)|Biçimlendirme Işlevinde tamsayı olmayan bağımsız değişken|
|[C6274](../code-quality/c6274.md)|Biçimlendirme Işlevinde karakter olmayan bağımsız değişken|
|[C6276](../code-quality/c6276.md)|Geçersiz dize dönüştürme|
|[C6277](../code-quality/c6277.md)|Geçersiz CreateProcess çağrısı|
|[C6278](../code-quality/c6278.md)|Dizi-yeni skaler-silme uyumsuzluğu|
|[C6279](../code-quality/c6279.md)|Skaler-yeni dizi-silme uyumsuzluğu|
|[C6280](../code-quality/c6280.md)|Bellek ayırma-ayırmayı kaldırma uyumsuzluğu|
|[C6281](../code-quality/c6281.md)|Bit düzeyinde Ilişki önceliği|
|[C6282](../code-quality/c6282.md)|Atama testin yerini alır|
|[C6283](../code-quality/c6283.md)|İlkel dizi-yeni skaler-silme uyumsuzluğu|
|[C6284](../code-quality/c6284.md)|Biçimlendirme Işlevine geçersiz nesne değişkeni|
|[C6285](../code-quality/c6285.md)|Sabitler mantıksal or|
|[C6286](../code-quality/c6286.md)|Sıfır olmayan mantıksal veya kayıp yan etkileri|
|[C6287](../code-quality/c6287.md)|Gereksiz test|
|[C6288](../code-quality/c6288.md)|Mantıksal and üzerinde karşılıklı Içerme yanlış|
|[C6289](../code-quality/c6289.md)|Mantıksal or üzerinde karşılıklı dışlama doğru|
|[C6290](../code-quality/c6290.md)|Mantıksal değil bit düzeyinde and önceliği|
|[C6291](../code-quality/c6291.md)|Mantıksal değil bit düzeyinde OR önceliği|
|[C6292](../code-quality/c6292.md)|Döngü en yüksek değerinden yukarı sayılır|
|[C6293](../code-quality/c6293.md)|Döngü en küçük değerden aşağı doğru sayılır|
|[C6294](../code-quality/c6294.md)|Döngü gövdesi hiç yürütülmedi|
|[C6295](../code-quality/c6295.md)|Sonsuz döngü|
|[C6296](../code-quality/c6296.md)|Döngü yalnızca bir kez yürütüldü|
|[C6297](../code-quality/c6297.md)|SHIFT 'e daha büyük boyuta dönüştürme sonucu|
|[C6299](../code-quality/c6299.md)|Bit alanını Boole karşılaştırmaya göre|
|[C6302](../code-quality/c6302.md)|Biçimlendirme Işlevine geçersiz karakter dizesi değişkeni|
|[C6303](../code-quality/c6303.md)|Biçimlendirme Işlevine geçersiz geniş karakter dizesi değişkeni|
|[C6305](../code-quality/c6305.md)|Eşleşmeyen boyut ve sayı kullanımı|
|[C6306](../code-quality/c6306.md)|Değişken bağımsız değişken Işlev çağrısı yanlış|
|[C6308](../code-quality/c6308.md)|Realloc sızıntısı|
|[C6310](../code-quality/c6310.md)|Geçersiz özel durum filtre sabiti|
|[C6312](../code-quality/c6312.md)|Özel durum yürütme döngüsüne devam et|
|[C6314](../code-quality/c6314.md)|Bit düzeyinde OR önceliği|
|[C6317](../code-quality/c6317.md)|Tamamlayıcı değil|
|[C6318](../code-quality/c6318.md)|Özel durum aramaya devam et|
|[C6319](../code-quality/c6319.md)|Virgülle yoksayıldı|
|[C6324](../code-quality/c6324.md)|Dize karşılaştırma yerine dize kopyalama|
|[C6328](../code-quality/c6328.md)|Olası bağımsız değişken türü uyumsuzluğu|
|[C6331](../code-quality/c6331.md)|VirtualFree geçersiz bayrakları|
|[C6332](../code-quality/c6332.md)|VirtualFree geçersiz parametresi|
|[C6333](../code-quality/c6333.md)|VirtualFree geçersiz boyutu|
|[C6335](../code-quality/c6335.md)|Sızan Işlem tanıtıcısı|
|[C6381](../code-quality/c6381.md)|Kapatılmış bilgiler eksik|
|[C6383](../code-quality/c6383.md)|Öğe-sayım bayt sayısı arabellek taşması|
|[C6384](../code-quality/c6384.md)|İşaretçi boyutu bölümü|
|[C6385](../code-quality/c6385.md)|Okuma taşması|
|[C6386](../code-quality/c6386.md)|Yazma taşması|
|[C6387](../code-quality/c6387.md)|Geçersiz parametre değeri|
|[C6388](../code-quality/c6388.md)|Geçersiz parametre değeri|
|[C6500](../code-quality/c6500.md)|Geçersiz öznitelik özelliği|
|[C6501](../code-quality/c6501.md)|Çakışan öznitelik özellik değerleri|
|[C6503](../code-quality/c6503.md)|Başvurular null olamaz|
|[C6504](../code-quality/c6504.md)|Işaretçi olmayan üzerinde null|
|[C6505](../code-quality/c6505.md)|Void üzerinde MustCheck|
|[C6506](../code-quality/c6506.md)|Işaretçi olmayan veya dizide arabellek boyutu|
|[C6508](../code-quality/c6508.md)|Sabit üzerinde yazma erişimi|
|[C6509](../code-quality/c6509.md)|Ön koşul üzerinde kullanılan dönüş|
|[C6510](../code-quality/c6510.md)|Işaretçili olmayan boş değer sonlandırıldı|
|[C6511](../code-quality/c6511.md)|MustCheck Evet veya Hayır olmalıdır|
|[C6513](../code-quality/c6513.md)|Arabellek boyutu olmadan öğe boyutu|
|[C6514](../code-quality/c6514.md)|Arabellek boyutu, dizi boyutunu aşıyor|
|[C6515](../code-quality/c6515.md)|Işaretçi olmayan ara bellek boyutu|
|[C6516](../code-quality/c6516.md)|Öznitelikte özellik yok|
|[C6517](../code-quality/c6517.md)|Okunabilir olmayan arabellekte geçerli boyut|
|[C6518](../code-quality/c6518.md)|Yazılabilir olmayan arabellekte yazılabilir boyut|
|[C6522](../code-quality/c6522.md)|Geçersiz boyut dize türü|
|[C6525](../code-quality/c6525.md)|Geçersiz boyut dizesine ulaşılamıyor konumu|
|[C6527](../code-quality/c6527.md)|Geçersiz ek açıklama: ' gereksiz Srelease ' özelliği void türünün değerleri üzerinde kullanılamaz|
|[C6530](../code-quality/c6530.md)|Tanınmayan biçim dizesi stili|
|[C6540](../code-quality/c6540.md)|Bu işlev üzerinde öznitelik ek açıklamaları kullanımı, var olan tüm __declspec ek açıklamalarını geçersiz kılar|
|[C6551](../code-quality/c6551.md)|Geçersiz boyut belirtimi: ifade ayrıştırılamıyor|
|[C6552](../code-quality/c6552.md)|Geçersiz Deref = veya Notref =: ifade ayrıştırılamıyor|
|[C6701](../code-quality/c6701.md)|Değer geçerli bir Evet/Hayır/belki değeri değil|
|[C6702](../code-quality/c6702.md)|Değer bir dize değeri değil|
|[C6703](../code-quality/c6703.md)|Değer bir sayı değil|
|[C6704](../code-quality/c6704.md)|Beklenmeyen ek açıklama Ifadesi hatası|
|[C6705](../code-quality/c6705.md)|Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşleşmiyor|
|[C6706](../code-quality/c6706.md)|Ek açıklama için beklenmeyen ek açıklama hatası|
|[C6995](../code-quality/c6995.md)|XML günlük dosyası kaydedilemedi|
|[C26100](../code-quality/c26100.md)|Yarış durumu|
|[C26101](../code-quality/c26101.md)|Kenetlenmiş işlem düzgün şekilde kullanılamıyor|
|[C26110](../code-quality/c26110.md)|Çağıran kilidi tutamıyor|
|[C26111](../code-quality/c26111.md)|Çağıran kilidi serbest bırakamıyor|
|[C26112](../code-quality/c26112.md)|Çağıran herhangi bir kilit tutamaz|
|[C26115](../code-quality/c26115.md)|Kilit bırakılamıyor|
|[C26116](../code-quality/c26116.md)|Kilit alınamıyor veya beklet|
|[C26117](../code-quality/c26117.md)|Tutulmayan kilit bırakılıyor|
|[C26140](../code-quality/c26140.md)|Eşzamanlılık SAL ek açıklaması hatası|
|[C28020](../code-quality/c28020.md)|İfade bu çağrıda doğru değil|
|[C28021](../code-quality/c28021.md)|Açıklama eklenen parametrenin bir işaretçi olması gerekir|
|[C28022](../code-quality/c28022.md)|Bu işlevdeki işlev sınıfı (es), kendisini tanımlamak için kullanılan typedef üzerindeki işlev sınıfları ile eşleşmiyor.|
|[C28023](../code-quality/c28023.md)|Atanan veya geçirilen işlev, en az bir sınıftan (es) bir \_Function @ no__t-1class @ no__t-2 ek açıklamasına sahip olmalıdır|
|[C28024](../code-quality/c28024.md)|Atanmakta olan işlev işaretçisine işlev sınıfı (es) listesinde bulunmayan işlev sınıfıyla açıklama eklenir.|
|[C28039](../code-quality/c28039.md)|Gerçek parametre türü, türle tam olarak eşleşmelidir|
|[C28112](../code-quality/c28112.md)|Birbirine kenetlenmiş bir işlev aracılığıyla erişilen bir değişkene, her zaman birbirine kenetlenmiş bir işlev aracılığıyla erişilmesi gerekir.|
|[C28113](../code-quality/c28113.md)|Birbirine kenetlenmiş bir işlev aracılığıyla yerel bir değişkene erişme|
|[C28125](../code-quality/c28125.md)|İşlev bir try/except bloğu içinden çağrılmalıdır|
|[C28137](../code-quality/c28137.md)|Değişken bağımsız değişkeni bunun yerine bir (sabit değer) sabit olmalıdır|
|[C28138](../code-quality/c28138.md)|Sabit bağımsız değişken bunun yerine değişken olmalıdır|
|[C28159](../code-quality/c28159.md)|Bunun yerine başka bir işlev kullanmayı düşünün.|
|[C28160](../code-quality/c28160.md)|Hata ek açıklaması|
|[C28163](../code-quality/c28163.md)|İşlev bir try/except bloğunun içinden asla çağrılmamalıdır|
|[C28164](../code-quality/c28164.md)|Bağımsız değişken bir nesneye işaretçi bekleyen bir işleve geçiriliyor (bir işaretçiye işaretçi değil)|
|[C28182](../code-quality/c28182.md)|NULL işaretçiyle başvuruluyor. İşaretçi, başka bir işaretçi ile aynı NULL değeri içeriyor.|
|[C28183](../code-quality/c28183.md)|Bağımsız değişken bir değer olabilir ve İşaretçisinde bulunan değerin bir kopyasıdır|
|[C28193](../code-quality/c28193.md)|Değişken incelenmesi gereken bir değer tutuyor|
|[C28196](../code-quality/c28196.md)|Gereksinim karşılanmıyor. (İfade true olarak değerlendirilmez.)|
|[C28202](../code-quality/c28202.md)|Statik olmayan üyeye geçersiz başvuru|
|[C28203](../code-quality/c28203.md)|Sınıf üyesine belirsiz başvuru.|
|[C28205](../code-quality/c28205.md)|\_Success @ no__t-1 veya \_On @ no__t-3failure @ no__t-4 geçersiz bir bağlamda kullanıldı|
|[C28206](../code-quality/c28206.md)|Sol işlenen bir yapıya işaret ediyor, '-> ' kullanın|
|[C28207](../code-quality/c28207.md)|Sol işlenen bir struct, '. ' kullanın|
|[C28209](../code-quality/c28209.md)|Sembol bildiriminin çakışan bir bildirimi vardır|
|[C28210](../code-quality/c28210.md)|__On_failure bağlamının ek açıklamaları açık bir ön bağlamda olmamalıdır|
|[C28211](../code-quality/c28211.md)|SAL_context için beklenen statik bağlam adı|
|[C28212](../code-quality/c28212.md)|Ek açıklama için beklenen işaretçi ifadesi|
|[C28213](../code-quality/c28213.md)|@No__t-0Use @ no__t-1decl @ no__t-2annotation @ no__t-3 ek açıklaması, önceki bir bildirime göre başvurulmadan önce kullanılmalıdır.|
|[C28214](../code-quality/c28214.md)|Öznitelik parametresi adları P1 olmalıdır... P9 olmalıdır|
|[C28215](../code-quality/c28215.md)|Typedüzeltmesini zaten bir tür düzeltmesine sahip olan bir parametreye uygulanamaz|
|[C28216](../code-quality/c28216.md)|CheckReturn ek açıklaması yalnızca belirli işlev parametresi için Sonkoşulları için geçerlidir.|
|[C28217](../code-quality/c28217.md)|İşlev için, ek açıklamanın parametre sayısı dosyada bulunan ile eşleşmiyor|
|[C28218](../code-quality/c28218.md)|İşlev parametresi için ek açıklamanın parametresi dosyada bulunan ile eşleşmiyor|
|[C28219](../code-quality/c28219.md)|Ek açıklamada parametre ek açıklaması için beklenen numaralandırma üyesi|
|[C28220](../code-quality/c28220.md)|Ek açıklamada parametre ek açıklaması için beklenen tamsayı ifadesi|
|[C28221](../code-quality/c28221.md)|Ek açıklamada parametre için beklenen dize ifadesi|
|[C28222](../code-quality/c28222.md)|__yes, @no__t -0 _No veya @no__t -1 _annotation için beklenen olabilir|
|[C28223](../code-quality/c28223.md)|Ek açıklama, parametre için beklenen belirteç/tanımlayıcı bulunamadı|
|[C28224](../code-quality/c28224.md)|Ek açıklama parametre gerektiriyor|
|[C28225](../code-quality/c28225.md)|Ek açıklamada gerekli parametrelerin doğru sayısı bulunamadı|
|[C28226](../code-quality/c28226.md)|Ek açıklama aynı zamanda bir PrimOp olamaz (geçerli bildirimde)|
|[C28227](../code-quality/c28227.md)|Ek açıklama aynı zamanda bir PrimOp olamaz (önceki bildirime bakın)|
|[C28228](../code-quality/c28228.md)|Ek açıklama parametresi: ek açıklamalarda tür kullanılamaz|
|[C28229](../code-quality/c28229.md)|Ek açıklama parametreleri desteklemiyor|
|[C28230](../code-quality/c28230.md)|Parametre türünün üyesi yok.|
|[C28231](../code-quality/c28231.md)|Ek açıklama yalnızca dizide geçerlidir|
|[C28232](../code-quality/c28232.md)|herhangi bir ek açıklamaya ön, post veya deref uygulanmadı|
|[C28233](../code-quality/c28233.md)|bir bloğa ön, sonrası veya deref uygulandı|
|[C28234](../code-quality/c28234.md)|__at ifadesi geçerli işleve uygulanmıyor|
|[C28235](../code-quality/c28235.md)|İşlev bir ek açıklama olarak tek başına kullanılamaz|
|[C28236](../code-quality/c28236.md)|Ek açıklama bir ifadede kullanılamaz|
|[C28237](../code-quality/c28237.md)|Parametresindeki ek açıklama artık desteklenmiyor|
|[C28238](../code-quality/c28238.md)|Parametresindeki ek açıklamanın birden fazla değeri, stringValue ve longValue 'ı vardır. Paramn = xxx kullanın|
|[C28239](../code-quality/c28239.md)|Parametresindeki ek açıklamanın değeri, stringValue veya longValue; ve Paramn = xxx. Yalnızca paramn = xxx kullanın|
|[C28240](../code-quality/c28240.md)|Parametresindeki ek açıklamanın param2 vardır ancak Param1 yok|
|[C28241](../code-quality/c28241.md)|Parametre üzerindeki işlev için ek açıklama tanınmıyor|
|[C28243](../code-quality/c28243.md)|Parametresindeki işlev için ek açıklama, ek açıklama eklenmiş olarak daha fazla başvuru gerektiriyor|
|[C28244](../code-quality/c28244.md)|İşlev için ek açıklama, ayrıştırılamayan bir parametre/dış ek açıklamaya sahiptir|
|[C28245](../code-quality/c28245.md)|İşlev açıklamasına yönelik ek açıklama ' this ' öğesini üye olmayan bir işlev üzerinde Tates|
|[C28246](../code-quality/c28246.md)|İşlevin parametre ek açıklaması, parametrenin türü ile eşleşmiyor|
|[C28250](../code-quality/c28250.md)|İşlev için tutarsız ek açıklama: önceki örnekte hata var.|
|[C28251](../code-quality/c28251.md)|İşlev için tutarsız ek açıklama: Bu örnekte hata var.|
|[C28252](../code-quality/c28252.md)|İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.|
|[C28253](../code-quality/c28253.md)|İşlev için tutarsız ek açıklama: parametre bu örnekteki başka bir ek açıklamaya sahip.|
|[C28254](../code-quality/c28254.md)|ek açıklamalarda dynamic_cast < > () desteklenmiyor|
|[C28262](../code-quality/c28262.md)|Ek açıklama için işlevde bir sözdizimi hatası bulundu|
|[C28263](../code-quality/c28263.md)|Iç ek açıklamanın koşullu ek açıklamasında söz dizimi hatası bulundu|
|[C28267](../code-quality/c28267.md)|Ek açıklamalarda bir söz dizimi hatası bulundu.|
|[C28272](../code-quality/c28272.md)|İşlevi için ek açıklama, incelenirken parametresi, işlev bildirimiyle tutarsız|
|[C28273](../code-quality/c28273.md)|İşlev için, ipuçları işlev bildirimiyle tutarsız|
|[C28275](../code-quality/c28275.md)|@No__t-0Macro @ no__t-1value @ no__t-2 parametresi null|
|[C28279](../code-quality/c28279.md)|Sembol için, eşleşen bir ' End ' olmadan bir ' begin' bulundu|
|[C28280](../code-quality/c28280.md)|Sembol için, eşleşen bir ' begin' olmadan bir ' End ' bulundu|
|[C28282](../code-quality/c28282.md)|Biçim dizeleri ön koşullarda olmalıdır|
|[C28285](../code-quality/c28285.md)|İşlev için, parametrede söz dizimi hatası|
|[C28286](../code-quality/c28286.md)|İşlev için, sonda yakınında sözdizimi hatası|
|[C28287](../code-quality/c28287.md)|İşlev için, \_Konumundaki @ no__t-1 () ek açıklamasında söz dizimi hatası (Tanınmayan parametre adı)|
|[C28288](../code-quality/c28288.md)|İşlev için, \_Konumundaki @ no__t-1 () ek açıklamasında söz dizimi hatası (geçersiz parametre adı)|
|[C28289](../code-quality/c28289.md)|İşlev için: ReadableTo veya WritableTo parametre olarak bir limit-spec içermiyordu|
|[C28290](../code-quality/c28290.md)|işlev için ek açıklama, gerçek parametre sayısından daha fazla dışlar içeriyor|
|[C28291](../code-quality/c28291.md)|deref düzey 0 ' da null/NotNull Post işlevi için anlamsız bir küçüktür.|
|[C28300](../code-quality/c28300.md)|İşleç için uyumsuz türlerin ifade işlenenleri|
|[C28301](../code-quality/c28301.md)|İşlevin ilk bildirimi için ek açıklama yok.|
|[C28302](../code-quality/c28302.md)|Ek açıklamada fazladan bir \_Deref @ no__t-1 işleci bulundu.|
|[C28303](../code-quality/c28303.md)|Ek açıklamada belirsiz bir \_Deref @ no__t-1 işleci bulundu.|
|[C28304](../code-quality/c28304.md)|Belirtece hatalı yerleştirilmiş \_Notref @ no__t-1 işleci uygulandı.|
|[C28305](../code-quality/c28305.md)|Belirteç ayrıştırılırken bir hata bulundu.|
|[C28306](../code-quality/c28306.md)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28307](../code-quality/c28307.md)|Parametresindeki ek açıklama kullanımdan görünmez|
|[C28350](../code-quality/c28350.md)|Ek açıklama koşullu olarak uygulanabilir olmayan bir durum tanımlar.|
|[C28351](../code-quality/c28351.md)|Ek açıklama, koşulda bir dinamik değerin (bir değişken) kullanılamayacağını açıklar.|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Olay işleyicileri doğru olarak bildirin|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Arabirim metotları alt türler tarafından çağrılabilmelidir|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invokes'u NativeMethods sınıfına taşıyın|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Temel sınıf metotlarını gizlemeyin|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable'ı doğru uygulayın|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Beklenmeyen konumlarda özel durum harekete geçirmeyin|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Otomatik yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke ardından hemen GetLastError çağırın|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM kayıt metotları eşleşmelidir|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invoke'ları doğru bildirin|
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
|[CA2116Ç](../code-quality/ca2116.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
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
