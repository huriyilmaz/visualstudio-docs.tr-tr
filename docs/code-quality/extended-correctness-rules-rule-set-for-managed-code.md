---
title: Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3e4a0d05454e16be3ebe2832bae4316afdf61bb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649644"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi

Microsoft genişletilmiş doğruluk kuralları kural kümesi, kod analizi tarafından bildirilen mantık ve çerçeve kullanım hatalarını en üst düzeye çıkarır. Ek vurgu, COM birlikte çalışabilirlik ve mobil uygulamalar gibi belirli senaryolara yerleştirilir. Bu senaryolardan biri projeniz için geçerliyse veya projenizde ek sorunlar bulmak için bu kural kümesini dahil etmeyi göz önünde bulundurmanız gerekir.

Microsoft genişletilmiş doğruluk kuralları kural kümesi, [yönetilen önerilen kurallar](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) kural kümesindeki kuralları Içeren [temel doğruluk kuralları](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) kural kümesindeki kuralları içerir.

Aşağıdaki tabloda, Microsoft genişletilmiş doğruluk kuralları kural kümesindeki tüm kurallar açıklanmaktadır.

|Kural|Açıklama|
|----------|-----------------|
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
|[CA1008](../code-quality/ca1008.md)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1013](../code-quality/ca1013.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1303](../code-quality/ca1303.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1308](../code-quality/ca1308.md)|Dizeleri büyük harfe normalleştirin|
|[CA1806](../code-quality/ca1806.md)|Metot sonuçlarını yoksaymayın|
|[CA1816](../code-quality/ca1816.md)|GC.SuppressFinalize'ı doğru çağırın|
|[CA1819](../code-quality/ca1819.md)|Özellikler diziler döndürmemelidir|
|[CA1820](../code-quality/ca1820.md)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1903](../code-quality/ca1903.md)|Yalnızca hedeflenen çerçeveden API kullanın|
|[CA2004](../code-quality/ca2004.md)|GC.KeepAlive'a çağrıları kaldırın|
|[CA2006](../code-quality/ca2006.md)|Yerel kaynakları kapsamak için SafeHandle kullanın|
|[CA2102](../code-quality/ca2102.md)|CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın|
|[CA2104](../code-quality/ca2104.md)|Salt okunur kesilebilir başvuru türleri bildirmeyin|
|[CA2105](../code-quality/ca2105.md)|Dizi alanları salt okunur olmamalıdır|
|[CA2106](../code-quality/ca2106.md)|Onay deyimlerinin güvenliğini sağlayın|
|[CA2115](../code-quality/ca2115.md)|Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın|
|[CA2119](../code-quality/ca2119.md)|Özel arabirimleri karşılayan metotları mühürleyin|
|[CA2120](../code-quality/ca2120.md)|Serileştirme oluşturucularının güvenliğini sağlayın|
|[CA2121](../code-quality/ca2121.md)|Statik oluşturucular özel olmalıdır|
|[CA2130](../code-quality/ca2130.md)|Güvenlik kritik sabitleri saydam olmalıdır|
|[CA2205](../code-quality/ca2205.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2215](../code-quality/ca2215.md)|Atma metotları taban sınıf atmayı çağırmalıdır|
|[CA2221](../code-quality/ca2221.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2226](../code-quality/ca2226.md)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](../code-quality/ca2227.md)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2239](../code-quality/ca2239.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA1032](../code-quality/ca1032.md)|Standart özel durum oluşturucularını uygulayın|
|[CA1054](../code-quality/ca1054.md)|URI parametreleri dize olmamalıdır|
|[CA1055](../code-quality/ca1055.md)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](../code-quality/ca1056.md)|URI özellikleri dize olmamalıdır|
|[CA1057](../code-quality/ca1057.md)|String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır|
|[CA1402](../code-quality/ca1402.md)|COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının|
|[CA1406](../code-quality/ca1406.md)|Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının|
|[CA1407](../code-quality/ca1407.md)|COM görünebilir türler içinde statik üyelerden kaçının|
|[CA1408](../code-quality/ca1408.md)|AutoDual ClassInterFaceType kullanmayın|
|[CA1409](../code-quality/ca1409.md)|COM görünebilir türler oluşturulabilir olmalıdır|
|[CA1411](../code-quality/ca1411.md)|COM kayıt metotları görünebilir olmamalıdır|
|[CA1412](../code-quality/ca1412.md)|ComSource arabirimlerini IDispatch olarak işaretleyin|
|[CA1413](../code-quality/ca1413.md)|COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının|
|[CA1414](../code-quality/ca1414.md)|Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin|
|[CA1600](../code-quality/ca1600.md)|Boş işlem önceliğini kullanmayın|
|[CA1601](../code-quality/ca1601.md)|Güç durumu değişikliklerini önleyen zamanlayıcılar kullanmayın|
|[CA1824](../code-quality/ca1824.md)|Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin|
|[CA2001](../code-quality/ca2001.md)|Sorunlu metotları çağırmaktan kaçının|
|[CA2003](../code-quality/ca2003.md)|Fiberleri iş parçacığı olarak görmeyin|
|[CA2135](../code-quality/ca2135.md)|Düzey 2 derlemeler LinkDemands içermemelidir|
|[CA2136](../code-quality/ca2136.md)|Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır|
|[CA2139](../code-quality/ca2139.md)|Saydam metotlar HandleProcessCorruptingExceptions özniteliğini kullanamaz|
|[CA2142](../code-quality/ca2142.md)|Saydam kod LinkDemands ile korunmamalıdır|
|[CA2143](../code-quality/ca2143.md)|Saydam metotlar güvenlik taleplerini kullanmamalıdır|
|[CA2144](../code-quality/ca2144.md)|Saydam kod derlemeleri bayt dizilerinden yüklememelidir|
|[CA2145](../code-quality/ca2145.md)|Saydam metotlar SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır|
|[CA2204](../code-quality/ca2204.md)|Harfler doğru yazılmalıdır|
|[CA2211](../code-quality/ca2211.md)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](../code-quality/ca2217.md)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2218](../code-quality/ca2218.md)|GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın|
|[CA2219](../code-quality/ca2219.md)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2225](../code-quality/ca2225.md)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2228](../code-quality/ca2228.md)|Yayımlanmamış kaynak biçimlerini yollamayın|
|[CA2230](../code-quality/ca2230.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2233](../code-quality/ca2233.md)|İşleçler taşmamalıdır|
|[CA2234](../code-quality/ca2234.md)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2243](../code-quality/ca2243.md)|Öznitelik dize harfleri doğru çözümlenmelidir|
