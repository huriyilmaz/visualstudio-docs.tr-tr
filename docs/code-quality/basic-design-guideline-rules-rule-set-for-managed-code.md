---
title: Yönetilen kod için Temel Tasarım Yönerge Kuralları kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cf30e3294c1a96e64efd47ffd14f03328ebec62c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75573190"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Yönetilen kod için Temel Tasarım Yönerge Kuralları kural kümesi

Kodunuzun anlaşılması ve kullanılması daha kolay hale getirilmesi üzerine odaklanmak için Microsoft temel tasarım kılavuzu kuralları kural kümesini kullanabilirsiniz. Projeniz kitaplık kodu içeriyorsa veya bakımı kolay olan kod için en iyi yöntemleri zorlamak istiyorsanız bu kural kümesini dahil etmelisiniz.

Temel tasarım kılavuz kuralları, [yönetilen önerilen kurallar](managed-recommended-rules-rule-set-for-managed-code.md) kural kümesindeki tüm kuralları içerir.

Aşağıdaki tabloda, Microsoft temel tasarım kılavuzu kuralları kural kümesindeki tüm kurallar açıklanmaktadır.

|Kural|Description|
|----------|-----------------|
|[CA1000](../code-quality/ca1000.md)|Genel türlerde statik üyeler belirtme|
|[CA1001](../code-quality/ca1001.md)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1002](../code-quality/ca1002.md)|Genel listeleri gösterme|
|[CA1003](../code-quality/ca1003.md)|Genel olay işleyicisi örnekleri kullan|
|[CA1004](../code-quality/ca1004.md)|Genel metotlar tür parametresi sağlamalıdır|
|[CA1005](../code-quality/ca1005.md)|Genel türlerde aşırı parametre kullanmaktan kaçının|
|[CA1006](../code-quality/ca1006.md)|Üye imzalarında genel türleri iç içe kullanma|
|[CA1007](../code-quality/ca1007.md)|Uygun yerlerde genel türleri kullanın|
|[CA1008](../code-quality/ca1008.md)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1009](../code-quality/ca1009.md)|Olay işleyicileri doğru olarak bildirin|
|[CA1010](../code-quality/ca1010.md)|Koleksiyonlar genel arabirimi uygulamalıdır|
|[CA1011](../code-quality/ca1011.md)|Parametre olarak temel türleri geçmeyi düşünün|
|[CA1012](../code-quality/ca1012.md)|Soyut türlerin oluşturucuları olmamalıdır|
|[CA1013](../code-quality/ca1013.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1014](../code-quality/ca1014.md)|Derlemeleri CLSCompliantAttribute ile işaretle|
|[CA1016](../code-quality/ca1016.md)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|
|[CA1017](../code-quality/ca1017.md)|Derlemeleri ComVisibleAttribute ile işaretleyin|
|[CA1018](../code-quality/ca1018.md)|Öznitelikleri AttributeUsageAttribute ile işaretle|
|[CA1019](../code-quality/ca1019.md)|Öznitelik bağımsız değişkenleri için erişimciler tanımlayın|
|[CA1023](../code-quality/ca1023.md)|Dizin oluşturucular çok boyutlu olmamalıdır|
|[CA1024](../code-quality/ca1024.md)|Uygun yerlerde özellikleri kullanın|
|[CA1025](../code-quality/ca1025.md)|Yinelenen bağımsız değişkenleri params dizisiyle değiştirin|
|[CA1026](../code-quality/ca1026.md)|Varsayılan parametreler kullanılmamalıdır|
|[CA1027](../code-quality/ca1027.md)|Sabit listelerini FlagsAttribute ile işaretleyin|
|[CA1028](../code-quality/ca1028.md)|Sabit listesi depolaması Int32 olmalıdır|
|[CA1030](../code-quality/ca1030.md)|Uygun yerlerde olayları kullanın|
|[CA1031](../code-quality/ca1031.md)|Genel özel durum türlerini yakalamayın|
|[CA1032](../code-quality/ca1032.md)|Standart özel durum oluşturucularını uygulayın|
|[CA1033](../code-quality/ca1033.md)|Arabirim metotları alt türler tarafından çağrılabilmelidir|
|[CA1034](../code-quality/ca1034.md)|İç içe türler görünür olmamalıdır|
|[CA1035](../code-quality/ca1035.md)|ICollection uygulamalarının kesin türde üyeleri vardır|
|[CA1036](../code-quality/ca1036.md)|Karşılaştırılabilir türlerde metotları geçersiz kıl|
|[CA1038](../code-quality/ca1038.md)|Numaralandırıcıların kesin türü belirtilmiş olmalıdır|
|[CA1039](../code-quality/ca1039.md)|Listeler kesin türdedir|
|[CA1041](../code-quality/ca1041.md)|ObsoleteAttribute iletisi sağla|
|[CA1043](../code-quality/ca1043.md)|Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın|
|[CA1044](../code-quality/ca1044.md)|Özellikler salt yazılır olmamalıdır|
|[CA1046](../code-quality/ca1046.md)|Eşittir işlecini başvuru türlerinde aşırı yüklemeyin|
|[CA1047](../code-quality/ca1047.md)|Sealed türlerde protected üyeler bildirmeyin|
|[CA1048](../code-quality/ca1048.md)|Sealed türlerde virtual üyeler bildirmeyin|
|[CA1049](../code-quality/ca1049.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|
|[CA1050](../code-quality/ca1050.md)|Ad alanlarında türler bildirin|
|[CA1051](../code-quality/ca1051.md)|Görünür örnek alanlarını bildirmeyin|
|[CA1052](../code-quality/ca1052.md)|Static tutucu türler sealed olmalıdır|
|[CA1053](../code-quality/ca1053.md)|Static tutucu türlerin oluşturucuları olmamalıdır|
|[CA1054](../code-quality/ca1054.md)|URI parametreleri dize olmamalıdır|
|[CA1055](../code-quality/ca1055.md)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](../code-quality/ca1056.md)|URI özellikleri dize olmamalıdır|
|[CA1057](../code-quality/ca1057.md)|String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır|
|[CA1058](../code-quality/ca1058.md)|Türler belirli temel türleri aşmamalıdır|
|[CA1059](../code-quality/ca1059.md)|Üyeler belirli somut türleri kullanıma sunmamalıdır|
|[CA1060](../code-quality/ca1060.md)|P/Invokes'u NativeMethods sınıfına taşıyın|
|[CA1061](../code-quality/ca1061.md)|Temel sınıf metotlarını gizlemeyin|
|[CA1063](../code-quality/ca1063.md)|IDisposable'ı doğru uygulayın|
|[CA1064](../code-quality/ca1064.md)|Özel durumlar genel olmalıdır|
|[CA1065](../code-quality/ca1065.md)|Beklenmeyen konumlarda özel durum harekete geçirmeyin|
|[CA1301](../code-quality/ca1301.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](../code-quality/ca1401.md)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403.md)|Otomatik yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404.md)|P/Invoke ardından hemen GetLastError çağırın|
|[CA1405](../code-quality/ca1405.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410.md)|COM kayıt metotları eşleşmelidir|
|[CA1415](../code-quality/ca1415.md)|P/Invoke'ları doğru bildirin|
|[CA1500](../code-quality/ca1500.md)|Değişken adları alan adları ile eşleşmemelidir|
|[CA1502](../code-quality/ca1502.md)|Aşırı karmaşıklıktan kaçının|
|[CA1708](../code-quality/ca1708.md)|Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır|
|[CA1716](../code-quality/ca1716.md)|Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir|
|[CA1801](../code-quality/ca1801.md)|Kullanılmayan parametreleri gözden geçirin|
|[CA1804](../code-quality/ca1804.md)|Kullanılmayan yerelleri kaldırın|
|[CA1809](../code-quality/ca1809.md)|Aşırı yerellerden kaçının|
|[CA1810](../code-quality/ca1810.md)|Başvuru türü statik alanları satır içinden başlatın|
|[CA1811](../code-quality/ca1811.md)|Çağırılmayan özel kodlardan kaçının|
|[CA1812](../code-quality/ca1812.md)|Örneklenmemiş iç sınıflardan kaçının|
|[CA1813](../code-quality/ca1813.md)|Mühürsüz özniteliklerden kaçının|
|[CA1814](../code-quality/ca1814.md)|Çok boyutlu diziler yerine basit dizileri tercih edin|
|[CA1815](../code-quality/ca1815.md)|Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın|
|[CA1819](../code-quality/ca1819.md)|Özellikler diziler döndürmemelidir|
|[CA1820](../code-quality/ca1820.md)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1821](../code-quality/ca1821.md)|Boş sonlandırıcıları kaldırın|
|[CA1822](../code-quality/ca1822.md)|Üyeleri static olarak işaretleyin|
|[CA1823](../code-quality/ca1823.md)|Kullanılmayan özel alanlardan kaçının|
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
|[CA2201](../code-quality/ca2201.md)|Ayrılmış özel durum türlerini harekete geçirmeyin|
|[CA2202](../code-quality/ca2202.md)|Nesneleri birden çok kez atmayın|
|[CA2205](../code-quality/ca2205.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2207](../code-quality/ca2207.md)|Değer türü statik alanları satır içi başlatın|
|[CA2208](../code-quality/ca2208.md)|Bağımsız değişken özel durumlarını doğru örnekleyin|
|[CA2211](../code-quality/ca2211.md)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2212](../code-quality/ca2212.md)|Servis verilen bileşenleri WebMethod ile işaretlemeyin|
|[CA2213](../code-quality/ca2213.md)|Atılabilen alanlar atılmalıdır|
|[CA2214](../code-quality/ca2214.md)|Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın|
|[CA2216](../code-quality/ca2216.md)|Atılabilir türler sonlandırıcıyı bildirmelidir|
|[CA2217](../code-quality/ca2217.md)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2219](../code-quality/ca2219.md)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2220](../code-quality/ca2220.md)|Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır|
|[CA2221](../code-quality/ca2221.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2225](../code-quality/ca2225.md)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2226](../code-quality/ca2226.md)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](../code-quality/ca2227.md)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2229](../code-quality/ca2229.md)|Serileştirme oluşturucularını uygulayın|
|[CA2230](../code-quality/ca2230.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2231](../code-quality/ca2231.md)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|
|[CA2232](../code-quality/ca2232.md)|Windows Forms giriş noktalarını STAThread ile işaretleyin|
|[CA2234](../code-quality/ca2234.md)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2235](../code-quality/ca2235.md)|Tüm serileştirilebilir olmayan alanları işaretleyin|
|[CA2236](../code-quality/ca2236.md)|ISerializable türler üzerinde taban sınıf metotlarını çağırın|
|[CA2237](../code-quality/ca2237.md)|ISerializable türleri SerializableAttribute ile işaretleyin|
|[CA2238](../code-quality/ca2238.md)|Serileştirme metotlarını doğru uygulayın|
|[CA2239](../code-quality/ca2239.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA2240](../code-quality/ca2240.md)|ISerializable'ı doğru uygulayın|
|[CA2241](../code-quality/ca2241.md)|Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın|
|[CA2242](../code-quality/ca2242.md)|NaN için doğru test edin|
