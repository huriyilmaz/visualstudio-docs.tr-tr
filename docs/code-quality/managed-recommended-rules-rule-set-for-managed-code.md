---
title: Yönetilen kod için Yönetilen Önerilen Kurallar kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 875f6b3aba88fa3786e4c303f23072e586c4848d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587348"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Yönetilen kod için Yönetilen Önerilen Kurallar kural kümesi

Olası güvenlik delikleri, uygulama kilitlenmesi ve diğer önemli mantık ve tasarım hataları da dahil olmak üzere, yönetilen kodunuzda en kritik sorunlara odaklanmak için Microsoft tarafından yönetilen Önerilen Kurallar kural kümesini kullanın. Bu kural kümesi, [yönetilen minimum kurallar](managed-minimum-rules-rule-set-for-managed-code.md) kural kümesindeki tüm kuralları içerir.

Bu kuralı, projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine ekleyin.

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
