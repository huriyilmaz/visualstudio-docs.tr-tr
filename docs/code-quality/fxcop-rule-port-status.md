---
title: FxCop kuralı bağlantı noktası durumu
ms.date: 05/21/2019
description: Veri analizinde .NET çözümleyicilere taşınabilir statik kod analizi kuralları hakkında Visual Studio. Güncelleştirmeleri taşınabilirlik üzerinde bağlantı noktası olan kuralları ve kaynakları görüntüleme.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 8445e7fa26fb8beef7452a53b3e4733bcfc43f47
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632025"
---
# <a name="fxcop-rule-port-status"></a>Fxcop kuralı bağlantı noktası durumu

Daha önce statik kod analizini Visual Studio, geçerli uygulamada .NET çözümleyicileri olarak hangi kuralların kullanılabilir [olduğunu merak ediyor olabilir.](install-net-analyzers.md) Bu sayfada, bağlantı noktası olan kurallar listeledik. Bağlantı noktası henüz bağlantı noktasılanmamış kurallar ve bunları bağlantı noktasıyla bağlantı noktası olarak kabul etme planları olup olmadığını görmek için bkz. [Unported](fxcop-unported-rules.md) rules for that been ported.

## <a name="ported-rules"></a>Taşınan kurallar

[Roslyn](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) çözümleyicileri'nin otomatik olarak yenilenmiş belge sayfasında, Roslyn çözümleyicileri'ne bağlantı noktası olan kuralların en güncel listesi yer almaktadır. Bu sayfada ayrıca kuralın varsayılan olarak etkin olup olmadığı ve ilişkili bir kod düzeltmesi olup olmadığı gibi ek *bilgiler de vardır.* ([Kod düzeltmeleri,](../ide/quick-actions.md) uygulamanın ampul simgesi menüsünde tek tıklamayla Visual Studio.)

Bu sayfada yer alan tarihten itibaren [.NET](install-net-analyzers.md) çözümleyicileri için bağlantı noktası olan FxCop kurallarının listesi şunları içerir:

Kural Kimliği | Başlık
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | Genel türlerde statik üyeler belirtme
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | Atılabilen alanlara sahip türler atılabilir olmalıdır
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | Genel listeleri gösterme
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | Genel olay işleyicisi örnekleri kullan
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | Genel türlerde aşırı parametre kullanmaktan kaçının
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | Sabit listelerinin sıfır değeri olmalıdır
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | Koleksiyonlar genel arabirimi uygulamalıdır
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | Soyut türlerin oluşturucuları olmamalıdır
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | Derlemeleri CLSCompliant ile işaretleme
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | Derlemeleri derleme sürümüyle işaretleme
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | Derlemeleri ComVisible ile işaretleme
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | Öznitelikleri AttributeUsageAttribute ile işaretle
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | Öznitelik bağımsız değişkenleri için erişimciler tanımlayın
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | out parametrelerinden kaçının
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | Uygun yerlerde özellikleri kullanın
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | Sabit listelerini FlagsAttribute ile işaretleyin
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | Enum Depolama Int32 olması gerekir
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | Uygun yerlerde olayları kullanın
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | Genel özel durum türlerini yakalamayın
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | Standart özel durum oluşturucularını uygulayın
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | Arabirim metotları alt türler tarafından çağrılabilmelidir
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | İç içe türler görünür olmamalıdır
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | Karşılaştırılabilir türlerde metotları geçersiz kıl
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | Boş arabirimlerden kaçının
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | ObsoleteAttribute iletisi sağla
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | Dizinciler için Tamsayı veya Dize Bağımsız Değişkeni Kullanma
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | Özellikler salt yazılır olmamalıdır
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | Türleri başvuru olarak geçmeyin
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | Eşittir işlecini başvuru türlerinde aşırı yüklemeyin
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | Sealed türlerde protected üyeler bildirmeyin
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | Ad alanlarında türler bildirin
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | Görünür örnek alanlarını bildirmeyin
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | Statik tutucu türler statik veya NotInheritable olmalıdır
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | Statik tutucu türlerin oluşturucuları olmalıdır (CA1053, .NET çözümleyicileri için [CA1052'nin](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) bir parçası)
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Uri parametreleri dizeler olmalıdır
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Uri dönüş değerleri dizeler değildir
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Uri özellikleri dizeler değildir
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | Türler belirli temel türleri aşmamalıdır
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | Pinvokes'ları yerel yöntemler sınıfına taşıma
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | Temel sınıf metotlarını gizlemeyin
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | Genel metotların bağımsız değişkenlerini doğrulayın
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | IDisposable'i Doğru Uygulama
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | Özel durumlar genel olmalıdır
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | Beklenmeyen konumlarda özel durum harekete geçirmeyin
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | Tür, {0} Equals'i geçersiz kılarak IEquatable \<T> uygulamalı
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | IEquatable uygulanırken Object.Equals(object) geçersiz kılın\<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | CultureInfo belirt
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | IFormatProvider belirt
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | Netlik için StringComparison belirtme
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | Dizeleri büyük harfe normalleştirin
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | Ordinal dize karşılaştırması kullanma
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | P/Invoke'lar görünür olmamalıdır
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | Aşırı devralmadan kaçının
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | Aşırı karmaşıklıktan kaçının
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | Bakımı yapılamayan kodlardan kaçının
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | Aşırı sınıf bağlantısından kaçının
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | Sabit listesi değerlerini 'Reserved' olarak adlandırmayın
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | Tanımlayıcılar alt çizgi içermemelidir
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | Tanımlayıcılar doğru soneke sahip olmalıdır
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | Tanımlayıcılar yanlış sonek içermemelidir
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | Sabit listesi değerlerine tür adını önek olarak eklemeyin
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | Olaylar önce ya da sonra önekine sahip olmamalıdır
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | Bayrak sabit listeleri çoğul adlara sahip olmalıdır
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | Tanımlayıcılar doğru ön eke sahip olmalıdır
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | Tanımlayıcı, tür adını içerir
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | Özellik adları get metotları ile eşleşmemelidir
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | Tür adları ad alanlarıyla eşleşmez
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | Parametre adları temel bildirimle eşleşmemelidir
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | Kullanılmayan parametreleri gözden geçirin
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | Uygun olduğunda değişmez değişmezleri kullanın
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | Gereksiz bir şekilde başlat
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | Metot sonuçlarını yoksaymayın
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | Başvuru türü statik alanları satır içinden başlatın
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | Örneklenmemiş iç sınıflardan kaçının
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | Mühürsüz özniteliklerden kaçının
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | Çok boyutlu diziler yerine basit dizileri tercih edin
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Dispose yöntemleri SuppressFinalize çağrısında bulundurarak
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | Özellikler diziler döndürmemelidir
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | Dize uzunluğunu kullanarak boş dizeleri test edin
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | Boş Sonlandırıcıları kaldırma
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | Üyeleri static olarak işaretleyin
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | Kullanılmayan özel alanlardan kaçının
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | Sıfır uzunluklu dizi ayırmalarından kaçının.
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | Kapsamı kaybetmeden önce nesneleri bırakın
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | Zayıf kimliği olan nesneleri kilitlemeyin
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | SQL sorgularını güvenlik açıkları için inceleyin
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | P/Invoke dize bağımsız değişkenleri için sıralama belirtin
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | Görünen olay işleyicilerini gözden geçirin
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | Özel arabirimleri karşılayan metotları mühürleyin
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | Bozuk Durum Özel Durumlarını Yakalama
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | Yığın ayrıntılarını korumak için yeniden kullanın.
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | Ayrılmış özel durum türlerini harekete geçirmeyin
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | Değer türü statik alanları satır içi başlatın
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | Bağımsız değişken özel durumlarını doğru örnekleyin
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | Sabit olmayan alanlar görünür olmamalıdır
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | Atılabilen alanlar atılmalıdır
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Atma metotları taban sınıf atmayı çağırmalıdır
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | Atılabilir türler sonlandırıcıyı bildirmelidir
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | Sabit listelerini FlagsAttribute ile işaretlemeyin
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | Finally yan tümceleri içinde özel durumlar yükseltilmez
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | İşleçler simetrik aşırı yüklemelere sahip olmalıdır
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | Koleksiyon özellikleri salt okunur olmalıdır
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | Serileştirme oluşturucularını uygulayın
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | Eşittir değer türünü geçersiz kılmada eşittir işlecinin aşırı yüklenmesi
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | Dizeler yerine sistem uri nesnelerini geçme
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | Tüm serileştirilebilir olmayan alanları işaretleyin
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | ISerializable türlerini serileştirilebilir ile işaretleme
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | NaN için doğru test edin
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | Öznitelik dize harfleri doğru çözümlenmelidir
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | Güvenli olmayan seri durumdan çıkarıcı BinaryFormatter kullanmayın
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | İlk olarak BinaryFormatter.Binder öğesini ayarlamadan önce BinaryFormatter.Deserialize çağırmayın
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | BinaryFormatter.Deserialize çağırmadan önce BinaryFormatter.Binder öğesinin ayarlandığından emin olun
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | Güvenli olmayan seri kaldırıcı LosFormatter kullanmayın
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | Güvenli olmayan seri kaldırıcı NetDataContractSerializer kullanmayın
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | İlk olarak NetDataContractSerializer.Binder öğesini ayarlamadan seri durumdan çıkarmayın
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | Seri durumdan çıkarmadan önce NetDataContractSerializer.Binder öğesinin ayarlandığından emin olun
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | Güvenli olmayan seri kaldırıcı ObjectStateFormatter kullanmayın
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | SimpleTypeResolver kullanarak JavaScriptSerializer ile seri durumdan çıkarmayın
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | Seri durumdan çıkarmadan önce SimpleTypeResolver ile JavaScriptSerializer’ın başlatılmadığından emin olun
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | SQL ekleme güvenlik açıkları için inceleme kodu
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | XSS güvenlik açıkları için inceleme kodu
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | Dosya yolu ekleme güvenlik açıkları için inceleme kodu
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | Bilgilerin açığa çıkmasıyla ilgili güvenlik açıkları için inceleme kodu
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | LDAP ekleme güvenlik açıkları için inceleme kodu
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | İşlem komutu ekleme güvenlik açıkları için inceleme kodu
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | Açık yeniden yönlendirme güvenlik açıkları için inceleme kodu
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | XPath ekleme güvenlik açıkları için inceleme kodu
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | XML ekleme güvenlik açıkları için inceleme kodu
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | XAML ekleme güvenlik açıkları için inceleme kodu
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | DLL ekleme güvenlik açıkları için inceleme kodu
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | Normal ifade ekleme güvenlik açıkları için inceleme kodu
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | URL'ye Göre Şema Ekleme
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | XML'de güvenli olmayan DTD işleme
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | Güvenli olmayan XSLT betik işleme.
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | API Design, XmlDocument ve XmlTextReader'da Güvenli Olmayan İşleme
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | Sahteciliği Doğrulama Belirteci ile Fiil İşleyicilerini İşaretle
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | Zayıf Şifreleme Algoritmaları Kullanmayın
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | Bozuk Şifreleme Algoritmaları Kullanma
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | Güvenli Olmayan Şifreleme Modlarını Kullanmayın
CA5359 | Sertifika Doğrulamayı Devre Dışı Bırakma
CA5360 | Deserialization'da Tehlikeli Yöntemler Çağırma
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | Güçlü Şifrelemenin SChannel Kullanımını Devre Dışı Bırakma
CA5362 | Seri hale getirilebilir sınıfta kendine başvur
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | İstek doğrulamayı devre dışı bırakmayın
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | Kullanım Dışı Güvenlik Protokollerini Kullanma
CA5365 | HTTP Üst Bilgisi Denetlemeyi Devre Dışı Bırakma
CA5366 | DataSet Read Xml için XmlReader Kullanma
CA5367 | İşaretçi alanlarıyla türleri seri hale getirme
CA5368 | Sayfadan türetilen sınıflar için ViewStateUserKey ayarlama
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | Deserialize için XmlReader kullanma
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | Okuyucuyu Doğrulama için XmlReader Kullanma
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | Şema Okuma için XmlReader kullanma
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | XPathDocument için XmlReader kullanma
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | Eski anahtar türetme işlevini kullanmayın
CA5374 | XslTransform Kullanma
CA5375 | Hesap Paylaşılan Erişim İmzası Kullanma
CA5376 | SharedAccessProtocol HttpsOnly kullanma
CA5377 | Kapsayıcı Düzeyinde Erişim İlkesi Kullanma
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | ServicePointManagerSecurityProtocols'u Devre Dışı Bırakma
CA5379 | Zayıf Anahtar Türetme İşlevi Algoritması Kullanma
CA9999 | Çözümleyici sürümü eşleşmez

## <a name="see-also"></a>Ayrıca bkz.

- [.NET çözümleyicisi kuralları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
