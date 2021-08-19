---
title: Yönetilen kod için Temel Doğruluk Kuralları kural kümesi
ms.date: 11/04/2016
description: Mantıksal hatalara ve yaygın çerçeve API'si hatalarına Visual Studio Temel Doğruluk Kuralları kural kümesi hakkında bilgi edinin. Kural açıklamalarını görme.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 02c7b660c6aba7f25e631a14146582f08c3d5117
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155154"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Yönetilen kod için Temel Doğruluk Kuralları kural kümesi

Temel Doğruluk Kuralları kural kümesi, çerçeve API'lerinin kullanımında mantık hatalarına ve yaygın hatalara odaklanır. Temel Doğruluk Kuralları, Yönetilen Önerilen Kurallar [kural kümesinde yer alan](managed-recommended-rules-rule-set-for-managed-code.md) kuralları içerir.

Aşağıdaki tabloda Microsoft Temel Doğruluk Kuralları kural kümesinde yer alan tüm kurallar açıkılmıştır.

|Kural|Açıklama|
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
