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
ms.openlocfilehash: 84b37bce062ec5f1f406bc6ef9f6507399820af9
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82189482"
---
# <a name="fxcop-rule-port-status"></a>FxCop kural bağlantı noktası durumu

Daha önce Visual Studio 'da statik Kod analizini kullandıysanız, bu kurallardan hangilerinin geçerli uygulamada [FxCop çözümleyicileri](install-fxcop-analyzers.md)olarak kullanılabildiğini merak ediyor olabilirsiniz. Bu sayfada, bir yuva yapılan kuralların yanı sıra, bağlantı noktası ile ilgili planlar olup olmadığı listelenmiştir.

## <a name="ported-rules"></a>Taşınan kurallar

Roslyn-çözümleyiciler depolarındaki otomatik olarak oluşturulan [Belgeler sayfasında](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) , FxCop çözümleyicileri ' nin içinde yer alan kuralların en güncel listesi bulunur. Bu sayfada Ayrıca kuralın varsayılan olarak etkinleştirilip etkinleştirilmeyeceğini ve ilişkili bir *kod düzeltmesine*sahip olup olmadığı gibi ek bilgiler de bulunur. ([Kod düzeltmeleri](../ide/quick-actions.md) , Visual Studio 'da ampul simgesi menüsünde sunulan tek tıklamayla düzeltmeler ' dir.)

Bu sayfadaki tarihin itibariyle, [FxCop çözümleyicileri](install-fxcop-analyzers.md) 'nin kapsamında yer alan FxCop kuralları listesi şunları içerir:

Kural Kimliği | Başlık
--------|---------
[CA1000](ca1000.md) | Genel türlerde statik üyeler belirtme
[CA1001](ca1001.md) | Atılabilen alanlara sahip türler atılabilir olmalıdır
[CA1003](ca1003.md) | Genel olay işleyicisi örnekleri kullan
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
[CA1066](ca1066.md) | Tür {0} , eşit olarak\<geçersiz kılındığından IEquatable T> uygulamalıdır
[CA1067](ca1067.md) | IEquatable\<T> uygularken Object. Equals (nesne) öğesini geçersiz kıl
[CA1068](ca1068.md) | CancellationToken parametreleri en sonda olmalıdır
CA1200 | cref etiketlerini ön ek ile kullanmaktan kaçının
[CA1303](ca1303.md) | Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[CA1304](ca1304.md) | CultureInfo belirt
[CA1305](ca1305.md) | IFormatProvider belirt
[CA1307](ca1307.md) | StringComparison belirt
[CA1308](ca1308.md) | Dizeleri büyük harfe normalleştirin
[CA1309](ca1309.md) | Sıralı dize karşılaştırmayı kullan
[CA1401](ca1401.md) | P/Invoke'lar görünür olmamalıdır
[CA1501](ca1501.md) | Aşırı devralmadan kaçının
[CA1502](ca1502.md) | Aşırı karmaşıklıktan kaçının
[CA1505](ca1505.md) | Bakımı yapılamayan kodlardan kaçının
[CA1506](ca1506.md) | Aşırı sınıf bağlantısından kaçının
[CA1507](ca1507.md) | Sembol adlarını ifade etmek için NameOf kullanın
[CA1508](ca1508.md) | Kullanılmayan koşullu koddan kaçının
CA1509 | Kod ölçümleri kural belirtim dosyasında geçersiz giriş
[CA1707](ca1707.md) | Tanımlayıcılar alt çizgi içermemelidir
[CA1708](ca1708.md) | Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır
[CA1710](ca1710.md) | Tanımlayıcılar doğru soneke sahip olmalıdır
[CA1711](ca1711.md) | Tanımlayıcılar yanlış sonek içermemelidir
[CA1712](ca1712.md) | Sabit listesi değerlerine tür adını önek olarak eklemeyin
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
CA1826 | Dizine eklenebilir koleksiyonlar üzerinde sıralanabilir Yöntemler kullanmayın. Bunun yerine toplamayı doğrudan kullanın
[CA2000](ca2000.md) | Kapsamı kaybetmeden önce nesneleri bırakın
[CA2002](ca2002.md) | Zayıf kimliği olan nesneleri kilitlemeyin
[CA2007](ca2007.md) | Beklenen görevde ConfigureAwait yöntemini çağırmayı düşünün
CA2008 | TaskScheduler geçirmeden görev oluşturmayın
CA2009 | IBir ımmutablecollection değerinde ToImmutableCollection çağırmayın
CA2010 | PreserveSigAttribute ile işaretlenmiş yöntemlerin döndürdüğü değeri her zaman kullanın
[CA2100](ca2100.md) | SQL sorgularını güvenlik açıkları için inceleyin
[CA2101](ca2101.md) | P/Invoke dize bağımsız değişkenleri için sıralama belirtin
[CA2119](ca2119.md) | Özel arabirimleri karşılayan metotları mühürleyin
[CA2153](ca2153.md) | Bozuk durum özel durumlarını yakalamayın
[CA2200](ca2200.md) | Yığın ayrıntılarını korumak için yeniden throw.
[CA2201](ca2201.md) | Ayrılmış özel durum türlerini harekete geçirmeyin
[CA2207](ca2207.md) | Değer türü statik alanları satır içi başlatın
[CA2208](ca2208.md) | Bağımsız değişken özel durumlarını doğru örnekleyin
[CA2211](ca2211.md) | Sabit olmayan alanlar görünür olmamalıdır
[CA2213](ca2213.md) | Atılabilen alanlar atılmalıdır
[CA2214](ca2214.md) | Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın
[CA2216](ca2216.md) | Atılabilir türler sonlandırıcıyı bildirmelidir
[CA2217](ca2217.md) | Sabit listelerini FlagsAttribute ile işaretlemeyin
[CA2218](ca2218.md) | GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın
[CA2219](ca2219.md) | Finally yan tümcelerinde özel durum yükseltmeyin
[CA2224](ca2224.md) | Aşırı yükleme işlecinin eşittir ile eşittir geçersiz kıl
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
CA2244 | Dizini oluşturulmuş öğe başlatmaları yinelenmeyin
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

## <a name="unported-rules"></a>Bağlantı edilmemiş kurallar

[FxCop çözümleyicilerine](install-fxcop-analyzers.md) eklenmemiş kuralların kümesi, henüz bir [yandan hala bir yandan da](#rules-that-may-be-ported)kaldırılmayan ve bu [öğelerden çıkılmamış](#deprecated-rules)olan kurallardan oluşur.

### <a name="rules-that-may-be-ported"></a>Bağlantı halinde olabilecek kurallar

Aşağıdaki FxCop eski analiz kuralları henüz çözümleyiciler olarak uygulanmadı, ancak yine de olabilir. Bunun nedeni, bir engelleme teknik nedeni veya kuralın daha düşük öncelikli olması olabilir. Her kuralın taşıma durumu hakkında daha fazla bilgi için, **izleme sorunu** sütunundaki bağlantıya tıklayın.

Kural Kimliği | Sorun izleniyor
--- | ---
[CA1002](ca1002.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>Kullanım dışı kurallar

Aşağıdaki FxCop eski analiz kuralları kullanım dışıdır ve çözümleyiciler olarak uygulanmaz. Daha fazla bilgi için, [Roslyn-çözümleyiciler GitHub sorunları sayfasında](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port)kural kimliğine göre arama yapabilirsiniz (örneğin, **CA1009**).

- [CA1009](ca1009.md)
- [CA1020](ca1020.md)
- [CA1025](ca1025.md)
- [CA1026](ca1026.md)
- [CA1035](ca1035.md)
- [CA1038](ca1038.md)
- [CA1039](ca1039.md)
- [CA1059](ca1059.md)
- [CA1302](ca1302.md)
- [CA1400](ca1400.md)
- [CA1406](ca1406.md)
- [CA1504](ca1504.md)
- [CA1701](ca1701.md)
- [CA1702](ca1702.md)
- [CA1703](ca1703.md)
- [CA1800](ca1800.md)
- [CA1809](ca1809.md)
- [CA1901](ca1901.md)
- [CA1903](ca1903.md)
- [CA2003](ca2003.md)
- [CA2102](ca2102.md)
- [CA2103](ca2103.md)
- [CA2104](ca2104.md)
- [CA2105](ca2105.md)
- [CA2106](ca2106.md)
- [CA2107](ca2107.md)
- [CA2108](ca2108.md)
- [CA2111](ca2111.md)
- [CA2112](ca2112.md)
- [CA2114](ca2114.md)
- [CA2115](ca2115.md)
- [CA2116](ca2116.md)
- [CA2117](ca2117.md)
- [CA2118](ca2118.md)
- [CA2120](ca2120.md)
- [CA2121](ca2121.md)
- [CA2122](ca2122.md)
- [CA2123](ca2123.md)
- [CA2124](ca2124.md)
- [CA2126](ca2126.md)
- [CA2130](ca2130.md)
- [CA2131](ca2131.md)
- [CA2132](ca2132.md)
- [CA2133](ca2133.md)
- [CA2134](ca2134.md)
- [CA2135](ca2135.md)
- [CA2136](ca2136.md)
- [CA2137](ca2137.md)
- [CA2138](ca2138.md)
- [CA2139](ca2139.md)
- [CA2140](ca2140.md)
- [CA2141](ca2141.md)
- [CA2142](ca2142.md)
- [CA2143](ca2143.md)
- [CA2144](ca2144.md)
- [CA2145](ca2145.md)
- [CA2146](ca2146.md)
- [CA2147](ca2147.md)
- [CA2149](ca2149.md)
- [CA2151](ca2151.md)
- [CA2202](ca2202.md)
- [CA2210](ca2210.md)
- [CA2220](ca2220.md)
- [CA2221](ca2221.md)
- [CA2222](ca2222.md) ([gerekçe](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft. CodeAnalysis. Fxcopçözümleyiciler kuralları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
