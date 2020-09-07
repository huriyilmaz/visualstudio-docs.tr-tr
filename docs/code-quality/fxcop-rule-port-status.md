---
title: FxCop kural bağlantı noktası durumu
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508372"
---
# <a name="fxcop-rule-port-status"></a>FxCop kural bağlantı noktası durumu

Daha önce Visual Studio 'da statik Kod analizini kullandıysanız, bu kurallardan hangilerinin geçerli uygulamada [FxCop çözümleyicileri](install-fxcop-analyzers.md)olarak kullanılabildiğini merak ediyor olabilirsiniz. Bu sayfa, bir sayfada yer alan kuralları listeler. [Numaralandırmamaları](fxcop-unported-rules.md) ve bağlantı noktası ile ilgili planlar olup olmadığı hakkında bilgi için bkz. eksik kurallar.

## <a name="ported-rules"></a>Taşınan kurallar

Roslyn-çözümleyiciler depolarındaki otomatik olarak oluşturulan [Belgeler sayfasında](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) , FxCop çözümleyicileri ' nin içinde yer alan kuralların en güncel listesi bulunur. Bu sayfada Ayrıca kuralın varsayılan olarak etkinleştirilip etkinleştirilmeyeceğini ve ilişkili bir *kod düzeltmesine*sahip olup olmadığı gibi ek bilgiler de bulunur. ([Kod düzeltmeleri](../ide/quick-actions.md) , Visual Studio 'da ampul simgesi menüsünde sunulan tek tıklamayla düzeltmeler ' dir.)

Bu sayfadaki tarihin itibariyle, [FxCop çözümleyicileri](install-fxcop-analyzers.md) 'nin kapsamında yer alan FxCop kuralları listesi şunları içerir:

Kural Kimliği | Başlık
--------|---------
[CA1000](ca1000.md) | Genel türlerde statik üyeler belirtme
[CA1001](ca1001.md) | Atılabilen alanlara sahip türler atılabilir olmalıdır
[CA1002](ca1002.md) | Genel listeleri gösterme
[CA1003](ca1003.md) | Genel olay işleyicisi örnekleri kullan
[CA1005](ca1005.md) | Genel türlerde aşırı parametre kullanmaktan kaçının
[CA1008](ca1008.md) | Sabit listelerinin sıfır değeri olmalıdır
[CA1010](ca1010.md) | Koleksiyonlar genel arabirimi uygulamalıdır
[CA1012](ca1012.md) | Soyut türlerin oluşturucuları olmamalıdır
[CA1014](ca1014.md) | Derlemeleri CLSCompliant ile işaretle
[CA1016](ca1016.md) | Derlemeleri derleme sürümü ile işaretle
[CA1017](ca1017.md) | Derlemeleri ComVisible ile işaretle
[CA1018](ca1018.md) | Öznitelikleri AttributeUsageAttribute ile işaretle
[CA1019](ca1019.md) | Öznitelik bağımsız değişkenleri için erişimciler tanımlayın
[CA1021](ca1021.md) | out parametrelerinden kaçının
[CA1024](ca1024.md) | Uygun yerlerde özellikleri kullanın
[CA1027](ca1027.md) | Sabit listelerini FlagsAttribute ile işaretleyin
[CA1028](ca1028.md) | Sabit Listesi depolaması Int32 olmalıdır
[CA1030](ca1030.md) | Uygun yerlerde olayları kullanın
[CA1031](ca1031.md) | Genel özel durum türlerini yakalamayın
[CA1032](ca1032.md) | Standart özel durum oluşturucularını uygulayın
[CA1033](ca1033.md) | Arabirim metotları alt türler tarafından çağrılabilmelidir
[CA1034](ca1034.md) | İç içe türler görünür olmamalıdır
[CA1036](ca1036.md) | Karşılaştırılabilir türlerde metotları geçersiz kıl
[CA1040](ca1040.md) | Boş arabirimlerden kaçının
[CA1041](ca1041.md) | ObsoleteAttribute iletisi sağla
[CA1043](ca1043.md) | Dizin oluşturucular Için Integral veya dize bağımsız değişkeni kullanın
[CA1044](ca1044.md) | Özellikler salt yazılır olmamalıdır
[CA1045](ca1045.md) | Türleri başvuru olarak geçmeyin
[CA1046](ca1046.md) | Eşittir işlecini başvuru türlerinde aşırı yüklemeyin
[CA1047](ca1047.md) | Sealed türlerde protected üyeler bildirmeyin
[CA1050](ca1050.md) | Ad alanlarında türler bildirin
[CA1051](ca1051.md) | Görünür örnek alanlarını bildirmeyin
[CA1052](ca1052.md) | Statik tutucu türleri statik veya NotInheritable olmalıdır
[CA1053](ca1053.md) | Statik tutucu türlerin oluşturucuları olmamalıdır (CA1053, FxCop çözümleyicileri için [CA1052](ca1052.md) 'in bir parçasıdır)
[CA1054](ca1054.md) | URI parametreleri dize olmamalıdır
[CA1055](ca1055.md) | URI dönüş değerleri dize olmamalıdır
[CA1056](ca1056.md) | URI özellikleri dize olmamalıdır
[CA1058](ca1058.md) | Türler belirli temel türleri aşmamalıdır
[CA1060](ca1060.md) | PInvoke 'ı yerel metotlar sınıfına taşı
[CA1061](ca1061.md) | Temel sınıf metotlarını gizlemeyin
[CA1062](ca1062.md) | Genel metotların bağımsız değişkenlerini doğrulayın
[CA1063](ca1063.md) | IDisposable 'ı doğru uygulayın
[CA1064](ca1064.md) | Özel durumlar genel olmalıdır
[CA1065](ca1065.md) | Beklenmeyen konumlarda özel durum harekete geçirmeyin
[CA1066](ca1066.md) | Tür, {0} eşit olarak \<T> geçersiz kılındığından IEquatable uygulamalıdır
[CA1067](ca1067.md) | IEquatable uygularken Object. Equals (nesne) öğesini geçersiz kıl\<T>
[CA1303](ca1303.md) | Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[CA1304](ca1304.md) | CultureInfo belirt
[CA1305](ca1305.md) | IFormatProvider belirt
[CA1307](ca1307.md) | Açıklık için StringComparison belirtin
[CA1308](ca1308.md) | Dizeleri büyük harfe normalleştirin
[CA1309](ca1309.md) | Sıralı dize karşılaştırmayı kullan
[CA1401](ca1401.md) | P/Invoke'lar görünür olmamalıdır
[CA1501](ca1501.md) | Aşırı devralmadan kaçının
[CA1502](ca1502.md) | Aşırı karmaşıklıktan kaçının
[CA1505](ca1505.md) | Bakımı yapılamayan kodlardan kaçının
[CA1506](ca1506.md) | Aşırı sınıf bağlantısından kaçının
[CA1700](ca1700.md) | Sabit listesi değerlerini 'Reserved' olarak adlandırmayın
[CA1707](ca1707.md) | Tanımlayıcılar alt çizgi içermemelidir
[CA1708](ca1708.md) | Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır
[CA1710](ca1710.md) | Tanımlayıcılar doğru soneke sahip olmalıdır
[CA1711](ca1711.md) | Tanımlayıcılar yanlış sonek içermemelidir
[CA1712](ca1712.md) | Sabit listesi değerlerine tür adını önek olarak eklemeyin
[CA1713](ca1713.md) | Olaylar önce ya da sonra önekine sahip olmamalıdır
[CA1714](ca1714.md) | Bayrak sabit listeleri çoğul adlara sahip olmalıdır
[CA1715](ca1715.md) | Tanımlayıcılar doğru ön eke sahip olmalıdır
[CA1716](ca1716.md) | Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir
[CA1717](ca1717.md) | Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır
[CA1720](ca1720.md) | Tanımlayıcı tür adı içeriyor
[CA1721](ca1721.md) | Özellik adları get metotları ile eşleşmemelidir
[CA1724](ca1724.md) | Tür adları ad alanlarıyla eşleşmemelidir
[CA1725](ca1725.md) | Parametre adları temel bildirimle eşleşmemelidir
[CA1801](ca1801.md) | Kullanılmayan parametreleri gözden geçirin
[CA1802](ca1802.md) | Uygun yerlerde sabit değerler kullanın
[CA1805](ca1805.md) | Gereksiz yere başlatma
[CA1806](ca1806.md) | Metot sonuçlarını yoksaymayın
[CA1810](ca1810.md) | Başvuru türü statik alanları satır içinden başlatın
[CA1812](ca1812.md) | Örneklenmemiş iç sınıflardan kaçının
[CA1813](ca1813.md) | Mühürsüz özniteliklerden kaçının
[CA1814](ca1814.md) | Çok boyutlu diziler yerine basit dizileri tercih edin
[CA1815](ca1815.md) | Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın
[CA1816](ca1816.md) | Dispose metotları SuppressFinalize öğesini çağırmalıdır
[CA1819](ca1819.md) | Özellikler diziler döndürmemelidir
[CA1820](ca1820.md) | Dize uzunluğunu kullanarak boş dizeleri test edin
[CA1821](ca1821.md) | Boş sonlandırıcıları kaldır
[CA1822](ca1822.md) | Üyeleri static olarak işaretleyin
[CA1823](ca1823.md) | Kullanılmayan özel alanlardan kaçının
[CA1824](ca1824.md) | Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin
[CA1825](ca1825.md) | Sıfır uzunluklu dizi ayırmaktan kaçının.
[CA2000](ca2000.md) | Kapsamı kaybetmeden önce nesneleri bırakın
[CA2002](ca2002.md) | Zayıf kimliği olan nesneleri kilitlemeyin
[CA2100](ca2100.md) | SQL sorgularını güvenlik açıkları için inceleyin
[CA2101](ca2101.md) | P/Invoke dize bağımsız değişkenleri için sıralama belirtin
[CA2109](ca2109.md) | Görünen olay işleyicilerini gözden geçirin
[CA2119](ca2119.md) | Özel arabirimleri karşılayan metotları mühürleyin
[CA2153](ca2153.md) | Bozuk durum özel durumlarını yakalamayın
[CA2200](ca2200.md) | Yığın ayrıntılarını korumak için yeniden throw.
[CA2201](ca2201.md) | Ayrılmış özel durum türlerini harekete geçirmeyin
[CA2207](ca2207.md) | Değer türü statik alanları satır içi başlatın
[CA2208](ca2208.md) | Bağımsız değişken özel durumlarını doğru örnekleyin
[CA2211](ca2211.md) | Sabit olmayan alanlar görünür olmamalıdır
[CA2213](ca2213.md) | Atılabilen alanlar atılmalıdır
[CA2214](ca2214.md) | Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın
[CA2215](ca2215.md) | Atma metotları taban sınıf atmayı çağırmalıdır
[CA2216](ca2216.md) | Atılabilir türler sonlandırıcıyı bildirmelidir
[CA2217](ca2217.md) | Sabit listelerini FlagsAttribute ile işaretlemeyin
[CA2219](ca2219.md) | Finally yan tümcelerinde özel durum yükseltmeyin
[CA2225](ca2225.md) | İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir
[CA2226](ca2226.md) | İşleçler simetrik aşırı yüklemelere sahip olmalıdır
[CA2227](ca2227.md) | Koleksiyon özellikleri salt okunur olmalıdır
[CA2229](ca2229.md) | Serileştirme oluşturucularını uygulayın
[CA2231](ca2231.md) | Eşittir değer türü geçersiz kılan aşırı yükleme işleci eşittir
[CA2234](ca2234.md) | Dizeler yerine sistem URI nesnelerini geçirme
[CA2235](ca2235.md) | Tüm serileştirilebilir olmayan alanları işaretleyin
[CA2237](ca2237.md) | ISerializable türlerini seri hale getirilebilir ile işaretle
[CA2241](ca2241.md) | Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın
[CA2242](ca2242.md) | NaN için doğru test edin
[CA2243](ca2243.md) | Öznitelik dize harfleri doğru çözümlenmelidir
[CA2300](ca2300.md) | Güvenli olmayan seri durumdan çıkarıcı BinaryFormatter kullanmayın
[CA2301](ca2301.md) | İlk olarak BinaryFormatter.Binder öğesini ayarlamadan önce BinaryFormatter.Deserialize çağırmayın
[CA2302](ca2302.md) | BinaryFormatter.Deserialize çağırmadan önce BinaryFormatter.Binder öğesinin ayarlandığından emin olun
[CA2305](ca2305.md) | Güvenli olmayan seri kaldırıcı LosFormatter kullanmayın
[CA2310](ca2310.md) | Güvenli olmayan seri kaldırıcı NetDataContractSerializer kullanmayın
[CA2311](ca2311.md) | İlk olarak NetDataContractSerializer.Binder öğesini ayarlamadan seri durumdan çıkarmayın
[CA2312](ca2312.md) | Seri durumdan çıkarmadan önce NetDataContractSerializer.Binder öğesinin ayarlandığından emin olun
[CA2315](ca2315.md) | Güvenli olmayan seri kaldırıcı ObjectStateFormatter kullanmayın
[CA2321](ca2321.md) | SimpleTypeResolver kullanarak JavaScriptSerializer ile seri durumdan çıkarmayın
[CA2322](ca2322.md) | Seri durumdan çıkarmadan önce SimpleTypeResolver ile JavaScriptSerializer’ın başlatılmadığından emin olun
[CA3001](ca3001.md) | SQL ekleme güvenlik açıkları için inceleme kodu
[CA3002](ca3002.md) | XSS güvenlik açıkları için inceleme kodu
[CA3003](ca3003.md) | Dosya yolu ekleme güvenlik açıkları için inceleme kodu
[CA3004](ca3004.md) | Bilgilerin açığa çıkmasıyla ilgili güvenlik açıkları için inceleme kodu
[CA3005](ca3005.md) | LDAP ekleme güvenlik açıkları için inceleme kodu
[CA3006](ca3006.md) | İşlem komutu ekleme güvenlik açıkları için inceleme kodu
[CA3007](ca3007.md) | Açık yeniden yönlendirme güvenlik açıkları için inceleme kodu
[CA3008](ca3008.md) | XPath ekleme güvenlik açıkları için inceleme kodu
[CA3009](ca3009.md) | XML ekleme güvenlik açıkları için inceleme kodu
[CA3010](ca3010.md) | XAML ekleme güvenlik açıkları için inceleme kodu
[CA3011](ca3011.md) | DLL ekleme güvenlik açıkları için inceleme kodu
[CA3012](ca3012.md) | Normal ifade ekleme güvenlik açıkları için inceleme kodu
[CA3061](ca3061.md) | URL 'ye göre şema eklemeyin
[CA3075](ca3075.md) | XML 'de güvenli olmayan DTD işleme
[CA3076](ca3076.md) | Güvenli olmayan XSLT betiği işleme.
[CA3077](ca3077.md) | API tasarımında, XmlDocument 'da ve XmlTextReader 'da güvenli olmayan Işlem
[CA3147](ca3147.md) | Fiil Işleyicilerini Validate Antiforgery belirteci Ile işaretle
[CA5350](ca5350.md) | Zayıf Şifreleme Algoritmaları Kullanmayın
[CA5351](ca5351.md) | Bozuk şifreleme algoritmaları kullanmayın
[CA5358](ca5358.md) | Güvenli Olmayan Şifreleme Modlarını Kullanmayın
CA5359 | Sertifika doğrulamasını devre dışı bırakma
CA5360 | Seri durumdan çıkarma sırasında tehlikeli yöntemleri çağırmayın
[CA5361](ca5361.md) | Sağlam şifreleme için SChannel kullanımını devre dışı bırakma
CA5362 | Kendisini seri hale getirilebilir sınıfta başvurma
[CA5363](ca5363.md) | Istek doğrulamasını devre dışı bırakma
[CA5364](ca5364.md) | Kullanım dışı güvenlik protokollerini kullanma
CA5365 | HTTP üstbilgi denetimini devre dışı bırakma
CA5366 | DataSet Için XmlReader kullanarak XML okuma
CA5367 | Işaretçi alanları Ile türleri Serileştirmeyin
CA5368 | Sayfadan türetilmiş sınıflar Için ViewStateUserKey ayarla
[CA5369](ca5369.md) | Seri durumdan çıkarma Için XmlReader kullanın
[CA5370](ca5370.md) | Okuyucuyu doğrulamak Için XmlReader kullanın
[CA5371](ca5371.md) | Şema okuma Için XmlReader kullanın
[CA5372](ca5372.md) | XPathDocument Için XmlReader kullanın
[CA5373](ca5373.md) | Eski anahtar türetme işlevini kullanmayın
CA5374 | XslTransform kullanma
CA5375 | Hesap paylaşılan erişim Imzasını kullanma
CA5376 | SharedAccessProtocol HttpsOnly kullanın
CA5377 | Kapsayıcı düzeyinde erişim Ilkesi kullan
[CA5378](ca5378.md) | ServicePointManagerSecurityProtocols'u Devre Dışı Bırakma
CA5379 | Zayıf anahtar türetme Işlevi algoritması kullanmayın
CA9999 | Çözümleyici sürümü uyumsuzluğu

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft. CodeAnalysis. Fxcopçözümleyiciler kuralları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
