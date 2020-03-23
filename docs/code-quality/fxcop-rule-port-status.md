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
ms.openlocfilehash: fccd167bfafd4c27895b01927aaabc1e77eab91c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303213"
---
# <a name="fxcop-rule-port-status"></a>Fxcop kural bağlantı noktası durumu

Daha önce Visual Studio statik kod analizi kullandıysanız, bu kurallardan hangisinin [FxCop analizörleri](install-fxcop-analyzers.md)olarak geçerli uygulamada mevcut olduğunu merak ediyor olabilirsiniz. Bu sayfa, taşınan kuralların yanı sıra taşımamış kuralları ve taşıma planları olup olmadığını listeler.

## <a name="ported-rules"></a>Taşınan kurallar

Roslyn-analyzers repo'daki [otomatik leştirilmiş dokümantasyon sayfası,](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) FxCop analizörlerine taşınan kuralların en güncel listesine sahiptir. Bu sayfada, kuralın varsayılan olarak etkinolup olmadığı ve ilişkili bir *kod düzeltmesi*olup olmadığı gibi ek bilgiler de vardır. ( Kod düzeltmeleri Visual Studio'daki ampul simgesi menüsünde bulunan tek tıklamayla[düzeltmelerdir.)](../ide/quick-actions.md)

Bu sayfadaki tarih itibariyle, [FxCop analizörlerine](install-fxcop-analyzers.md) taşınan FxCop kurallarının listesi şunları içerir:

Kural Kimliği | Başlık
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | Genel türlerde statik üyeler belirtme
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Atılabilen alanlara sahip türler atılabilir olmalıdır
[CA1003](ca1003-use-generic-event-handler-instances.md) | Genel olay işleyicisi örnekleri kullan
[CA1008](ca1008-enums-should-have-zero-value.md) | Sabit listelerinin sıfır değeri olmalıdır
[CA1010](ca1010-collections-should-implement-generic-interface.md) | Koleksiyonlar genel arabirimi uygulamalıdır
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | Soyut türlerin oluşturucuları olmamalıdır
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | CLSCompliant ile derlemeleri işaretleme
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | Derleme sürümü yle derlemeleri işaretleme
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | ComVisible ile derlemeleri işaretleme
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | Öznitelikleri AttributeUsageAttribute ile işaretle
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | Öznitelik bağımsız değişkenleri için erişimciler tanımlayın
[CA1021](ca1021.md) | out parametrelerinden kaçının
[CA1024](ca1024-use-properties-where-appropriate.md) | Uygun yerlerde özellikleri kullanın
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | Sabit listelerini FlagsAttribute ile işaretleyin
[CA1028](ca1028-enum-storage-should-be-int32.md) | Enum Depolama Int32 olmalıdır
[CA1030](ca1030-use-events-where-appropriate.md) | Uygun yerlerde olayları kullanın
[CA1031](ca1031-do-not-catch-general-exception-types.md) | Genel özel durum türlerini yakalamayın
[CA1032](ca1032-implement-standard-exception-constructors.md) | Standart özel durum oluşturucularını uygulayın
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | Arabirim metotları alt türler tarafından çağrılabilmelidir
[CA1034](ca1034-nested-types-should-not-be-visible.md) | İç içe türler görünür olmamalıdır
[CA1036](ca1036-override-methods-on-comparable-types.md) | Karşılaştırılabilir türlerde metotları geçersiz kıl
[CA1040](ca1040-avoid-empty-interfaces.md) | Boş arabirimlerden kaçının
[CA1041](ca1041-provide-obsoleteattribute-message.md) | ObsoleteAttribute iletisi sağla
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | Dizinleyiciler için İntegral Veya String Bağımsız Değişkeni Kullanma
[CA1044](ca1044-properties-should-not-be-write-only.md) | Özellikler salt yazılır olmamalıdır
[CA1050](ca1050-declare-types-in-namespaces.md) | Ad alanlarında türler bildirin
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | Görünür örnek alanlarını bildirmeyin
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | Statik tutucu türleri statik veya Devredilemez olmalıdır
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | Statik tutucu türlerinde yapıcı olmamalıdır (CA1053 FxCop analizörleri için [CA1052'nin](ca1052-static-holder-types-should-be-sealed.md) bir parçasıdır)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Uri parametreleri dizeli olmamalıdır
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Uri dönüş değerleri dizeleri olmamalıdır
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Uri özellikleri dizeleri olmamalıdır
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | Türler belirli temel türleri aşmamalıdır
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | Pinvokes'i yerel yöntemler sınıfına taşıma
[CA1061](ca1061-do-not-hide-base-class-methods.md) | Temel sınıf metotlarını gizlemeyin
[CA1062](ca1062-validate-arguments-of-public-methods.md) | Genel metotların bağımsız değişkenlerini doğrulayın
[CA1063](ca1063-implement-idisposable-correctly.md) | IDisposable'ı Doğru Uygula
[CA1064](ca1064-exceptions-should-be-public.md) | Özel durumlar genel olmalıdır
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Beklenmeyen konumlarda özel durum harekete geçirmeyin
CA1066 | Eşitleri geçersiz kıldığı için IEquatable {0} \<T> yazmalıdır
CA1067 | Object.Equals(object) IEquatable\<T> uygularken geçersiz kılın
[CA1068](ca1068.md) | CancellationToken parametreleri en sonda olmalıdır
CA1200 | cref etiketlerini ön ek ile kullanmaktan kaçının
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[CA1304](ca1304-specify-cultureinfo.md) | CultureInfo belirt
[CA1305](ca1305-specify-iformatprovider.md) | IFormatProvider belirt
[CA1307](ca1307-specify-stringcomparison.md) | StringComparison belirt
[CA1308](ca1308-normalize-strings-to-uppercase.md) | Dizeleri büyük harfe normalleştirin
[CA1309](ca1309-use-ordinal-stringcomparison.md) | Ordinal string karşılaştırması kullanın
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | P/Invoke'lar görünür olmamalıdır
[CA1501](ca1501-avoid-excessive-inheritance.md) | Aşırı devralmadan kaçının
[CA1502](ca1502-avoid-excessive-complexity.md) | Aşırı karmaşıklıktan kaçının
[CA1505](ca1505-avoid-unmaintainable-code.md) | Bakımı yapılamayan kodlardan kaçının
[CA1506](ca1506-avoid-excessive-class-coupling.md) | Aşırı sınıf bağlantısından kaçının
[CA1507](ca1507.md) | Sembol adlarını ifade etmek için ad kullanma
CA1508 | Ölü koşullu koddan kaçının
CA1509 | Kod ölçümleri kural belirtimi dosyasında geçersiz giriş
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | Tanımlayıcılar alt çizgi içermemelidir
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | Tanımlayıcılar doğru soneke sahip olmalıdır
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | Tanımlayıcılar yanlış sonek içermemelidir
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | Sabit listesi değerlerine tür adını önek olarak eklemeyin
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | Bayrak sabit listeleri çoğul adlara sahip olmalıdır
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | Tanımlayıcılar doğru ön eke sahip olmalıdır
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | Tanımlayıcı tür adı içerir
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | Özellik adları get metotları ile eşleşmemelidir
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | Tür adları ad boşluklarıyla eşleşmemelidir
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | Parametre adları temel bildirimle eşleşmemelidir
[CA1801](ca1801.md) | Kullanılmayan parametreleri gözden geçirin
[CA1802](ca1802.md) | Uygun olduğunda edebi kullanım
[CA1806](ca1806.md) | Metot sonuçlarını yoksaymayın
[CA1810](ca1810.md) | Başvuru türü statik alanları satır içinden başlatın
[CA1812](ca1812.md) | Örneklenmemiş iç sınıflardan kaçının
[CA1813](ca1813.md) | Mühürsüz özniteliklerden kaçının
[CA1814](ca1814.md) | Çok boyutlu diziler yerine basit dizileri tercih edin
[CA1815](ca1815.md) | Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın
[CA1816](ca1816.md) | Bertaraf yöntemleri SuppressFinalize çağırmalıdır
[CA1819](ca1819.md) | Özellikler diziler döndürmemelidir
[CA1820](ca1820.md) | Dize uzunluğunu kullanarak boş dizeleri test edin
[CA1821](ca1821.md) | Boş Finalizers kaldırın
[CA1822](ca1822.md) | Üyeleri static olarak işaretleyin
[CA1823](ca1823.md) | Kullanılmayan özel alanlardan kaçının
[CA1824](ca1824.md) | Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin
CA1825 | Sıfır uzunlukta dizi ayırmalarından kaçının.
CA1826 | Dizinlenebilir koleksiyonlarda Sayısal yöntemler kullanmayın. Bunun yerine koleksiyonu doğrudan kullanın
[CA2000](ca2000.md) | Kapsamı kaybetmeden önce nesneleri bırakın
[CA2002](ca2002.md) | Zayıf kimliği olan nesneleri kilitlemeyin
[CA2007](ca2007.md) | Beklenen görevde YapılandırmaBekle'yi aramayı düşünün
CA2008 | Görev Zamanlayıcısı'nı geçmeden görev oluşturmayın
CA2009 | DeğişmezKoleksiyon değerinde ToImmutableCollection'ı aramayın
CA2010 | Her zaman PreserveSigAttribute ile işaretlenmiş yöntemlerle döndürülen değeri tüketin
[CA2100](ca2100.md) | SQL sorgularını güvenlik açıkları için inceleyin
[CA2101](ca2101.md) | P/Invoke dize bağımsız değişkenleri için sıralama belirtin
[CA2119](ca2119.md) | Özel arabirimleri karşılayan metotları mühürleyin
[CA2153](ca2153.md) | Bozuk Durum Özel Durum Larını Yakalama
[CA2200](ca2200.md) | Yığın ayrıntılarını korumak için yeniden atın.
[CA2201](ca2201.md) | Ayrılmış özel durum türlerini harekete geçirmeyin
[CA2207](ca2207.md) | Değer türü statik alanları satır içi başlatın
[CA2208](ca2208.md) | Bağımsız değişken özel durumlarını doğru örnekleyin
[CA2211](ca2211.md) | Sabit olmayan alanlar görünür olmamalıdır
[CA2213](ca2213.md) | Atılabilen alanlar atılmalıdır
[CA2214](ca2214.md) | Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın
[CA2216](ca2216.md) | Atılabilir türler sonlandırıcıyı bildirmelidir
[CA2217](ca2217.md) | Sabit listelerini FlagsAttribute ile işaretlemeyin
[CA2218](ca2218.md) | GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın
[CA2219](ca2219.md) | Son maddelerde özel durum lar artma
[CA2224](ca2224.md) | Overloading işleci eşittir Override Eşittir
[CA2225](ca2225.md) | İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir
[CA2226](ca2226.md) | İşleçler simetrik aşırı yüklemelere sahip olmalıdır
[CA2227](ca2227.md) | Koleksiyon özellikleri salt okunur olmalıdır
[CA2229](ca2229.md) | Serileştirme oluşturucularını uygulayın
[CA2231](ca2231.md) | Aşırı yük işleci geçersiz kılma değer türü Eşittir eşittir eşittir
[CA2234](ca2234.md) | Geçiş sistemi uri nesneleri yerine dizeleri
[CA2235](ca2235.md) | Tüm serileştirilebilir olmayan alanları işaretleyin
[CA2237](ca2237.md) | Serializable ile İşaretI ISerializable türleri
[CA2241](ca2241.md) | Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın
[CA2242](ca2242.md) | NaN için doğru test edin
[CA2243](ca2243.md) | Öznitelik dize harfleri doğru çözümlenmelidir
CA2244 | Dizinlenmiş öğe başlatmalarını çoğaltma
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
CA3061 | ŞEma'yı URL'ye Göre Eklemeyin
[CA3075](ca3075.md) | XML'de güvensiz DTD işleme
[CA3076](ca3076.md) | Güvensiz XSLT komut dosyası işleme.
[CA3077](ca3077.md) | API Tasarım, XmlDocument ve XmlTextReader'da Güvensiz İşleme
[CA3147](ca3147.md) | Antiforgery Token'i Doğrulayan Fiil Handleyicis'i Işaretle
[CA5350](ca5350.md) | Zayıf Şifreleme Algoritmaları Kullanmayın
[CA5351](ca5351.md) | Kırık Şifreleme Algoritmaları Kullanmayın
CA5358 | Güvenli Olmayan Şifreleme Modlarını Kullanmayın
CA5359 | Sertifika Doğrulamayı Devre Dışı Bırakma
CA5360 | Deserialization Tehlikeli Yöntemler Arama etmeyin
CA5361 | Güçlü Kripto SChannel Kullanımını Devre Dışı Etmeyin
CA5362 | Serializable Sınıfında Kendini Tanıtma
CA5363 | İstek Doğrulamayı Devre Dışı Bırakma
CA5364 | Amortismana Karşı Güvenlik Protokolleri Kullanmayın
CA5365 | HTTP Üstbilgi Denetimini Devre Dışı Etmeyin
CA5366 | DataSet Read Xml için XmlReader'ı kullanın
CA5367 | İşaretçi Alanlarıyla Türleri Serileştirme
CA5368 | Sayfadan Türetilen Sınıflar Için ViewStateUserKey'i Ayarlama
CA5369 | Deserialize için XmlReader kullanın
CA5370 | Okuyucu doğrulama için XmlReader kullanın
CA5371 | Schema Read için XmlReader kullanın
CA5372 | XPathDocument için XmlReader kullanın
CA5373 | Eski anahtar türetme işlevini kullanmayın
CA5374 | XslTransform kullanmayın
CA5375 | Hesap Paylaşılan Erişim İmzası Kullanmayın
CA5376 | SharedAccessProtocol'u kullanma httpsOnly
CA5377 | Kapsayıcı Düzeyi Erişim İlkesi'ni Kullanma
CA5378 | ServicePointManagerSecurityProtocols'u Devre Dışı Bırakma
CA5379 | Zayıf Anahtar Türetme Fonksiyonu Algoritması Kullanmayın
CA99999 | Çözümleyici sürüm uyuşmazlığı

## <a name="unported-rules"></a>Atılamayan kurallar

[FxCop analizörleri](install-fxcop-analyzers.md) için taşınan değil kurallar kümesi henüz değil ama yine de [taşınabilir olabilir](#rules-that-may-be-ported)kurallar oluşur , ve bu amortismana ve taşınan [olmayacaktır](#deprecated-rules).

### <a name="rules-that-may-be-ported"></a>Taşınabilir kurallar

Aşağıdaki FxCop eski analiz kuralları henüz çözümleyici olarak uygulanmamıştır, ancak yine de olabilir. Bunun nedeni, engelleme teknik bir neden veya sadece kural daha düşük öncelik olması olabilir. Her kuralın taşıma durumu hakkında daha fazla bilgi için **İzleme sorunu** sütunundaki bağlantıyı tıklatın.

Kural Kimliği | İzleme sorunu
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
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

### <a name="deprecated-rules"></a>Amortismana ait kurallar

Aşağıdaki FxCop eski analiz kuralları amortismana alınır ve çözümleyici olarak uygulanmaz. Daha fazla bilgi [için, roslyn-analyzers GitHub sorunları sayfasında](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port)kural kimliğine (örneğin, **CA1009)** göre arama yapabilirsiniz.

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
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
- [CA2111 1](ca2111.md)
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
- [CA2137 CA2137](ca2137.md)
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
- [CA2222](ca2222.md) ([gerekçe )](https://github.com/dotnet/roslyn-analyzers/issues/1378)
- [CA2223](ca2223.md)
- [CA2228](ca2228.md)
- [CA2230](ca2230.md)
- [CA2233](ca2233.md)
- [CA5122](ca5122.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft.CodeAnalysis.FxCopAnalyzers kuralları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
