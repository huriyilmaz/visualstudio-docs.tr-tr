---
title: Kullanım uyarıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bd1e993723d3ef1779eb3a23e19fedd081b6a6d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603522"
---
# <a name="usage-warnings"></a>Kullanım Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım uyarıları .NET Framework uygun kullanımını destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1801: Kullanılmayan parametreleri gözden geçir](../code-quality/ca1801-review-unused-parameters.md)|Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir.|
|[CA1806: Yöntem sonuçlarını yoksaymayın](../code-quality/ca1806-do-not-ignore-method-results.md)|Yeni bir nesne oluşturulur, ancak hiç kullanılmaz veya çağrılan yeni dizeyi oluşturur ve döndürür ve yeni dize hiç kullanılmaz ya da COM veya P/Invoke yöntemi, bir HRESULT ya da hiç kullanılmayan hata kodu döndürür.|
|[CA1816: GC.SuppressFinalize öğesini doğru çağırın](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize ya da Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize ya da bir yöntemi GC çağırır. SuppressFinalize ve bu (Visual Basic) dışında bir şey geçirir.|
|[CA2200: Yığın ayrıntılarını korumak için yeniden fırlatma](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Bir özel durum yeniden oluşturulur ve özel durum throw ifadesinde açıkça belirtilir. Throw deyimindeki özel durum belirtilerek bir özel durum yeniden oluşturulursa, özel durumu oluşturan özgün Yöntem ve geçerli yöntem arasındaki Yöntem çağrıları kaybolur.|
|[CA2201: Ayrılmış özel durum türleri oluşturmayın](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2202: Nesneleri birden çok kez atmayın](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Yöntem uygulaması, aynı nesne üzerinde System.IDisposable.Dispose veya bir Dispose eşdeğer (örneğin, bazı türleri üzerinde Close() yöntemi) için birden fazla çağrı kodu yolları içerir.|
|[CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Bir yöntemin gövdesi içinde hazır bilgi dizesi Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Platform çağırma yöntemi tanımlanır ve .NET Framework sınıf kitaplığında denk işlevlere sahip bir yöntem bulunur.|
|[CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.|
|[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir.|
|[CA2211: Sabit olmayan alanlar görünür olmamalıdır](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Bu tür bir alana erişimin dikkatle denetlenmesi ve sınıf nesnesine erişimin eşitlenmesi için gelişmiş programlama teknikleri olması gerekir.|
|[CA2212: Servis verilen bileşenleri WebMethod ile işaretlemeyin](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|System. EnterpriseServices. ServicedComponent 'tan devralan bir türdeki yöntem System. Web. Services. WebMethodAttribute ile işaretlenir. WebMethodAttribute ve bir ServicedComponent yönteminin çakışan davranışları ve bağlam ve işlem akışı için gereksinimleri olduğu için, bazı senaryolarda yöntemin davranışı yanlış olacaktır.|
|[CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|IDisposable uygulayan türlerin alanları System.IDisposable uygulayan bir türle bildirilir. Bir Dispose yöntemi alanının tanıtıcısının bildirim türü Dispose yöntemi tarafından çağrılmaz.|
|[CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.|
|[CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Tür atılabilen bir türden devralınırsa, kendi Dispose yönteminden basit tür olan Dispose yöntemini çağırmalıdır.|
|[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|System. IDisposable uygulayan ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, Object. Finalize tarafından açıklandığı şekilde bir Sonlandırıcı uygulamaz.|
|[CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Dışarıdan görünür bir numaralandırma FlagsAttribute ile işaretlenir ve Numaralandırmadaki bir veya daha fazla değere sahip bir veya daha fazla değer, Numaralandırmadaki diğer tanımlanmış değerlerin bir birleşimi.|
|[CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode, karma algoritmalar ve karma tablolar gibi veri yapıları için uygun olan geçerli örneği temel alan bir değer döndürür. Aynı türdeki ve eşit olan iki nesnenin aynı karma kodu döndürmesi gerekir.|
|[CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunu güvence altına almak için, türler basit sınıflarının kendi Finalize yönteminde Finalize yöntemini çağırmalıdır.|
|[CA2221: Sonlandırıcılar korunmalıdır](../code-quality/ca2221-finalizers-should-be-protected.md)|Sonlandırıcılar aile erişim değiştiricisi kullanmalıdır.|
|[CA2222: Devralınan üye görünürlüğünü azaltmayın](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Devralınan üyeler için erişim değiştiricisini değiştirmemelisiniz. Devralınmış bir üyeyi özel olarak değiştirme, arayanların yöntemin temel sınıf uygulamasına erişmesini engellemez.|
|[CA2223: Üyeler dönüş türünden daha fazla farklı olmalıdır](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Ortak dil çalışma zamanı, aynı üyeler arasında ayrım yapmak için dönüş türleri kullanımına izin verir, ancak bu özelliği ne ortak dil belirtimi ne de .NET programlama dillerinin ortak özelliğidir.|
|[CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Ortak tür eşitlik işlecini uygular, ancak Object. Equals öğesini geçersiz kılmaz.|
|[CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye, işleçle aynı işlevselliğe erişim sağlar ve aşırı yüklenmiş işleçleri desteklemeyen dillerde programlayan geliştiriciler için sağlanır.|
|[CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Bir tür eşitlik veya eşitsizlik işlecini uygular ve karşıt işleci uygulamaz.|
|[CA2227: Koleksiyon özellikleri salt okunur olmalıdır](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir.|
|[CA2228: Yayımlanmamış kaynak biçimlerini yollamayın](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|.NET Framework yayın öncesi sürümleri kullanılarak oluşturulan kaynak dosyaları, .NET Framework desteklenen sürümleri tarafından kullanılamayabilir.|
|[CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)|Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.|
|[CA2230: Değişken bağımsız değişkenler için params kullanın](../code-quality/ca2230-use-params-for-variable-arguments.md)|Ortak veya korumalı tür VarArgs çağırma kuralı params anahtar sözcüğünü kullanan bir ortak veya korumalı yöntem içerir.|
|[CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Bir değer türü Object.Equals'ı geçersiz kılar, ama eşitlik işlecini uygulamaz.|
|[CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute, COM uygulama modelinin tek bir iş parçacıklı grup olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir.|
|[CA2233: İşlemler taşmamalıdır](../code-quality/ca2233-operations-should-not-overflow.md)|İşlemin sonucunun, dahil edilen veri türleri için olası değerler aralığının dışında olmadığından emin olmak için, aritmetik işlemler önce işlenenleri doğrulamadan gerçekleştirilmemelidir.|
|[CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı.  Bildirim türü yöntemi, System.Uri parametresini aşırı yüklemeye uyan yöntemi içerir.|
|[CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.|
|[CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Bu kural ihlalini düzeltmek için, taban türü GetObjectData yöntemini veya karşılık gelen türetilmiş yöntemden ya da oluşturucudan serileştirme oluşturucusunu çağırın.|
|[CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türü ISerializable arabiriminin uygulanması aracılığıyla özel bir serileştirme yordamı kullanıyor olsa bile, türlerin SerializableAttribute özniteliğiyle işaretlenmesi gerekir.|
|[CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Seri hale getirme olayı tanıtan yöntem türü, doğru imzaya, dönüş türüne veya görünürlüğe sahip değil.|
|[CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Bir tür, System. Runtime. Serialization. OptionalFieldAttribute özniteliğiyle işaretlenmiş bir alana sahiptir ve tür, serileştirme olay işleme yöntemleri sağlamıyor.|
|[CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)|Bu kural ihlalini onarmak için, GetObjectData yöntemini görünür ve geçersiz kılınabilir yapın ve tüm örnek alanlarının serileştirme işlemine eklendiğinden veya açıkça NonSerializedAttribute özniteliğiyle işaretlenmiş olduğundan emin olun.|
|[CA2241: Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|System. String. Format öğesine geçirilen biçim bağımsız değişkeni, her nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermiyor veya tam tersi.|
|[CA2242: NaN için doğru sınayın](../code-quality/ca2242-test-for-nan-correctly.md)|Bu ifade, değeri Single.Nan veya Double.Nan'a karşı test eder. Single.IsNan(Single) ya da Double.IsNan(Double) değerini test etmek için kullanın.|
|[CA2243: Öznitelik dize harfleri doğru çözümlenmelidir](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Özniteliğin dize sabit değeri bir URL, GUID veya sürüm için doğru ayrıştırılmadı.|
