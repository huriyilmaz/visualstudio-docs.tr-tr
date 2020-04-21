---
title: Yerel Minimum Kurallar kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8abf4d4c5d2158ab4a3c9deeb11ab93e31b4cc3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649347"
---
# <a name="native-minimum-rules-rule-set"></a>Yerel Minimum Kurallar kural kümesi

Microsoft Yerel Minimum Kuralları, olası güvenlik açıkları ve uygulama çökmeleri de dahil olmak üzere yerel koddaki en kritik sorunlara odaklanır.

Yerel projeler için oluşturduğunuz herhangi bir özel kural kümesine ayarlanan bu kuralı ekleyin.

|Kural|Açıklama|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Başharfsiz Bellek Kullanma|
|[C6011](../code-quality/c6011.md)|Null Pointer'ı Dereferencing|
|[C6029](../code-quality/c6029.md)|İşaretlenmemiş Değerin Kullanımı|
|[C6053](../code-quality/c6053.md)|Çağrıdan Sıfır Sonlandırma|
|[C6059](../code-quality/c6059.md)|Kötü Concatenation|
|[C6063](../code-quality/c6063.md)|İşlev biçimlendirmek için eksik string bağımsız değişkeni|
|[C6064](../code-quality/c6064.md)|İşlev biçimlendirmek için Eksik Sonda Bağımsız Değişkeni|
|[C6066](../code-quality/c6066.md)|İşlev biçimlendirmek için işaretçi bağımsız değişkeni eksik|
|[C6067](../code-quality/c6067.md)|İşlev biçimlendirmek için String Pointer bağımsız değişkeni eksik|
|[C6101](../code-quality/c6101.md)|Başharfe getirilmemiş belleği döndürme|
|[C6200](../code-quality/c6200.md)|Dizin Arabellek Maksimumu Aşıyor|
|[C6201](../code-quality/c6201.md)|Dizin Yığın Arabellek Maksimum aşıyor|
|[C6270](../code-quality/c6270.md)|İşlev biçimlendirmek için Float bağımsız değişkeni eksik|
|[C6271](../code-quality/c6271.md)|İşlev biçimlendirmek için ekstra bağımsız değişken|
|[C6272](../code-quality/c6272.md)|İşlev biçimlendirmek için Float olmayan bağımsız değişken|
|[C6273](../code-quality/c6273.md)|İşlev biçimlendirmek için Non-Integer Bağımsız Değişkeni|
|[C6274](../code-quality/c6274.md)|Işlevi biçimlendirmek için karakter dışı bağımsız değişken|
|[C6276](../code-quality/c6276.md)|Geçersiz Yaylı Çalgılar Döküm|
|[C6277](../code-quality/c6277.md)|Geçersiz CreateProcess Çağrısı|
|[C6284](../code-quality/c6284.md)|Geçersiz Nesne Bağımsız Değişkeni İşlev biçimlendirmek için|
|[C6290](../code-quality/c6290.md)|Mantıksal-BitWise değil-Ve Öncelik|
|[C6291](../code-quality/c6291.md)|Mantıksal-BitWise-Veya Öncelik değil|
|[C6302](../code-quality/c6302.md)|Geçersiz Karakter String Bağımsız Değişkeni Biçimlendirme İşlev|
|[C6303](../code-quality/c6303.md)|Geçersiz Geniş Karakter Dize Bağımsız Değişkeni İşlev biçimlendirmek için|
|[C6305](../code-quality/c6305.md)|Uyumsuz Boyut Ve Sayım Kullanımı|
|[C6306](../code-quality/c6306.md)|Yanlış Değişken Bağımsız Değişken İşlev Çağrısı|
|[C6328](../code-quality/c6328.md)|Potansiyel Bağımsız Değişken Türü Uyuşmazlığı|
|[C6385](../code-quality/c6385.md)|Oku Overrun|
|[C6386](../code-quality/c6386.md)|Overrun yaz|
|[C6387](../code-quality/c6387.md)|Geçersiz Parametre Değeri|
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
|[C26450](../code-quality/c26450.md)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](../code-quality/c26451.md)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](../code-quality/c26452.md)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](../code-quality/c26453.md)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](../code-quality/c26454.md)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](../code-quality/c26495.md)|MEMBER_UNINIT|
|[C28021](../code-quality/c28021.md)|Açıklamalı olan parametre bir işaretçi olmalıdır|
|[C28182](../code-quality/c28182.md)|NULL işaretçisini dereferencing. İşaretçi, başka bir işaretçiyle aynı NULL değerini içerir.|
|[C28202](../code-quality/c28202.md)|Statik olmayan üyeye yasa dışı başvuru|
|[C28203](../code-quality/c28203.md)|Sınıf üyesine belirsiz başvuru.|
|[C28205](../code-quality/c28205.md)|\_Başarı\_ \_veya\_\_ Yasadışı bir bağlamda kullanılan başarısızlık|
|[C28206](../code-quality/c28206.md)|Sol operand noktaları bir yapı, '->' kullanın|
|[C28207](../code-quality/c28207.md)|Sol operand bir yapı, kullanın '.'|
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
|[C28350](../code-quality/c28350.md)|Ek açıklama, koşullu olarak geçerli olmayan bir durumu açıklar.|
|[C28351](/cpp/code-quality/c28351)|Ek açıklama, dinamik bir değerin (değişkenin) bu durumda kullanılamadığı yeri açıklar.|
