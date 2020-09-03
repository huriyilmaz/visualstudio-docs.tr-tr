---
title: Yönetilen kod için genişletilmiş doğruluk kuralları kural kümesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bef208dbcb4c1017840602d198b5099267b25a99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667636"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genişletilmiş Doğruluk Kuralları kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft genişletilmiş doğruluk kuralları kural kümesi, kod analizi tarafından bildirilen mantık ve çerçeve kullanım hatalarını en üst düzeye çıkarır. Ek vurgu, COM birlikte çalışabilirlik ve mobil uygulamalar gibi belirli senaryolara yerleştirilir. Bu senaryolardan biri projeniz için geçerliyse veya projenizde ek sorunlar bulmak için bu kural kümesini dahil etmeyi göz önünde bulundurmanız gerekir.

 Microsoft genişletilmiş doğruluk kuralları kural kümesi, Microsoft temel doğruluk kuralları kural kümesindeki kuralları içerir. Temel doğruluk kuralları, Microsoft 'un en düşük Önerilen Kurallar kural kümesindeki kuralları içerir. Daha fazla bilgi için bkz. yönetilen kod için [Temel Doğruluk Kuralları kural kümesi](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) ve yönetilen [kod Için Yönetilen Önerilen Kurallar kural kümesi](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 Aşağıdaki tabloda, Microsoft genişletilmiş doğruluk kuralları kural kümesindeki tüm kurallar açıklanmaktadır.

|Kural|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Atılabilen alanlara sahip türler atılabilir olmalıdır|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Olay işleyicileri doğru olarak bildirin|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Derlemeleri AssemblyVersionAttribute ile işaretleyin|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Arabirim metotları alt türler tarafından çağrılabilmelidir|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Yerel kaynaklara sahip türler atılabilir olmalıdır|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invokes'u NativeMethods sınıfına taşıyın|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Temel sınıf metotlarını gizlemeyin|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable'ı doğru uygulayın|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Beklenmeyen konumlarda özel durum harekete geçirmeyin|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke giriş noktaları bulunmalıdır|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke'lar görünür olmamalıdır|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Otomatik yerleşim türleri COM görünebilir olmamalıdır|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke ardından hemen GetLastError çağırın|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM görünebilir tür taban türler COM görünebilir olmalıdır|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM kayıt metotları eşleşmelidir|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invoke'ları doğru bildirin|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Boş sonlandırıcıları kaldırın|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Değer tür alanları taşınabilir olmalıdır|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke bildirimleri taşınabilir olmalıdır|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Zayıf kimliği olan nesneleri kilitlemeyin|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL sorgularını güvenlik açıkları için inceleyin|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|İşaretçiler görünür olmamalıdır|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Güvenli türler alanları açığa çıkarmamalıdır|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Metot güvenliği türün bir üst kümesi olmalıdır|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Bağlantı talepleri olan metotları dolaylı olarak açığa çıkarmayın|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Tür bağlantı talepleri kalıtım taleplerini gerektirir|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Temsilciler tutarlı saydamlığı olan metotlara bağlanmalıdır|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metotlar taban metotları geçersiz kılarken tutarlı saydamlığı tutmalıdır|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Saydam metotlar yalnızca doğrulanabilir IL içermelidir|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Saydam metotlar SuppressUnmanagedCodeSecurity özniteliğine sahip metotları çağırmamalıdır|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Saydam kod güvenlik kritik nesnelerine başvurmamalıdır|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Saydam yöntemler bağlantı taleplerini karşılamamalıdır|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Saydam metotlar yerel kod içine çağırmamalıdır|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Yığın ayrıntılarını korumak için yeniden fırlatın|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nesneleri birden çok kez atmayın|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Değer türü statik alanları satır içi başlatın|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Servis verilen bileşenleri WebMethod ile işaretlemeyin|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Atılabilen alanlar atılmalıdır|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Atılabilir türler sonlandırıcıyı bildirmelidir|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Serileştirme oluşturucularını uygulayın|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows Forms giriş noktalarını STAThread ile işaretleyin|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Tüm serileştirilebilir olmayan alanları işaretleyin|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable türler üzerinde taban sınıf metotlarını çağırın|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable türleri SerializableAttribute ile işaretleyin|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Serileştirme metotlarını doğru uygulayın|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable'ı doğru uygulayın|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN için doğru test edin|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Harfleri yerelleştirilmiş parametreler olarak göndermeyin|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeleri büyük harfe normalleştirin|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|Metot sonuçlarını yoksaymayın|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|GC.SuppressFinalize'ı doğru çağırın|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Özellikler diziler döndürmemelidir|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Yalnızca hedeflenen çerçeveden API kullanın|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|GC.KeepAlive'a çağrıları kaldırın|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Yerel kaynakları kapsamak için SafeHandle kullanın|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Salt okunur kesilebilir başvuru türleri bildirmeyin|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Dizi alanları salt okunur olmamalıdır|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Onay deyimlerinin güvenliğini sağlayın|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Özel arabirimleri karşılayan metotları mühürleyin|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Serileştirme oluşturucularının güvenliğini sağlayın|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Statik oluşturucular özel olmalıdır|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Güvenlik kritik sabitleri saydam olmalıdır|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Atma metotları taban sınıf atmayı çağırmalıdır|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standart özel durum oluşturucularını uygulayın|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI parametreleri dize olmamalıdır|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI özellikleri dize olmamalıdır|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|COM görünebilir türler içinde statik üyelerden kaçının|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|AutoDual ClassInterFaceType kullanmayın|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|COM görünebilir türler oluşturulabilir olmalıdır|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|COM kayıt metotları görünebilir olmamalıdır|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource arabirimlerini IDispatch olarak işaretleyin|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Boş işlem önceliğini kullanmayın|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Güç durumu değişikliklerini önleyen zamanlayıcılar kullanmayın|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Sorunlu metotları çağırmaktan kaçının|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Fiberleri iş parçacığı olarak görmeyin|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Düzey 2 derlemeler LinkDemands içermemelidir|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Saydam metotlar HandleProcessCorruptingExceptions özniteliğini kullanamaz|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Saydam kod LinkDemands ile korunmamalıdır|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Saydam metotlar güvenlik taleplerini kullanmamalıdır|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Saydam kod derlemeleri bayt dizilerinden yüklememelidir|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Saydam metotlar SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Harfler doğru yazılmalıdır|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Yayımlanmamış kaynak biçimlerini yollamayın|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|İşleçler taşmamalıdır|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Öznitelik dize harfleri doğru çözümlenmelidir|
