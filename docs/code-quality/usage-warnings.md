---
title: Kullanım Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305690"
---
# <a name="usage-warnings"></a>Kullanım Uyarıları

Kullanım uyarıları .NET 'in uygun kullanımını destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1801: Kullanılmayan parametreleri gözden geçir @ no__t-0|Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir.|
|[CA1806: Yöntem sonuçlarını yoksayma @ no__t-0|Yeni bir nesne oluşturulur, ancak hiç kullanılmaz veya çağrılan yeni dizeyi oluşturur ve döndürür ve yeni dize hiç kullanılmaz ya da COM veya P/Invoke yöntemi, bir HRESULT ya da hiç kullanılmayan hata kodu döndürür.|
|[CA1816: GC 'yi çağırın. SuppressFinalize doğru @ no__t-0|Dispose uygulamasını bir yöntemi, GC çağırmaz. IDisposable.Dispose; ya da GC Dispose uygulamasını değil bir yöntemi çağırır. IDisposable.Dispose; ya da GC yöntemi çağırır. IDisposable.Dispose ve bu (Visual Basic'te Me) dışında bir şey geçirir.|
|[CA2200: Yığın ayrıntılarını korumak için yeniden throw @ no__t-0|Tekrar fırlatılan bir özel durum ve fırlatma açıklamasında açıkça belirtilen özel durum. Bir özel durum throw deyiminde özel durum belirterek yeniden fırlatılırsa yöntem listesi özel durum döndüren özgün yöntem ile kaybolan geçerli yöntem arasında çağırır.|
|[CA2201: Ayrılmış özel durum türlerini yükseltmeyin @ no__t-0|Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2202: Nesneleri birden çok kez atma @ no__t-0|Yöntem uygulaması, aynı nesne üzerinde System.IDisposable.Dispose veya bir Dispose eşdeğer (örneğin, bazı türleri üzerinde Close() yöntemi) için birden fazla çağrı kodu yolları içerir.|
|[CA2204: Değişmez değerler doğru yazılmalıdır @ no__t-0|Bir yöntemin gövdesi içinde hazır bilgi dizesi Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA2205: Win32 API @ no__t-0 ' ın yönetilen eşdeğerlerini kullanın|Platform çağırma yöntemi tanımlanır ve eşdeğer işlevselliğe sahip bir .NET yöntemi kullanılabilir.|
|[CA2207: Değer türü statik alanları satır içi @ no__t-0 olarak Başlat|Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.|
|[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin @ no__t-0|Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir.|
|[CA2211: Sabit olmayan alanlar görünür olmamalıdır @ no__t-0|Sabit veya salt okuma olmayan statik alanlar iş parçacığı açısından güvenli değildir. Bu tür bir alana erişimin dikkatle denetlenmesi ve sınıf nesnesine erişimin eşitlenmesi için gelişmiş programlama teknikleri olması gerekir.|
|[CA2212: Hizmet verilen bileşenleri WebMethod @ no__t ile işaretlemeyin-0|System. EnterpriseServices. ServicedComponent 'tan devralan bir türdeki yöntem System. Web. Services. WebMethodAttribute ile işaretlenir. WebMethodAttribute ve bir ServicedComponent yönteminin çakışan davranışları ve bağlam ve işlem akışı için gereksinimleri olduğu için, bazı senaryolarda yöntemin davranışı yanlış olacaktır.|
|[CA2213: Atılabilir alanlar atılmalıdır @ no__t-0|IDisposable uygulayan türlerin alanları System.IDisposable uygulayan bir türle bildirilir. Bir Dispose yöntemi alanının tanıtıcısının bildirim türü Dispose yöntemi tarafından çağrılmaz.|
|[CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın @ no__t-0|Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.|
|[CA2215: Dispose yöntemleri temel sınıf Dispose @ no__t-0 ' i çağırmalıdır|Tür atılabilen bir türden devralınırsa, kendi Dispose yönteminden basit tür olan Dispose yöntemini çağırmalıdır.|
|[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir @ no__t-0|System. IDisposable uygulayan ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, Object. Finalize tarafından açıklandığı şekilde bir Sonlandırıcı uygulamaz.|
|[CA2217: Numaralandırmaları FlagsAttribute @ no__t ile işaretlemeyin-0|Dışarıdan görünür bir numaralandırma FlagsAttribute ile işaretlenir ve Numaralandırmadaki bir veya daha fazla değere sahip bir veya daha fazla değer, Numaralandırmadaki diğer tanımlanmış değerlerin bir birleşimi.|
|[CA2218: Geçersiz kılma için GetHashCode geçersiz kılma @ no__t-0|GetHashCode, karma algoritmalar ve karma tablolar gibi veri yapıları için uygun olan geçerli örneği temel alan bir değer döndürür. Aynı türdeki ve eşit olan iki nesnenin aynı karma kodu döndürmesi gerekir.|
|[CA2219: Özel durum yan tümcelerinde özel durumlar tetiklemeyin @ no__t-0|Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2220: Sonlandırıcılar temel sınıf sonlandırıcısını çağırmalıdır @ no__t-0|Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunu güvence altına almak için, türler basit sınıflarının kendi Finalize yönteminde Finalize yöntemini çağırmalıdır.|
|[CA2221: Sonlandırıcılar korunmalıdır @ no__t-0|Sonlandırıcılar aile erişim değiştiricisi kullanmalıdır.|
|[CA2222: Devralınan üye görünürlüğünü azaltma @ no__t-0|Devralınan Üyeler için erişim değiştiricisini değiştirmeyin. Devralınmış bir üyeyi özel olarak değiştirme, arayanların yöntemin temel sınıf uygulamasına erişmesini engellemez.|
|[CA2223: Üyeler, dönüş türü @ no__t-0 ' dan fazla farklı olmalıdır|Ortak dil çalışma zamanı, aynı üyeler arasında ayrım yapmak için dönüş türleri kullanımına izin verir, ancak bu özelliği ne ortak dil belirtimi ne de .NET programlama dillerinin ortak özelliğidir.|
|[CA2224: Aşırı yükleme işlecinde Equals eşittir @ no__t-0|Ortak tür eşitlik işlecini uygular, ancak Object. Equals öğesini geçersiz kılmaz.|
|[CA2225: İşleç aşırı yüklemelerinin adlandırılmış alternatifleri var @ no__t-0|Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye, işleçle aynı işlevselliğe erişim sağlar ve aşırı yüklenmiş işleçleri desteklemeyen dillerde programlayan geliştiriciler için sağlanır.|
|[CA2226: İşleçler, simetrik aşırı yüklemeleri olmalıdır @ no__t-0|Bir tür eşitlik veya eşitsizlik işlecini uygular ve karşıt işleci uygulamaz.|
|[CA2227: Koleksiyon özellikleri salt okuma olmalıdır @ no__t-0|Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir.|
|[CA2228: Serbest bırakılmamış kaynak biçimlerini gönderme @ no__t-0|.NET 'in yayın öncesi sürümleri kullanılarak oluşturulan kaynak dosyaları, .NET 'in desteklenen sürümleri tarafından kullanılamayabilir.|
|[CA2229: Serileştirme oluşturucularını Uygula @ no__t-0|Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.|
|[CA2230: Değişken bağımsız değişkenler için params kullanın @ no__t-0|Ortak veya korumalı tür VarArgs çağırma kuralı params anahtar sözcüğünü kullanan bir ortak veya korumalı yöntem içerir.|
|[CA2231: Geçersiz kılma ValueType. Equals @ no__t-0 üzerine yükleme işleci|Değer türü `Object.Equals` ' y i geçersiz kılar, ancak eşitlik işlecini uygulamaz.|
|[CA2232: Windows Forms giriş noktalarını STAThread @ no__t-0 ile işaretle|STAThreadAttribute, COM uygulama modelinin tek bir iş parçacıklı grup olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir.|
|[CA2233: İşlemler @ no__t-0 taşmamalıdır|İşlemin sonucunun, dahil edilen veri türleri için olası değerler aralığının dışında olmadığından emin olmak için, aritmetik işlemler önce işlenenleri doğrulamadan gerçekleştirilmemelidir.|
|[CA2234: @ No__t-0 dizeleri yerine System. Uri nesneleri geçirin|Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı.  Bildirim türü yöntemi, System.Uri parametresini aşırı yüklemeye uyan yöntemi içerir.|
|[CA2235: Tüm seri hale getirilebilir olmayan alanları işaretle @ no__t-0|Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.|
|[CA2236: ISerializable türlerinde temel sınıf yöntemlerini çağırma @ no__t-0|Bu kural ihlalini düzeltmek için, taban türü GetObjectData yöntemini veya karşılık gelen türetilmiş yöntemden ya da oluşturucudan serileştirme oluşturucusunu çağırın.|
|[CA2237: ISerializable türlerini SerializableAttribute @ no__t ile işaretle-0|Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türü ISerializable arabiriminin uygulanması aracılığıyla özel bir serileştirme yordamı kullanıyor olsa bile, türlerin SerializableAttribute özniteliğiyle işaretlenmesi gerekir.|
|[CA2238: Serileştirme yöntemlerini doğru uygulayın @ no__t-0|Seri hale getirme olayı tanıtan yöntem türü, doğru imzaya, dönüş türüne veya görünürlüğe sahip değil.|
|[CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma yöntemleri sağla @ no__t-0|Bir tür, System. Runtime. Serialization. OptionalFieldAttribute özniteliğiyle işaretlenmiş bir alana sahiptir ve tür, serileştirme olay işleme yöntemleri sağlamıyor.|
|[CA2240: ISerializable doğru Uygula @ no__t-0|Bu kural ihlalini onarmak için, GetObjectData yöntemini görünür ve geçersiz kılınabilir yapın ve tüm örnek alanlarının serileştirme işlemine eklendiğinden veya açıkça NonSerializedAttribute özniteliğiyle işaretlenmiş olduğundan emin olun.|
|[CA2241: Biçimlendirme yöntemlerine doğru bağımsız değişkenleri sağlayın @ no__t-0|System. String. Format öğesine geçirilen biçim bağımsız değişkeni, her nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermiyor veya tam tersi.|
|[CA2242: NaN için test doğru @ no__t-0|Bu ifade, değeri Single.Nan veya Double.Nan'a karşı test eder. Single.IsNan(Single) ya da Double.IsNan(Double) değerini test etmek için kullanın.|
|[CA2243: Öznitelik dize sabit değerleri doğru ayrıştırılmalıdır @ no__t-0|Özniteliğin dize sabit değeri bir URL, GUID veya sürüm için doğru ayrıştırılmadı.|