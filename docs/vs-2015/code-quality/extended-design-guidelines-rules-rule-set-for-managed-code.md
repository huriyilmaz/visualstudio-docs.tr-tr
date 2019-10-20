---
title: Yönetilen kod için genişletilmiş tasarım yönergeleri kuralları kural kümesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0951d337375a7396d1158dc933b77fda13fa91a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667616"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genişletilmiş Tasarım Yönerge Kuralları kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft genişletilmiş tasarım kılavuzu kuralları kural kümesi, bildirilen kullanılabilirliği ve bakım sorunlarını en üst düzeye çıkarmak için temel tasarım kılavuzu kuralları ' nı genişletir. Ek vurgu, adlandırma yönergelerine göre yerleştirilir. Projeniz kitaplık kodu içeriyorsa veya bakımı kolay olan kod yazmak için en yüksek standartları zorlamak istiyorsanız bu kural kümesini dahil etmeyi göz önünde bulundurmanız gerekir.

 Genişletilmiş tasarım kılavuz kuralları, tüm Microsoft temel tasarım kılavuzu kurallarını içerir. Temel tasarım kılavuz kuralları, Microsoft 'un en düşük önerilen kurallarını içerir. Daha fazla bilgi için bkz. yönetilen kod için [temel tasarım kılavuz kuralları kural kümesi](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) ve yönetilen [kod Için Yönetilen Önerilen Kurallar kural kümesi](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 Aşağıdaki tabloda, Microsoft genişletilmiş tasarım kılavuzu kuralları kural kümesindeki tüm kurallar açıklanmaktadır.

|Kural|Açıklama|
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
|[CA2116Ç](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Genel türlerde statik üyeler belirtme|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Genel listeleri gösterme|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Genel olay işleyicisi örnekleri kullan|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Genel metotlar tür parametresi sağlamalıdır|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Genel türlerde aşırı parametre kullanmaktan kaçının|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Üye imzalarında genel türleri iç içe kullanma|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Uygun yerlerde genel türleri kullanın|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Sabit listelerinin sıfır değeri olmalıdır|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Koleksiyonlar genel arabirimi uygulamalıdır|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Parametre olarak temel türleri geçmeyi düşünün|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Soyut türlerin oluşturucuları olmamalıdır|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Toplama ve çıkarmayı aşırı yüklediğinizde eşittir işlecini aşırı yükleyin|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Derlemeleri CLSCompliantAttribute ile işaretle|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Derlemeleri ComVisibleAttribute ile işaretleyin|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Öznitelikleri AttributeUsageAttribute ile işaretle|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Öznitelik bağımsız değişkenleri için erişimciler tanımlayın|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Dizin oluşturucular çok boyutlu olmamalıdır|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Uygun yerlerde özellikleri kullanın|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Yinelenen bağımsız değişkenleri params dizisiyle değiştirin|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Varsayılan parametreler kullanılmamalıdır|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Sabit listelerini FlagsAttribute ile işaretleyin|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Sabit listesi depolaması Int32 olmalıdır|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Uygun yerlerde olayları kullanın|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Genel özel durum türlerini yakalamayın|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Standart özel durum oluşturucularını uygulayın|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|İç içe türler görünür olmamalıdır|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection uygulamalarının kesin türde üyeleri vardır|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Karşılaştırılabilir türlerde metotları geçersiz kıl|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Numaralandırıcıların kesin türü belirtilmiş olmalıdır|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Listeler kesin türdedir|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|ObsoleteAttribute iletisi sağla|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Dizin oluşturucular için tam sayı veya dize bağımsız değişken kullanın|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Özellikler salt yazılır olmamalıdır|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Eşittir işlecini başvuru türlerinde aşırı yüklemeyin|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Sealed türlerde protected üyeler bildirmeyin|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Sealed türlerde virtual üyeler bildirmeyin|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Ad alanlarında türler bildirin|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Görünür örnek alanlarını bildirmeyin|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Static tutucu türler sealed olmalıdır|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Static tutucu türlerin oluşturucuları olmamalıdır|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI parametreleri dize olmamalıdır|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI dönüş değerleri dize olmamalıdır|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI özellikleri dize olmamalıdır|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|String URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Türler belirli temel türleri aşmamalıdır|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Üyeler belirli somut türleri kullanıma sunmamalıdır|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Özel durumlar genel olmalıdır|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Değişken adları alan adları ile eşleşmemelidir|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Aşırı karmaşıklıktan kaçının|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Kullanılmayan parametreleri gözden geçirin|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Kullanılmayan yerelleri kaldırın|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Aşırı yerellerden kaçının|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Başvuru türü statik alanları satır içinden başlatın|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Çağırılmayan özel kodlardan kaçının|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Örneklenmemiş iç sınıflardan kaçının|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Mühürsüz özniteliklerden kaçının|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Çok boyutlu diziler yerine basit dizileri tercih edin|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Özellikler diziler döndürmemelidir|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Dize uzunluğunu kullanarak boş dizeleri test edin|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Üyeleri static olarak işaretleyin|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Kullanılmayan özel alanlardan kaçının|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ayrılmış özel durum türlerini harekete geçirmeyin|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API'sinin yönetilen eşdeğerlerini kullanın|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Bağımsız değişken özel durumlarını doğru örnekleyin|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Sabit olmayan alanlar görünür olmamalıdır|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Sabit listelerini FlagsAttribute ile işaretlemeyin|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Özel durum yan tümceleri içinde özel durum harekete geçirmeyin|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Sonlandırıcılar korunmalıdır|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Devralınan üye görünürlüğünü azaltmayın|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Üyeler dönüş türünden daha fazla farklı olmalıdır|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|İşleçler simetrik aşırı yüklemelere sahip olmalıdır|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Koleksiyon özellikleri salt okunur olmalıdır|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Değişken bağımsız değişkenler için params kullanın|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Dizeler yerine System.Uri nesneleri gönderin|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın|
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Az tür içeren ad alanlarından kaçının|
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|out parametrelerinden kaçının|
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Boş arabirimlerden kaçının|
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Türleri başvuru olarak geçmeyin|
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Genel metotların bağımsız değişkenlerini doğrulayın|
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Aşırı devralmadan kaçının|
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Yanıltıcı alan adlarını gözden geçirin|
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Bakımı yapılamayan kodlardan kaçının|
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Aşırı sınıf bağlantısından kaçının|
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Sabit listesi değerlerini 'Reserved' olarak adlandırmayın|
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır|
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır|
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Kaynak dizeleri doğru yazılmalıdır|
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Tanımlayıcılar doğru yazılmalıdır|
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Tanımlayıcılar alt çizgi içermemelidir|
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır|
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Tanımlayıcılar doğru soneke sahip olmalıdır|
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Tanımlayıcılar yanlış sonek içermemelidir|
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Sabit listesi değerlerine tür adını önek olarak eklemeyin|
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Olaylar önce ya da sonra önekine sahip olmamalıdır|
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Bayrak sabit listeleri çoğul adlara sahip olmalıdır|
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Tanımlayıcılar doğru ön eke sahip olmalıdır|
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır|
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Parametre adları üye adları ile eşleşmemelidir|
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Tanımlayıcılar tür adları içermemelidir|
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Özellik adları get metotları ile eşleşmemelidir|
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Tanımlayıcılar yanlış ön ek içermemelidir|
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Tür adları ad alanları ile eşleşmemelidir|
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Parametre adları temel bildirimle eşleşmemelidir|
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Tercih edilen terimleri kullanın|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Harfler doğru yazılmalıdır|
