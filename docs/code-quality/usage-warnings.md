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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd2f5919b0f48290ecc14cf71295e2af0bac4748
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509724"
---
# <a name="usage-warnings"></a>Kullanım Uyarıları

Kullanım uyarıları .NET 'in uygun kullanımını destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801.md)|Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir.|
|[CA1816: GC.SuppressFinalize'ı doğru çağırın](../code-quality/ca1816.md)|Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize ya da Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize ya da bir yöntemi GC çağırır. SuppressFinalize ve bu (Visual Basic) dışında bir şey geçirir.|
|[CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın](../code-quality/ca2200.md)|Tekrar fırlatılan bir özel durum ve fırlatma açıklamasında açıkça belirtilen özel durum. Bir özel durum throw deyiminde özel durum belirterek yeniden fırlatılırsa yöntem listesi özel durum döndüren özgün yöntem ile kaybolan geçerli yöntem arasında çağırır.|
|[CA2201: Ayrılmış özel durum türlerini harekete geçirmeyin](../code-quality/ca2201.md)|Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2202: Nesneleri birden çok kez atmayın](../code-quality/ca2202.md)|Yöntem uygulaması, aynı nesne üzerinde System.IDisposable.Dispose veya bir Dispose eşdeğer (örneğin, bazı türleri üzerinde Close() yöntemi) için birden fazla çağrı kodu yolları içerir.|
|[CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207.md)|Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.|
|[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin](../code-quality/ca2208.md)|Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir.|
|[CA2211: Sabit olmayan alanlar görünür olmamalıdır](../code-quality/ca2211.md)|Sabit veya salt okuma olmayan statik alanlar iş parçacığı açısından güvenli değildir. Bu tür bir alana erişimin dikkatle denetlenmesi ve sınıf nesnesine erişimin eşitlenmesi için gelişmiş programlama teknikleri olması gerekir.|
|[CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213.md)|IDisposable uygulayan türlerin alanları System.IDisposable uygulayan bir türle bildirilir. Bir Dispose yöntemi alanının tanıtıcısının bildirim türü Dispose yöntemi tarafından çağrılmaz.|
|[CA2214: Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın](../code-quality/ca2214.md)|Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.|
|[CA2215: Atma metotları taban sınıf atmayı çağırmalıdır](../code-quality/ca2215.md)|Tür atılabilen bir türden devralınırsa, kendi Dispose yönteminden basit tür olan Dispose yöntemini çağırmalıdır.|
|[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216.md)|System. IDisposable uygulayan ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, Object. Finalize tarafından açıklandığı şekilde bir Sonlandırıcı uygulamaz.|
|[CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md)|Dışarıdan görünür bir numaralandırma FlagsAttribute ile işaretlenir ve Numaralandırmadaki bir veya daha fazla değere sahip bir veya daha fazla değer, Numaralandırmadaki diğer tanımlanmış değerlerin bir birleşimi.|
|[CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](../code-quality/ca2219.md)|Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225.md)|Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye, işleçle aynı işlevselliğe erişim sağlar ve aşırı yüklenmiş işleçleri desteklemeyen dillerde programlayan geliştiriciler için sağlanır.|
|[CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226.md)|Bir tür eşitlik veya eşitsizlik işlecini uygular ve karşıt işleci uygulamaz.|
|[CA2227: Koleksiyon özellikleri salt okunur olmalıdır](../code-quality/ca2227.md)|Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir.|
|[CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229.md)|Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.|
|[CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](../code-quality/ca2231.md)|Değer türü geçersiz kılınır `Object.Equals` ancak eşitlik işlecini uygulamaz.|
|[CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin](../code-quality/ca2232.md)|STAThreadAttribute, COM uygulama modelinin tek bir iş parçacıklı grup olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir.|
|[CA2233: İşleçler taşmamalıdır](../code-quality/ca2233.md)|İşlemin sonucunun, dahil edilen veri türleri için olası değerler aralığının dışında olmadığından emin olmak için, aritmetik işlemler önce işlenenleri doğrulamadan gerçekleştirilmemelidir.|
|[CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234.md)|Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı.  Bildirim türü yöntemi, System.Uri parametresini aşırı yüklemeye uyan yöntemi içerir.|
|[CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235.md)|Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.|
|[CA2236: ISerializable türler üzerinde taban sınıf metotlarını çağırın](../code-quality/ca2236.md)|Bu kural ihlalini düzeltmek için, taban türü GetObjectData yöntemini veya karşılık gelen türetilmiş yöntemden ya da oluşturucudan serileştirme oluşturucusunu çağırın.|
|[CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237.md)|Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türü ISerializable arabiriminin uygulanması aracılığıyla özel bir serileştirme yordamı kullanıyor olsa bile, türlerin SerializableAttribute özniteliğiyle işaretlenmesi gerekir.|
|[CA2238: Serileştirme metotlarını doğru uygulayın](../code-quality/ca2238.md)|Seri hale getirme olayı tanıtan yöntem türü, doğru imzaya, dönüş türüne veya görünürlüğe sahip değil.|
|[CA2239: İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın](../code-quality/ca2239.md)|Bir tür, System. Runtime. Serialization. OptionalFieldAttribute özniteliğiyle işaretlenmiş bir alana sahiptir ve tür, serileştirme olay işleme yöntemleri sağlamıyor.|
|[CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240.md)|Bu kural ihlalini onarmak için, GetObjectData yöntemini görünür ve geçersiz kılınabilir yapın ve tüm örnek alanlarının serileştirme işlemine eklendiğinden veya açıkça NonSerializedAttribute özniteliğiyle işaretlenmiş olduğundan emin olun.|
|[CA2241: Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın](../code-quality/ca2241.md)|System. String. Format öğesine geçirilen biçim bağımsız değişkeni, her nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermiyor veya tam tersi.|
|[CA2242: NaN için doğru test edin](../code-quality/ca2242.md)|Bu ifade, değeri Single.Nan veya Double.Nan'a karşı test eder. Single.IsNan(Single) ya da Double.IsNan(Double) değerini test etmek için kullanın.|
|[CA2243: Öznitelik dize harfleri doğru çözümlenmelidir](../code-quality/ca2243.md)|Özniteliğin dize sabit değeri bir URL, GUID veya sürüm için doğru ayrıştırılmadı.|
|[CA2244: Dizine eklenmiş öğe başlatmalarını yineleme](../code-quality/ca2244.md)|Bir nesne başlatıcısının aynı sabit dizine sahip birden fazla dizinli öğe başlatıcısı vardır. Son başlatıcı gereksizdir.|
|[CA2245: Bir özelliği kendisine atama](../code-quality/ca2245.md)|Bir özellik yanlışlıkla kendisine atandı.|
|[CA2246: Sembol ve üyesini aynı deyime atama](../code-quality/ca2246.md)|Bir sembol ve üyesini atama, diğer bir deyişle, bir alan veya özellik, aynı deyimde önerilmez. Üye erişiminin, bu deyimdeki atamadan önce simgenin eski değerini veya atamasından yeni değeri kullanması amaçlandıysa, bu, net değildir.|
|[CA2247: TaskCompletionSource oluşturucusuna geçirilen bağımsız değişken TaskContinuationOptions sabit listesi yerine TaskCreationOptions sabit listesi olmalı](../code-quality/ca2246.md)|TaskCompletionSource, temel alınan görevi denetleyen TaskCreationOptions ve görevde saklanan nesne durumunu alan oluşturucuların bulunduğu oluşturuculara sahiptir.  TaskCreationOptions yerine bir TaskContinuationOptions 'ı yanlışlıkla geçirmek, çağrının durum olarak kabul edilmesine neden olur.|
|[CA2248: ' Enum. HasFlag ' için doğru ' Enum ' bağımsız değişkenini sağlayın](../code-quality/ca2248.md)|Yöntem çağrısına bir bağımsız değişken olarak geçirilen sabit listesi türü, `HasFlag` çağıran enum türünden farklı.|
|[CA2249: String.IndexOf yerine String.Contains kullanmayı düşünün](../code-quality/ca2249.md)|`string.IndexOf`Sonucun varlığı veya bir alt dizenin yokluğunu denetlemek için kullanıldığı yere yapılan çağrılar, ile değiştirilebilir `string.Contains` .|
