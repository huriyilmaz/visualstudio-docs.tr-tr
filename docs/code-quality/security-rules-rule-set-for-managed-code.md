---
title: Yönetilen kod için Güvenlik Kuralları kural kümesi
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf4e140b3a379221c3b7e5a05428b29e3a985b
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018386"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Yönetilen kod için Güvenlik Kuralları kural kümesi

Bildirilen olası güvenlik sorunlarının sayısını en üst düzeye çıkarmak için eski kod analizi için Microsoft güvenlik kuralları kural kümesini kullanın.

|Kural|Açıklama|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL sorgularını güvenlik açıkları için inceleyin|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Kesin temelli güvenliği gözden geçirin|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Salt okunur kesilebilir başvuru türleri bildirmeyin|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Dizi alanları salt okunur olmamalıdır|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Onay deyimlerinin güvenliğini sağlayın|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Gözden geçirmeyi reddedin ve yalnızca kullanımına izin verin|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Görünen olay işleyicilerini gözden geçirin|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|İşaretçiler görünür olmamalıdır|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Güvenli türler alanları açığa çıkarmamalıdır|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Metot güvenliği türün bir üst kümesi olmalıdır|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın|
|[CA2116Ç](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçirin|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Özel arabirimleri karşılayan metotları mühürleyin|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Serileştirme oluşturucularının güvenliğini sağlayın|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statik oluşturucular özel olmalıdır|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Bağlantı talepleri olan metotları dolaylı olarak açığa çıkarmayın|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Tür bağlantı talepleri kalıtım taleplerini gerektirir|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Güvenlik kritik sabitleri saydam olmalıdır|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Temsilciler tutarlı saydamlığı olan metotlara bağlanmalıdır|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metotlar taban metotları geçersiz kılarken tutarlı saydamlığı tutmalıdır|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Düzey 2 derlemeler LinkDemands içermemelidir|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Saydam metotlar yalnızca doğrulanabilir IL içermelidir|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Saydam metotlar SuppressUnmanagedCodeSecurity özniteliğine sahip metotları çağırmamalıdır|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Saydam metotlar HandleProcessCorruptingExceptions özniteliğini kullanamaz|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Saydam kod güvenlik kritik nesnelerine başvurmamalıdır|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Saydam yöntemler bağlantı taleplerini karşılamamalıdır|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Saydam kod LinkDemands ile korunmamalıdır|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Saydam metotlar güvenlik taleplerini kullanmamalıdır|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Saydam kod derlemeleri bayt dizilerinden yüklememelidir|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Saydam metotlar SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Saydam metotlar yerel kod içine çağırmamalıdır|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Derlemelerin geçerli tanımlayıcı adları olmalıdır|
|[CA2300](ca2300.md)|Güvenli olmayan seri durumdan çıkarıcı BinaryFormatter kullanmayın|
|[CA2301](ca2301.md)|İlk olarak BinaryFormatter.Binder öğesini ayarlamadan önce BinaryFormatter.Deserialize çağırmayın|
|[CA2302](ca2302.md)|BinaryFormatter.Deserialize çağırmadan önce BinaryFormatter.Binder öğesinin ayarlandığından emin olun|
|[CA2305](ca2305.md)|Güvenli olmayan seri kaldırıcı LosFormatter kullanmayın|
|[CA2310](ca2310.md)|Güvenli olmayan seri kaldırıcı NetDataContractSerializer kullanmayın|
|[CA2311](ca2311.md)|İlk olarak NetDataContractSerializer.Binder öğesini ayarlamadan seri durumdan çıkarmayın|
|[CA2312](ca2312.md)|Seri durumdan çıkarmadan önce NetDataContractSerializer.Binder öğesinin ayarlandığından emin olun|
|[CA2315](ca2315.md)|Güvenli olmayan seri kaldırıcı ObjectStateFormatter kullanmayın|
|[CA2321](ca2321.md)|SimpleTypeResolver kullanarak JavaScriptSerializer ile seri durumdan çıkarmayın|
|[CA2322](ca2322.md)|Seri durumdan çıkarmadan önce SimpleTypeResolver ile JavaScriptSerializer’ın başlatılmadığından emin olun|
|[CA3001](../code-quality/ca3001.md)|SQL ekleme güvenlik açıkları için inceleme kodu|
|[CA3002](../code-quality/ca3002.md)|XSS güvenlik açıkları için inceleme kodu|
|[CA3003](../code-quality/ca3003.md)|Dosya yolu ekleme güvenlik açıkları için inceleme kodu|
|[CA3004](../code-quality/ca3004.md)|Bilgilerin açığa çıkmasıyla ilgili güvenlik açıkları için inceleme kodu|
|[CA3005](../code-quality/ca3005.md)|LDAP ekleme güvenlik açıkları için inceleme kodu|
|[CA3006](../code-quality/ca3006.md)|İşlem komutu ekleme güvenlik açıkları için inceleme kodu|
|[CA3007](../code-quality/ca3007.md)|Açık yeniden yönlendirme güvenlik açıkları için inceleme kodu|
|[CA3008](../code-quality/ca3008.md)|XPath ekleme güvenlik açıkları için inceleme kodu|
|[CA3009](../code-quality/ca3009.md)|XML ekleme güvenlik açıkları için inceleme kodu|
|[CA3010](../code-quality/ca3010.md)|XAML ekleme güvenlik açıkları için inceleme kodu|
|[CA3011](../code-quality/ca3011.md)|DLL ekleme güvenlik açıkları için inceleme kodu|
|[CA3012](../code-quality/ca3012.md)|Normal ifade ekleme güvenlik açıkları için inceleme kodu|
