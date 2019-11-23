---
title: Eski dil hizmeti ayrıştırıcısı ve tarayıcısı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726733"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı
Ayrıştırıcı, dil hizmetinin kalbidir. Yönetilen paket çerçevesi (MPF) dil sınıfları, görüntülenmekte olan kodla ilgili bilgileri seçmek için bir dil ayrıştırıcısı gerektirir. Bir Ayrıştırıcı, metni sözcük temelli belirteçlere ayırır ve sonra bu belirteçleri tür ve işlevlere göre tanımlar.

## <a name="discussion"></a>Tartışma
 Aşağıda bir C# yöntemi verilmiştir.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 Bu örnekte, belirteçler sözcükler ve noktalama işaretleri vardır. Belirteç türleri aşağıdaki gibidir.

|Belirteç adı|Belirteç türü|
|----------------|----------------|
|Namespace, Class, Public, void, int|sözcükle|
|=|operator|
|{ } ( ) ;|ayırıcı|
|MyNamespace, MyClass, MyFunction, arg1, var1|tanımlayıcı|
|MyNamespace|ad alanı|
|Sınıfım|sınıf|
|MyFunction|yöntemi|
|arg1|parametre|
|var1|Yerel değişken|

 Ayrıştırıcısının rolü belirteçleri belirlemektir. Bazı belirteçlerin birden fazla türü olabilir. Ayrıştırıcı belirteçleri tanımladıktan sonra dil hizmeti, söz dizimi vurgulaması, küme ayracı eşleştirme ve IntelliSense işlemleri gibi yararlı özellikler sağlamak için bu bilgileri kullanabilir.

## <a name="types-of-parsers"></a>Ayrıştırıcıları türleri
 Dil hizmeti ayrıştırıcısı, bir derleyicinin parçası olarak kullanılan bir ayrıştırıcıyla aynı değildir. Ancak, bu tür bir ayrıştırıcıda bir derleyici ayrıştırıcıyla aynı şekilde hem tarayıcı hem de ayrıştırıcı kullanması gerekir.

- Bir tarayıcı, belirteç türlerini belirlemek için kullanılır. Bu bilgiler, söz dizimi vurgulaması için ve diğer işlemleri tetikleyebilecek (ayraç eşleştirme gibi) belirteç türlerini hızlı bir şekilde tanımlamak için kullanılır. Bu tarayıcı <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi tarafından temsil edilir.

- Bir Ayrıştırıcı, belirteçlerin işlevlerini ve kapsamını tanımlamakta kullanılır. Bu bilgiler, IntelliSense işlemlerinde Yöntemler, değişkenler, parametreler ve bildirimler gibi dil öğelerini tanımlamak ve bağlam temelinde üye ve yöntem imzaları listeleri sağlamak için kullanılır. Bu ayrıştırıcı Ayrıca, parantez ve parantezler gibi eşleşen dil öğesi çiftlerini bulmak için de kullanılır. Bu ayrıştırıcıya <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi aracılığıyla erişilir.

  Dil hizmetiniz için bir tarayıcıyı ve ayrıştırıcısı nasıl uygulayacağınızı öğrenin. Çözümleyicilerin nasıl çalıştığını ve kendi ayrıştırıcılarınızın nasıl yazılacağını betimleyen birkaç kaynak vardır. Ayrıca, bir Ayrıştırıcı oluşturmaya yardımcı olan çeşitli ücretsiz ve ticari ürünler de mevcuttur.

### <a name="the-parsesource-parser"></a>ParseSource ayrıştırıcısı
 Bir derleyicinin parçası olarak kullanılan bir Ayrıştırıcıdan farklı olarak (belirteçlerin bazı yürütülebilir kod biçimine dönüştürülebildiği) farklı nedenlerden dolayı bir dil hizmeti ayrıştırıcısı çağrılabilir ve birçok farklı bağlamda. Bu yaklaşımı, <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminde nasıl uygulayacağınızı görürsünüz. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminin bir arka plan iş parçacığında çağrılabilecek olabileceğini aklınızda bulundurmanız önemlidir.

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest> yapısı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesnesine bir başvuru içerir. Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesnesi arka plan iş parçacığında kullanılamaz. Aslında, temel MPF sınıflarının birçoğu arka plan iş parçacığında kullanılamaz. Bunlar, görünüm ile doğrudan veya dolaylı olarak iletişim kuran <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> sınıfları ve diğer herhangi bir sınıfı içerir.

 Bu ayrıştırıcı genellikle ilk kez çağrıldığında veya <xref:Microsoft.VisualStudio.Package.ParseReason> ayrıştırma nedeni değeri verildiğinde kaynak dosyanın tamamını ayrıştırır. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemine yapılan sonraki çağrılar, ayrıştırılmış kodun küçük bir kısmını işler ve önceki tam Ayrıştırma işleminin sonuçları kullanılarak çok daha hızlı yürütülebilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi, <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesneleri aracılığıyla ayrıştırma işleminin sonuçlarını iletişim kurar. <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesi, belirli bir ayrıştırma nedeni hakkında bilgi toplamak için kullanılır. Örneğin, eşleşen küme ayraçları veya parametre listelerine sahip Yöntem imzalarının yayılmaları hakkındaki bilgiler. <xref:Microsoft.VisualStudio.Package.AuthoringScope>, bildirim ve yöntem imzaları koleksiyonları sağlar ve ayrıca gelişmiş düzenleme seçeneğine git seçeneğini destekler (**tanıma**git, **bildirime**git, **başvuruya git**).

### <a name="the-iscanner-scanner"></a>IScanner tarayıcısı
 Ayrıca, <xref:Microsoft.VisualStudio.Package.IScanner>uygulayan bir tarayıcı da uygulamalısınız. Ancak, bu tarayıcı <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı aracılığıyla satır içi olarak çalıştığından, genellikle uygulaması daha kolay olur. Her satırın başlangıcında, MPF <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfına, tarayıcıya geçirilen bir durum değişkeni olarak kullanılacak bir değer verir. Her satırın sonunda, tarayıcı güncelleştirilmiş durum değişkenini döndürür. MPF bu durum bilgilerini her satır için önbelleğe alır, böylece tarayıcı kaynak dosyanın başlangıcında başlatmaya gerek kalmadan herhangi bir satırdan ayrıştırmaya başlayabilir. Tek bir satırın hızlı taraması, düzenleyicinin kullanıcıya hızlı geri bildirim sağlamasına olanak tanır.

## <a name="parsing-for-matching-braces"></a>Eşleşen küme ayraçları için ayrıştırma
 Bu örnek, kullanıcının yazdığı bir kapanış ayracı ile eşleşen denetim akışını gösterir. Bu süreçte, belirtecin türünü ve belirtecin bir eşleştirme ayracı işlemini tetikleyemeyeceğini anlamak için renklendirme için kullanılan tarayıcı da kullanılır. Tetikleyici bulunursa, eşleşen ayracı bulmak için <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi çağırılır. Son olarak, iki küme ayracı vurgulanır.

 Küme ayraçları Tetikleyiciler ve ayrıştırma nedenlerinin adlarında kullanılmasına karşın, bu işlem gerçek küme ayraçları ile sınırlı değildir. Eşleşen bir çift olarak belirtilen tüm karakter çiftleri desteklenir. Örnekler şunlardır (ve), \< ve > ve [ve].

 Dil hizmetinin eşleşen ayraçları desteklediğini varsayın.

1. Kullanıcı bir kapanış küme ayracı (}).

2. Küme ayracı, kaynak dosyadaki imlece eklenir ve imleç bir tarafından ilerlemiş olur.

3. <xref:Microsoft.VisualStudio.Package.Source> sınıfındaki <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> yöntemi, türü belirlenmiş kapanış ayracı ile çağırılır.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> yöntemi, geçerli imleç konumundan hemen önceki konumdaki belirteci almak için <xref:Microsoft.VisualStudio.Package.Source> sınıfındaki <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yöntemini çağırır. Bu belirteç, türü belirlenmiş kapanış ayracı ' ne karşılık gelir).

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yöntemi, geçerli satırdaki tüm belirteçleri almak için <xref:Microsoft.VisualStudio.Package.Colorizer> nesnesindeki <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yöntemini çağırır.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yöntemi, geçerli satırın metniyle <xref:Microsoft.VisualStudio.Package.IScanner> nesne üzerindeki <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> yöntemini çağırır.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yöntemi, geçerli satırdaki tüm belirteçleri toplamak için <xref:Microsoft.VisualStudio.Package.IScanner> nesnesindeki <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> yöntemini tekrar tekrar çağırır.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yöntemi, istenen konumu içeren belirteci almak için <xref:Microsoft.VisualStudio.Package.Source> sınıfında özel bir yöntemi çağırır ve <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yönteminden alınan belirteçlerin listesine geçirilir.

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> yöntemi <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yönteminden döndürülen belirteçte <xref:Microsoft.VisualStudio.Package.TokenTriggers> belirteç tetikleyici bayrağını arar; diğer bir deyişle, kapatma küme ayracını temsil eden belirteç).

6. <xref:Microsoft.VisualStudio.Package.TokenTriggers> tetikleyici bayrağı bulunursa, <xref:Microsoft.VisualStudio.Package.Source> sınıfındaki <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> yöntemi çağrılır.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> yöntemi, <xref:Microsoft.VisualStudio.Package.ParseReason>ayrıştırma neden değeri ile bir ayrıştırma işlemi başlatır. Bu işlem, sonuçta <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfında <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemini çağırır. Zaman uyumsuz ayrıştırma etkinse, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoduna yapılan bu çağrı arka plan iş parçacığında oluşur.

8. Ayrıştırma işlemi tamamlandığında, <xref:Microsoft.VisualStudio.Package.Source> sınıfında `HandleMatchBracesResponse` adlı bir iç tamamlama işleyicisi (geri çağırma yöntemi olarak da bilinir) çağırılır. Bu çağrı, ayrıştırıcının değil <xref:Microsoft.VisualStudio.Package.LanguageService> temel sınıfı tarafından otomatik olarak yapılır.

9. `HandleMatchBracesResponse` yöntemi <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesinde depolanan <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesinden yayılmalar listesini alır. (Span, kaynak dosyadaki bir dizi satırı ve karakteri belirten <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> yapısıdır.) Bu yayılmalar, genellikle her biri açma ve kapatma ayraçları için olmak üzere iki yayılma içerir.

10. `HandleBracesResponse` yöntemi, <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesinde depolanan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesnesi üzerinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> yöntemini çağırır. Bu, verilen yayılmaları vurgular.

11. <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Özellik <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> etkinse, `HandleBracesResponse` yöntemi, eşleşen yayılma tarafından dahil edilen metni alır ve durum çubuğunda Bu yayılma alanının ilk 80 karakterini görüntüler. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi, eşleşen çifte eşlik eden dil öğesini içeriyorsa, bu en iyi sonucu verir. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> özelliğine bakın.

12. Yapıldığını.

### <a name="summary"></a>Özet
 Eşleşen küme ayraçları işlemi, genellikle basit dil öğesi çiftleri ile sınırlıdır. Eşleşen Üçlü öğeler ("`if(...)`", "`{`" ve "`}`" veya "`else`", "`{`" ve "`}`") gibi daha karmaşık öğeler, bir sözcük tamamlama işleminin parçası olarak vurgulanabilir. Örneğin, "Else" sözcüğü bittiğinde, eşleşen "`if`" deyimleri vurgulanabilir. Bir dizi `if`/`else if` deyim varsa, bunların hepsi eşleşen küme ayraçları ile aynı mekanizmaya göre vurgulanacaktır. <xref:Microsoft.VisualStudio.Package.Source> temel sınıfı bunu şu şekilde destekler: tarayıcı, imleç konumundan önceki belirteç için tetikleyici değer <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> belirteç tetikleyici değerini döndürmelidir.

 Daha fazla bilgi için bkz. [eski dil hizmetinde küme ayracı eşleme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Renklendirme için ayrıştırma
 Kaynak kodu renklendirme basittir, belirtecin türünü ve bu türle ilgili dönüş renk bilgilerini belirlemeniz yeterlidir. <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, her belirteçle ilgili renk bilgilerini sağlamak için düzenleyici ve tarayıcı arasında aracı işlevi görür. <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, bir satırı renklendirime ve ayrıca kaynak dosyadaki tüm satırların durum bilgilerini toplama konusunda yardımcı olmak için <xref:Microsoft.VisualStudio.Package.IScanner> nesnesini kullanır. MPF dil hizmeti sınıflarında, yalnızca <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi aracılığıyla tarayıcıyla iletişim kurduğu için <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfının geçersiz kılınması gerekmez. <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfında <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemini geçersiz kılarak <xref:Microsoft.VisualStudio.Package.IScanner> arabirimini uygulayan nesnesini sağlarsınız.

 <xref:Microsoft.VisualStudio.Package.IScanner> tarayıcıya <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> yöntemi aracılığıyla kaynak kodu satırı verilir. <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> yöntemine yapılan çağrılar, satır belirteçlerin tükenene kadar satırdaki bir sonraki belirteci almak için yinelenir. Renklendirme için MPF tüm kaynak kodlarını satır dizisi olarak değerlendirir. Bu nedenle, tarayıcı, kaynak olarak bu kaynağa gelen kaynak ile Cope sağlamalıdır. Bunlara ek olarak, herhangi bir zamanda tarayıcıya herhangi bir zaman geçirilebilir ve tek garanti, tarayıcının durum değişkenini taranmadan önceki satırdan almasını sağlar.

 <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, belirteç tetikleyicilerini belirlemek için de kullanılır. Bu Tetikleyiciler, MPF 'ye belirli bir belirtecin sözcük tamamlama veya eşleşen küme ayraçları gibi daha karmaşık bir işlem başlatabileceğini söyler. Bu tür Tetikleyiciler hızlı olması ve herhangi bir konumda gerçekleşmesi gerektiğinden, tarayıcı bu görev için en uygun seçenektir.

 Daha fazla bilgi için, bkz. [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Işlevsellik ve kapsam için ayrıştırma
 İşlevsellik ve kapsam için ayrıştırma, yalnızca karşılaşılan belirteç türlerini tanımlamaya kıyasla daha fazla çaba gerektirir. Ayrıştırıcının yalnızca belirteç türünü değil, belirtecin kullanıldığı işlevselliği de belirlemesi gerekir. Örneğin, bir tanımlayıcı yalnızca bir addır, ancak dilinizde bir tanımlayıcı, içeriğe bağlı olarak bir sınıf, ad alanı, yöntem veya değişkenin adı olabilir. Belirtecin genel türü bir tanımlayıcı olabilir, ancak tanımlayıcı ne olduğuna ve nerede tanımlandığına bağlı olarak başka anlamlara da sahip olabilir. Bu kimlik, ayrıştırıcısının ayrıştırılmakta olan dil hakkında daha kapsamlı bilgi sahibi olmasını gerektirir. Burada <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfın geldiği yerdir. <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfı tanımlayıcılar, Yöntemler, eşleşen dil çiftleri (küme ayraçları ve parantezler gibi) ve dil Üçlü (örneğin, "`foreach()`" "`{`" ve "`}`") gibi üç bölüm olması dışında dil çiftlerine benzer bilgiler toplar. Ayrıca, hata ayıklayıcının yüklenmesi gerekmez ve bir programın hata ayıklaması yapıldığında otomatik olarak yerel değişkenleri ve parametreleri gösteren hata ayıklama penceresi ve ayrıştırıcıların **hata ayıklamaya** ek olarak uygun yerel değişkenleri ve parametreleri belirlemesine ihtiyaç duymak üzere, kod kimliğini desteklemek için <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfını geçersiz kılabilirsiniz.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesi, <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesinin bir parçası olarak ayrıştırıcıya geçirilir ve yeni bir <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesi her oluşturulduğunda yeni bir <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesi oluşturulur. Ayrıca <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi, çeşitli IntelliSense işlemlerini işlemek için kullanılan bir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnesi döndürmelidir. <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnesi bildirimler için bir liste ve ayrıştırma nedenine bağlı olarak, her biri doldurulmuş yöntemler için bir liste tutar. <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)