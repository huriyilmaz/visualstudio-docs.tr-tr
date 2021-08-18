---
title: Yönetilen kod için Genişletilmiş Tasarım Yönerge Kuralları kural kümesi
ms.date: 11/04/2016
description: Visual Studio'de kullanılabilirlik ve bakıma odaklanan Genişletilmiş Tasarım Yönergeleri Kuralları kural kümesi hakkında bilgi edinin. Kural açıklamalarını görme.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: d284dec49e0973f2781f00f178fa193b52797085
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075339"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genişletilmiş Tasarım Yönerge Kuralları kural kümesi

Microsoft Genişletilmiş Tasarım Kılavuz Kuralları kural kümesi, bildirilen kullanılabilirlik ve bakım sorunlarını en üst düzeye çıkarmak için temel tasarım kılavuzu kurallarını genişletmektedir. Adlandırma yönergelerine daha fazla vurgu yapıldı. Projeniz kitaplık koduna sahipse veya bakımı kolay kod yazmak için en yüksek standartları uygulamak istemiyorsanız bu kural kümesi dahil etmek düşünebilirsiniz.

Genişletilmiş Tasarım Kılavuz Kuralları, Temel Tasarım [](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) Kılavuz Kuralları kural kümesinde yer alan ve Yönetilen Önerilen Kurallar kural kümesinde yer alan kuralları [içeren tüm kuralları](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) içerir.

Aşağıdaki tabloda, Microsoft Genişletilmiş Tasarım Kılavuz Kuralları kural kümesinde yer alan tüm kurallar açıkılmıştır.

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
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Genel türlerde statik üyeler belirtme|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Genel listeleri gösterme|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Genel olay işleyicisi örnekleri kullan|
|[CA1004](../code-quality/ca1004.md)|Genel metotlar tür parametresi sağlamalıdır|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Genel türlerde aşırı parametre kullanmaktan kaçının|
|[CA1006](../code-quality/ca1006.md)|Üye imzalarında genel türleri iç içe kullanma|
|[CA1007](../code-quality/ca1007.md)|Uygun yerlerde genel türleri kullanın|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Koleksiyonlar genel arabirimi uygulamalıdır|
|[CA1011](../code-quality/ca1011.md)|Parametre olarak temel türleri geçmeyi düşünün|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Soyut türlerin oluşturucuları olmamalıdır|
|[CA1013](../code-quality/ca1013.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Derlemeleri CLSCompliantAttribute ile işaretle|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Derlemeleri ComVisibleAttribute ile işaretleyin|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Öznitelikleri AttributeUsageAttribute ile işaretle|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Öznitelik bağımsız değişkenleri için erişimciler tanımlayın|
|[CA1023](../code-quality/ca1023.md)|Dizin oluşturucular çok boyutlu olmamalıdır|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Uygun yerlerde özellikleri kullanın|
|[CA1025](../code-quality/ca1025.md)|Yinelenen bağımsız değişkenleri params dizisiyle değiştirin|
|[CA1026](../code-quality/ca1026.md)|Varsayılan parametreler kullanılmamalıdır|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Sabit listelerini FlagsAttribute ile işaretleyin|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Sabit listesi depolaması Int32 olmalıdır|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Uygun yerlerde olayları kullanın|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Genel özel durum türlerini yakalamayın|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Standart özel durum oluşturucularını uygulayın|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|İç içe türler görünür olmamalıdır|
|[CA1035](../code-quality/ca1035.md)|ICollection uygulamalarının kesin türde üyeleri vardır|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Karşılaştırılabilir türlerde metotları geçersiz kıl|
|[CA1038](../code-quality/ca1038.md)|Numaralandırıcıların kesin türü belirtilmiş olmalıdır|
|[CA1039](../code-quality/ca1039.md)|Listeler kesin türdedir|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|ObsoleteAttribute iletisi sağla|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Özellikler salt yazılır olmamalıdır|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Eşittir işlecini başvuru türlerinde aşırı yüklemeyin|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Sealed türlerde protected üyeler bildirmeyin|
|[CA1048](../code-quality/ca1048.md)|Sealed türlerde virtual üyeler bildirmeyin|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Ad alanlarında türler bildirin|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Görünür örnek alanlarını bildirmeyin|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Static tutucu türler sealed olmalıdır|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Static tutucu türlerin oluşturucuları olmamalıdır|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI parametreleri dize olmamalıdır|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI özellikleri dize olmamalıdır|
|[CA1057](../code-quality/ca1057.md)|String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Türler belirli temel türleri aşmamalıdır|
|[CA1059](../code-quality/ca1059.md)|Üyeler belirli somut türleri kullanıma sunmamalıdır|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Özel durumlar genel olmalıdır|
|[CA1500](../code-quality/ca1500.md)|Değişken adları alan adları ile eşleşmemelidir|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Aşırı karmaşıklıktan kaçının|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Kullanılmayan parametreleri gözden geçirin|
|[CA1804](../code-quality/ca1804.md)|Kullanılmayan yerelleri kaldırın|
|[CA1809](../code-quality/ca1809.md)|Aşırı yerellerden kaçının|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Başvuru türü statik alanları satır içinden başlatın|
|[CA1811](../code-quality/ca1811.md)|Çağırılmayan özel kodlardan kaçının|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Örneklenmemiş iç sınıflardan kaçının|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Mühürsüz özniteliklerden kaçının|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Çok boyutlu diziler yerine basit dizileri tercih edin|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Özellikler diziler döndürmemelidir|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Üyeleri static olarak işaretleyin|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Kullanılmayan özel alanlardan kaçının|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Ayrılmış özel durum türlerini harekete geçirmeyin|
|[CA2205](../code-quality/ca2205.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Bağımsız değişken özel durumlarını doğru örnekleyin|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2221](../code-quality/ca2221.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2230](../code-quality/ca2230.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2239](../code-quality/ca2239.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA1020](../code-quality/ca1020.md)|Az tür içeren ad alanlarından kaçının|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|out parametrelerinden kaçının|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|Boş arabirimlerden kaçının|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|Türleri başvuru olarak geçmeyin|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|Genel metotların bağımsız değişkenlerini doğrulayın|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|Aşırı devralmadan kaçının|
|[CA1504](../code-quality/ca1504.md)|Yanıltıcı alan adlarını gözden geçirin|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|Bakımı yapılamayan kodlardan kaçının|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|Aşırı sınıf bağlantısından kaçının|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|Sabit listesi değerlerini 'Reserved' olarak adlandırmayın|
|[CA1701](../code-quality/ca1701.md)|Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır|
|[CA1702](../code-quality/ca1702.md)|Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır|
|[CA1703](../code-quality/ca1703.md)|Kaynak dizeleri doğru yazılmalıdır|
|[CA1704](../code-quality/ca1704.md)|Tanımlayıcılar doğru yazılmalıdır|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|Tanımlayıcılar alt çizgi içermemelidir|
|[CA1709](../code-quality/ca1709.md)|Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|Tanımlayıcılar doğru soneke sahip olmalıdır|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|Tanımlayıcılar yanlış sonek içermemelidir|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|Sabit listesi değerlerine tür adını önek olarak eklemeyin|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|Olaylar önce ya da sonra önekine sahip olmamalıdır|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|Bayrak sabit listeleri çoğul adlara sahip olmalıdır|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|Tanımlayıcılar doğru ön eke sahip olmalıdır|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır|
|[CA1719](../code-quality/ca1719.md)|Parametre adları üye adları ile eşleşmemelidir|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|Tanımlayıcılar tür adları içermemelidir|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|Özellik adları get metotları ile eşleşmemelidir|
|[CA1722](../code-quality/ca1722.md)|Tanımlayıcılar yanlış ön ek içermemelidir|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|Tür adları ad alanları ile eşleşmemelidir|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|Parametre adları temel bildirimle eşleşmemelidir|
|[CA1726](../code-quality/ca1726.md)|Tercih edilen terimleri kullanın|
|[CA2204](../code-quality/ca2204.md)|Harfler doğru yazılmalıdır|
