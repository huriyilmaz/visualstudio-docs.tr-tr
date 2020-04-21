---
title: Yerel Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a86cb62fe0ae0db971a417ef923f45eedbefe0c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649290"
---
# <a name="native-recommended-rules-rule-set"></a>Yerel Önerilen Kurallar kural kümesi

Yerel Önerilen Kurallar, olası güvenlik açıkları ve uygulama kilitlenmeleri de dahil olmak üzere yerel koddaki en kritik ve yaygın sorunlara odaklanır. Bu kural kümesi, [Yerel Minimum Kurallar](native-minimum-rules-rule-set.md) kuralı kümesindeki tüm kuralları içerir.

Yerel projeler için oluşturduğunuz herhangi bir özel kural kümesine ayarlanan bu kuralı ekleyin.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Başharfsiz Bellek Kullanma|
|[C6011](../code-quality/c6011.md)|Null Pointer'ı Dereferencing|
|[C6029](../code-quality/c6029.md)|İşaretlenmemiş Değerin Kullanımı|
|[C6031](../code-quality/c6031.md)|İade Değeri Yoksayılır|
|[C6053](../code-quality/c6053.md)|Çağrıdan Sıfır Sonlandırma|
|[C6054](../code-quality/c6054.md)|Sıfır Sonlandırma Eksik|
|[C6059](../code-quality/c6059.md)|Kötü Concatenation|
|[C6063](../code-quality/c6063.md)|İşlev biçimlendirmek için eksik string bağımsız değişkeni|
|[C6064](../code-quality/c6064.md)|İşlev biçimlendirmek için Eksik Sonda Bağımsız Değişkeni|
|[C6066](../code-quality/c6066.md)|İşlev biçimlendirmek için işaretçi bağımsız değişkeni eksik|
|[C6067](../code-quality/c6067.md)|İşlev biçimlendirmek için String Pointer bağımsız değişkeni eksik|
|[C6101](../code-quality/c6101.md)|Başharfe getirilmemiş belleği döndürme|
|[C6200](../code-quality/c6200.md)|Dizin Arabellek Maksimumu Aşıyor|
|[C6201](../code-quality/c6201.md)|Dizin Yığın Arabellek Maksimum aşıyor|
|[C6214](../code-quality/c6214.md)|Geçersiz Döküm HRESULT BOOL için|
|[C6215](../code-quality/c6215.md)|Geçersiz Döküm BOOL HRESULT için|
|[C6216](../code-quality/c6216.md)|Geçersiz Derleyici-Eklenen Dökme BOOL HRESULT için|
|[C6217](../code-quality/c6217.md)|NOT ile Geçersiz HRESULT Testi|
|[C6220](../code-quality/c6220.md)|Geçersiz HRESULT Karşılaştır -1|
|[C6226](../code-quality/c6226.md)|Geçersiz HRESULT Atama -1|
|[C6230](../code-quality/c6230.md)|Geçersiz HRESULT Boolean olarak kullanın|
|[C6235](../code-quality/c6235.md)|Mantıksal veya sıfır olmayan sabit|
|[C6236](../code-quality/c6236.md)|Mantıksal-veya sıfır olmayan sabitile|
|[C6237](../code-quality/c6237.md)|Mantıksal-Ve Yan Etkileri Kaybeder sıfır|
|[C6242](../code-quality/c6242.md)|Yerel Gevşeme Zorla|
|[C6248](../code-quality/c6248.md)|Null DACL oluşturma|
|[C6250](../code-quality/c6250.md)|Yayımlanmamış Adres Tanımlayıcıları|
|[C6255](../code-quality/c6255.md)|Alloca Korunmasız Kullanımı|
|[C6258](../code-quality/c6258.md)|Sonlandırma İş parçacığı kullanma|
|[C6259](../code-quality/c6259.md)|Bitwise-Or Sınırlı Anahtar Ölü Kod|
|[C6260](../code-quality/c6260.md)|Byte Aritmetik Kullanımı|
|[C6262](../code-quality/c6262.md)|Aşırı Yığın Kullanımı|
|[C6263](../code-quality/c6263.md)|Alloca In Loop kullanma|
|[C6268](../code-quality/c6268.md)|Döküm eksik Parantez|
|[C6269](../code-quality/c6269.md)|İşaretçi Dereference Yok Sayıldı|
|[C6270](../code-quality/c6270.md)|İşlev biçimlendirmek için Float bağımsız değişkeni eksik|
|[C6271](../code-quality/c6271.md)|İşlev biçimlendirmek için ekstra bağımsız değişken|
|[C6272](../code-quality/c6272.md)|İşlev biçimlendirmek için Float olmayan bağımsız değişken|
|[C6273](../code-quality/c6273.md)|İşlev biçimlendirmek için Non-Integer Bağımsız Değişkeni|
|[C6274](../code-quality/c6274.md)|Işlevi biçimlendirmek için karakter dışı bağımsız değişken|
|[C6276](../code-quality/c6276.md)|Geçersiz Yaylı Çalgılar Döküm|
|[C6277](../code-quality/c6277.md)|Geçersiz CreateProcess Çağrısı|
|[C6278](../code-quality/c6278.md)|Dizi-Yeni Skalar-Sil Uyuşmazlığı|
|[C6279](../code-quality/c6279.md)|Skaler-Yeni Dizi-Silme Uyuşmazlığı|
|[C6280](../code-quality/c6280.md)|Bellek Ayırma-Deallocation Uyuşmazlığı|
|[C6281](../code-quality/c6281.md)|Bitwise İlişki Önceliği|
|[C6282](../code-quality/c6282.md)|Atama Testi Değiştirir|
|[C6283](../code-quality/c6283.md)|İlkel Dizi-Yeni Skaler-Sil Uyuşmazlığı|
|[C6284](../code-quality/c6284.md)|Geçersiz Nesne Bağımsız Değişkeni İşlev biçimlendirmek için|
|[C6285](../code-quality/c6285.md)|Mantıksal-Veya Sabitler|
|[C6286](../code-quality/c6286.md)|Sıfır Olmayan Mantıksal Veya Kaybetme Yan Etkileri|
|[C6287](../code-quality/c6287.md)|Yedek Testi|
|[C6288](../code-quality/c6288.md)|Mantıksal ve yanlış üzerinde karşılıklı dahil|
|[C6289](../code-quality/c6289.md)|Mantıksal veya Doğru üzerinde karşılıklı dışlama|
|[C6290](../code-quality/c6290.md)|Mantıksal-BitWise değil-Ve Öncelik|
|[C6291](../code-quality/c6291.md)|Mantıksal-BitWise-Veya Öncelik değil|
|[C6292](../code-quality/c6292.md)|Döngü Maksimumdan Yukarı Sayar|
|[C6293](../code-quality/c6293.md)|Döngü En Düşükten Aşağı Sayar|
|[C6294](../code-quality/c6294.md)|Döngü Gövdesi Asla Yürütülmez|
|[C6295](../code-quality/c6295.md)|Sonsuz Döngü|
|[C6296](../code-quality/c6296.md)|Döngü Yalnızca Bir Kez Yürütülür|
|[C6297](../code-quality/c6297.md)|Daha büyük boyuta shift döküm sonucu|
|[C6299](../code-quality/c6299.md)|Bitfield Boolean Karşılaştırma için|
|[C6302](../code-quality/c6302.md)|Geçersiz Karakter String Bağımsız Değişkeni Biçimlendirme İşlev|
|[C6303](../code-quality/c6303.md)|Geçersiz Geniş Karakter Dize Bağımsız Değişkeni İşlev biçimlendirmek için|
|[C6305](../code-quality/c6305.md)|Uyumsuz Boyut Ve Sayım Kullanımı|
|[C6306](../code-quality/c6306.md)|Yanlış Değişken Bağımsız Değişken İşlev Çağrısı|
|[C6308](../code-quality/c6308.md)|Realloc Kaçak|
|[C6310](../code-quality/c6310.md)|Yasadışı Özel Durum Filtresi Sabiti|
|[C6312](../code-quality/c6312.md)|Özel Durum Devam Yürütme Döngüsü|
|[C6314](../code-quality/c6314.md)|Bitwise-Veya Öncelik|
|[C6317](../code-quality/c6317.md)|Tamamlayıcı Değil|
|[C6318](../code-quality/c6318.md)|Özel Durum Aramaya Devam Et|
|[C6319](../code-quality/c6319.md)|Virgülle YokSayıldı|
|[C6324](../code-quality/c6324.md)|String Yerine String Kopya Karşılaştırma|
|[C6328](../code-quality/c6328.md)|Potansiyel Bağımsız Değişken Türü Uyuşmazlığı|
|[C6331](../code-quality/c6331.md)|VirtualFree Geçersiz Bayraklar|
|[C6332](../code-quality/c6332.md)|VirtualFree Geçersiz Parametre|
|[C6333](../code-quality/c6333.md)|VirtualFree Geçersiz Boyut|
|[C6335](../code-quality/c6335.md)|Sızdırma İşlemkolu|
|[C6381](../code-quality/c6381.md)|Kapatma Bilgileri Eksik|
|[C6383](../code-quality/c6383.md)|Element-Count Bayt Sayısı Arabellek Aşımı|
|[C6384](../code-quality/c6384.md)|İşaretçi Boyut Bölümü|
|[C6385](../code-quality/c6385.md)|Oku Overrun|
|[C6386](../code-quality/c6386.md)|Overrun yaz|
|[C6387](../code-quality/c6387.md)|Geçersiz Parametre Değeri|
|[C6388](../code-quality/c6388.md)|Geçersiz Parametre Değeri|
|[C6500](../code-quality/c6500.md)|Geçersiz Öznitelik Özelliği|
|[C6501](../code-quality/c6501.md)|Çakışan Öznitelik Özellik Değerleri|
|[C6503](../code-quality/c6503.md)|Başvurular Null Olamaz|
|[C6504](../code-quality/c6504.md)|Null On Non-Pointer|
|[C6505](../code-quality/c6505.md)|MustCheck On Void|
|[C6506](../code-quality/c6506.md)|İşaretçi Olmayan Veya Dizide Arabellek Boyutu|
|[C6508](../code-quality/c6508.md)|Sabit Üzerine Erişim Yaz|
|[C6509](../code-quality/c6509.md)|Ön Koşulda Kullanılan İade|
|[C6510](../code-quality/c6510.md)|Null Non-Pointer üzerinde sonlandırıldı|
|[C6511](../code-quality/c6511.md)|Mustcheck Evet veya Hayır olmalıdır|
|[C6513](../code-quality/c6513.md)|Arabellek Boyutu Olmayan Öğe Boyutu|
|[C6514](../code-quality/c6514.md)|Arabellek Boyutu Dizi Boyutunu Aşıyor|
|[C6515](../code-quality/c6515.md)|Non-Pointer Üzerinde Arabellek Boyutu|
|[C6516](../code-quality/c6516.md)|Öznitelik Üzerinde Özellik Yok|
|[C6517](../code-quality/c6517.md)|Okunamayan Arabellekte Geçerli Boyut|
|[C6518](../code-quality/c6518.md)|Yazılabilir Olmayan Arabellek Te Yazılabilir Boyut|
|[C6522](../code-quality/c6522.md)|Geçersiz Boyut Dize Türü|
|[C6525](../code-quality/c6525.md)|Geçersiz Boyut Dize Erişilemez Konum|
|[C6527](../code-quality/c6527.md)|Geçersiz ek açıklama: 'NeedsRelease' özelliği geçersiz türdeğerleri kullanılamaz|
|[C6530](../code-quality/c6530.md)|Tanınmayan Biçim Dize Stili|
|[C6540](../code-quality/c6540.md)|Bu işlevde öznitelik ek açıklamalarının kullanılması, varolan tüm __declspec ek açıklamalarını geçersiz kılacaktır|
|[C6551](../code-quality/c6551.md)|Geçersiz boyut belirtimi: ifade ayrıştırılabilir değil|
|[C6552](../code-quality/c6552.md)|Geçersiz Deref= veya Notref=: ifade ayrıştırılabilir değil|
|[C6701](../code-quality/c6701.md)|Değer geçerli bir Evet/Hayır/Belki değeri değildir|
|[C6702](../code-quality/c6702.md)|Değer bir dize değeri değildir|
|[C6703](../code-quality/c6703.md)|Değer bir sayı değildir|
|[C6704](../code-quality/c6704.md)|Beklenmeyen Ek Açıklama İfade Saması Hatası|
|[C6705](../code-quality/c6705.md)|Ek açıklama için beklenen bağımsız değişken sayısı, ek açıklama için gerçek bağımsız değişken sayısıyla eşleşmiyor|
|[C6706](../code-quality/c6706.md)|Ek Açıklama için Beklenmeyen Ek Açıklama Hatası|
|[C6995](../code-quality/c6995.md)|XML Günlük dosyasını kaydetmek için başarısız oldu|
|[C26100](../code-quality/c26100.md)|Yarış durumu|
|[C26101](../code-quality/c26101.md)|Kilitli işlemi düzgün kullanmamak|
|[C26110](../code-quality/c26110.md)|Kilit tutmahatası arayan|
|[C26111](../code-quality/c26111.md)|Arayan kilidi serbest bırakamaz|
|[C26112](../code-quality/c26112.md)|Arayan herhangi bir kilit tutamaz|
|[C26115](../code-quality/c26115.md)|Kilidi serbest bırakılamaması|
|[C26116](../code-quality/c26116.md)|Kilit edinememe veya kilit tutma|
|[C26117](../code-quality/c26117.md)|Tutulmamış kilidi serbest bırakma|
|[C26140](../code-quality/c26140.md)|EşzamanlıSAL ek açıklama hatası|
|[C26441](../code-quality/c26441.md)|NO_UNNAMED_GUARDS|
|[C26444](../code-quality/c26444.md)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](../code-quality/c26498.md)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](../code-quality/c28020.md)|İfade bu çağrıda doğru değil|
|[C28021](../code-quality/c28021.md)|Açıklamalı olan parametre bir işaretçi olmalıdır|
|[C28022](../code-quality/c28022.md)|Bu işlevdeki işlev sınıfı(es) tanımlamak için kullanılan typedef'teki işlev sınıfı(es) ile eşleşmez.|
|[C28023](../code-quality/c28023.md)|Atanan veya geçirilen işlev, \_sınıfın\_\_ (es) en az biri için bir Fonksiyon sınıfı ek açıklama olmalıdır|
|[C28024](../code-quality/c28024.md)|Atanan işlev işaretçisi, işlev sınıfı(es) listesinde yer alan işlev sınıfıyla açıklamalı olarak açıklanır.|
|[C28039](../code-quality/c28039.md)|Gerçek parametrenin türü tam olarak türüne uygun olmalıdır|
|[C28112](../code-quality/c28112.md)|Birbirine kenetlenmiş bir işlev üzerinden erişilen bir değişkene her zaman Bir Birbirineken işlev üzerinden erişilmelidir.|
|[C28113](../code-quality/c28113.md)|Bir Yerel değişkene Birbirine bağlı bir işlev le erişim|
|[C28125](../code-quality/c28125.md)|Fonksiyon bir try/except bloğu içinden çağrılmalıdır|
|[C28137](../code-quality/c28137.md)|Değişken bağımsız değişken bunun yerine bir (literal) sabit olmalıdır|
|[C28138](../code-quality/c28138.md)|Sabit bağımsız değişken bunun yerine değişken olmalıdır|
|[C28159](../code-quality/c28159.md)|Bunun yerine başka bir işlev kullanmayı düşünün.|
|[C28160](../code-quality/c28160.md)|Hata ek açıklaması|
|[C28163](../code-quality/c28163.md)|İşlev hiçbir zaman bir try/except bloğundan çağrılmamalıdır|
|[C28164](../code-quality/c28164.md)|Bağımsız değişken, bir nesneye işaretçi bekleyen bir işleve geçiriliyor (işaretçi işaretçisi değil)|
|[C28182](../code-quality/c28182.md)|NULL işaretçisini dereferencing. İşaretçi, başka bir işaretçiyle aynı NULL değerini içerir.|
|[C28183](../code-quality/c28183.md)|Bağımsız değişken tek bir değer olabilir ve işaretçide bulunan değerin bir kopyasıdır|
|[C28193](../code-quality/c28193.md)|Değişken incelenmesi gereken bir değer tutar|
|[C28196](../code-quality/c28196.md)|Gereksinim yerine getirilmedi. (İfade doğru olarak değerlendirilmez.)|
|[C28202](../code-quality/c28202.md)|Statik olmayan üyeye yasa dışı başvuru|
|[C28203](../code-quality/c28203.md)|Sınıf üyesine belirsiz başvuru.|
|[C28205](../code-quality/c28205.md)|\_Başarı\_ \_veya\_\_ Yasadışı bir bağlamda kullanılan başarısızlık|
|[C28206](../code-quality/c28206.md)|Sol operand noktaları bir yapı, '->' kullanın|
|[C28207](../code-quality/c28207.md)|Sol operand bir yapı, kullanın '.'|
|[C28209](../code-quality/c28209.md)|Sembol bildiriminin çelişkili bir bildirimi vardır|
|[C28210](../code-quality/c28210.md)|__on_failure bağlamiçin ek açıklamalar açık ön bağlamda olmamalıdır|
|[C28211](../code-quality/c28211.md)|SAL_context için beklenen statik bağlam adı|
|[C28212](../code-quality/c28212.md)|Ek açıklama için işaretçi ifadesi bekleniyor|
|[C28213](../code-quality/c28213.md)|\_Kullanım\_eksilifikasyonları\_\_ ek açıklama, değişiklik yapılmadan, önceki bir bildirime başvurmak için kullanılmalıdır.|
|[C28214](../code-quality/c28214.md)|Öznitelik parametre adları p1 olmalıdır... p9|
|[C28215](../code-quality/c28215.md)|Yazı düzeltmesi zaten bir yazı düzeltmesi olan bir parametreye uygulanamaz|
|[C28216](../code-quality/c28216.md)|CheckReturn ek gösterimi yalnızca belirli işlev parametresi için posta koşulları için geçerlidir.|
|[C28217](../code-quality/c28217.md)|İşlev için, ek açıklama için parametre sayısı dosyada bulunan eşleşmiyor|
|[C28218](../code-quality/c28218.md)|İşlev parametresi için, ek açıklamanın parametresi dosyada bulunan parametreyle eşleşmiyor|
|[C28219](../code-quality/c28219.md)|Ek açıklamadaki parametrenin ek açıklama için beklenen numaralandırma üyesi|
|[C28220](../code-quality/c28220.md)|Ek açıklamadaki parametrenin ek açıklama için beklenen onsayı ifadesi|
|[C28221](../code-quality/c28221.md)|Ek açıklamadaki parametre için beklenen dize ifadesi|
|[C28222](../code-quality/c28222.md)|__yes, \__no \_veya _maybe ek açıklama bekleniyor|
|[C28223](../code-quality/c28223.md)|Ek açıklama, parametre için beklenen Belirteç/tanımlayıcı bulamadım|
|[C28224](../code-quality/c28224.md)|Ek açıklama parametreleri gerektirir|
|[C28225](../code-quality/c28225.md)|Ek açıklamada gerekli parametrelerin doğru sayısını bulamadım|
|[C28226](../code-quality/c28226.md)|Ek açıklama da primop (geçerli bildirimde) olamaz|
|[C28227](../code-quality/c28227.md)|Ek açıklama da primOp olamaz (bkz. önceki bildirim)|
|[C28228](../code-quality/c28228.md)|Ek açıklama parametresi: ek açıklamalarta türü kullanamaz|
|[C28229](../code-quality/c28229.md)|Ek açıklama parametreleri desteklemez|
|[C28230](../code-quality/c28230.md)|Parametre türüüye yoktur.|
|[C28231](../code-quality/c28231.md)|Ek açıklama yalnızca dizide geçerlidir|
|[C28232](../code-quality/c28232.md)|herhangi bir ek açıklama için uygulanmayan pre, post veya deref|
|[C28233](../code-quality/c28233.md)|bir blota uygulanan pre, post veya deref|
|[C28234](../code-quality/c28234.md)|__at ifadesi geçerli işlev için geçerli değildir|
|[C28235](../code-quality/c28235.md)|İşlev bir ek açıklama olarak tek başına duramaz|
|[C28236](../code-quality/c28236.md)|Ek açıklama bir ifadede kullanılamaz|
|[C28237](../code-quality/c28237.md)|Parametredeki ek açıklama artık desteklenmiyor|
|[C28238](../code-quality/c28238.md)|Parametredeki ek açıklama, birden fazla değere, stringValue'e ve longValue'e sahiptir. Paramn=xxx kullanın|
|[C28239](../code-quality/c28239.md)|Parametredeki ek açıklamanın hem değeri, hem stringValue'ı hem de uzun Değer vardır; ve paramn=xxx. Sadece paramn=xxx kullanın|
|[C28240](../code-quality/c28240.md)|Parametredeki ek açıklama param2'ye sahiptir, ancak param1|
|[C28241](../code-quality/c28241.md)|Parametredeki işlev inekliği tanınmaz|
|[C28243](../code-quality/c28243.md)|Parametredeki işlev ek açıklama, gerçek tür açıklamalı nın izin verdiğinden daha fazla dereferences gerektirir|
|[C28244](../code-quality/c28244.md)|İşlev için ek açıklama nın parsable parametresi/harici ek açıklama vardır|
|[C28245](../code-quality/c28245.md)|İşlev için ek açıklama, üye olmayan bir işlevde 'bu' ek açıklamalarını|
|[C28246](../code-quality/c28246.md)|İşlev için parametre ek açıklama parametre türü eşleşmiyor|
|[C28250](../code-quality/c28250.md)|İşlev için tutarsız ek açıklama: önceki örnekte bir hata vardır.|
|[C28251](../code-quality/c28251.md)|İşlev için tutarsız ek açıklama: Bu örnekte bir hata vardır.|
|[C28252](../code-quality/c28252.md)|İşlev için tutarsız ek açıklama: parametre bu örnekte başka ek açıklamalar vardır.|
|[C28253](../code-quality/c28253.md)|İşlev için tutarsız ek açıklama: parametre bu örnekte başka ek açıklamalar vardır.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() ek açıklamalar desteklenmez|
|[C28262](../code-quality/c28262.md)|Ek açıklamadaki sözdizimi hatası işlevde bulundu, ek açıklama için|
|[C28263](../code-quality/c28263.md)|İntrinsic ek açıklama için koşullu ek açıklamada sözdizimi hatası bulundu|
|[C28267](../code-quality/c28267.md)|Ek açıklamalarbir sözdizimi hatası işlevinde ek açıklama bulundu.|
|[C28272](../code-quality/c28272.md)|İşlev için ek açıklama, incelerken parametre işlev bildirimi ile tutarsız|
|[C28273](../code-quality/c28273.md)|İşlev için ipuçları işlev bildirimiile tutarsız|
|[C28275](../code-quality/c28275.md)|Makro \_\_değerine\_ parametre null|
|[C28279](../code-quality/c28279.md)|Sembol için, eşleşen bir 'bitiş' olmadan bir 'başlangıç' bulundu|
|[C28280](../code-quality/c28280.md)|Sembol için, eşleşen bir 'başlangıç' olmadan bir 'son' bulundu|
|[C28282](../code-quality/c28282.md)|Biçim Dizeleri ön koşulda olmalıdır|
|[C28285](../code-quality/c28285.md)|Fonksiyon için, parametrede sözdizimi hatası|
|[C28286](../code-quality/c28286.md)|İşlev için, sonuna yakın sözdizimi hatası|
|[C28287](../code-quality/c28287.md)|İşlev için, At \_\_() ek açıklama (tanınmayan parametre adı) sözdizimi Hatası|
|[C28288](../code-quality/c28288.md)|İşlev için, At \_\_() ek açıklama (geçersiz parametre adı) sözdizimi Hatası|
|[C28289](../code-quality/c28289.md)|Fonksiyon için: ReadableTo veya WritableTo parametre olarak bir limit-spec yoktu|
|[C28290](../code-quality/c28290.md)|fonksiyonuiçin ek açıklama parametrelerin gerçek sayısından daha fazla Hariciler içerir|
|[C28291](../code-quality/c28291.md)|deref düzeyinde null/notnull sonrası fonksiyon için anlamsızdır.|
|[C28300](../code-quality/c28300.md)|İşletici için uyumsuz türlerin ifade operands|
|[C28301](../code-quality/c28301.md)|İlk işlev bildirimi için ek açıklamalar yok.|
|[C28302](../code-quality/c28302.md)|Ek \_açıklama\_ üzerinde fazladan bir Deref operatörü bulundu.|
|[C28303](../code-quality/c28303.md)|Ek \_açıklama\_ üzerinde belirsiz bir Deref işleci bulundu.|
|[C28304](../code-quality/c28304.md)|Belirteci \_uygulanmış\_ bir yanlış yerleştirilmiş Notref işleci bulundu.|
|[C28305](../code-quality/c28305.md)|Bir belirteç ayrıştırken bir hata keşfedildi.|
|[C28306](../code-quality/c28306.md)|Parametredeki ek açıklama eskimiş|
|[C28307](../code-quality/c28307.md)|Parametredeki ek açıklama eskimiş|
|[C28350](../code-quality/c28350.md)|Ek açıklama, koşullu olarak geçerli olmayan bir durumu açıklar.|
|[C28351](/cpp/code-quality/c28351)|Ek açıklama, dinamik bir değerin (değişkenin) bu durumda kullanılamadığı yeri açıklar.|
