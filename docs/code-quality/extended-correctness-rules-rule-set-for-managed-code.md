---
title: Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi
ms.date: 11/04/2016
description: Com ile birlikte çalışabilirlik ve mobil uygulamalar için Visual Studio Genişletilmiş Doğruluk Kuralları kural kümesi hakkında bilgi edinebilirsiniz. Kural açıklamalarını görme.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: a664b01f5fec771f4891389d3ec807d2e4976797
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632031"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi

Microsoft Genişletilmiş Doğruluk Kuralları kural kümesi, kod analizi tarafından bildirilen mantık ve çerçeve kullanım hatalarını en üst düzeye çıkartır. COM birlikte çalışabilirliği ve mobil uygulamalar gibi belirli senaryolara ek olarak vurgulanır. Bu senaryolardan biri projeniz için geçerli ise veya projenize ek sorunlar bulmak için bu kural kümesi dahil etmek düşün gerekir.

Microsoft Genişletilmiş Doğruluk Kuralları kural kümesi, Yönetilen [](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) Önerilen Kurallar kural kümesinde yer alan kuralları içeren Temel Doğruluk Kuralları kural [kümesinde yer](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) alan kuralları içerir.

Aşağıdaki tabloda Microsoft Genişletilmiş Doğruluk Kuralları kural kümesinde yer alan tüm kurallar açıkılmıştır.

|Kural|Description|
|----------|-----------------|
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
|[CA2141](../code-quality/ca2141.md)|Saydam yöntemler LinkDemands'ı karşılamamalı|
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
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1013](../code-quality/ca1013.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Dizeleri büyük harfe normalleştirin|
|[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806)|Metot sonuçlarını yoksaymayın|
|[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816)|GC.SuppressFinalize'ı doğru çağırın|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Özellikler diziler döndürmemelidir|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1903](../code-quality/ca1903.md)|Yalnızca hedeflenen çerçeveden API kullanın|
|[CA2004](../code-quality/ca2004.md)|GC.KeepAlive'a çağrıları kaldırın|
|[CA2006](../code-quality/ca2006.md)|Yerel kaynakları kapsamak için SafeHandle kullanın|
|[CA2102](../code-quality/ca2102.md)|CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın|
|[CA2104](../code-quality/ca2104.md)|Salt okunur kesilebilir başvuru türleri bildirmeyin|
|[CA2105](../code-quality/ca2105.md)|Dizi alanları salt okunur olmamalıdır|
|[CA2106](../code-quality/ca2106.md)|Onay deyimlerinin güvenliğini sağlayın|
|[CA2115](../code-quality/ca2115.md)|Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Özel arabirimleri karşılayan metotları mühürleyin|
|[CA2120](../code-quality/ca2120.md)|Serileştirme oluşturucularının güvenliğini sağlayın|
|[CA2121](../code-quality/ca2121.md)|Statik oluşturucular özel olmalıdır|
|[CA2130](../code-quality/ca2130.md)|Güvenlik kritik sabitleri saydam olmalıdır|
|[CA2205](../code-quality/ca2205.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215)|Atma metotları taban sınıf atmayı çağırmalıdır|
|[CA2221](../code-quality/ca2221.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2239](../code-quality/ca2239.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Standart özel durum oluşturucularını uygulayın|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI parametreleri dize olmamalıdır|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI özellikleri dize olmamalıdır|
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
|[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824)|Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin|
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
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2218](../code-quality/ca2218.md)|GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2228](../code-quality/ca2228.md)|Yayımlanmamış kaynak biçimlerini yollamayın|
|[CA2230](../code-quality/ca2230.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2233](../code-quality/ca2233.md)|İşleçler taşmamalıdır|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243)|Öznitelik dize harfleri doğru çözümlenmelidir|
