---
title: Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcı | Microsoft Docs
description: Görüntülenen kodla ilgili bilgileri seçen eski dil hizmeti ayrıştırıcısı ve tarayıcısı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 81b8df95ca4bdad98cb2fdceaae0c6178cefcbccc210e5a62b459bffa6481d21
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447967"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı
Ayrıştırıcı, dil hizmetinin merkezindedir. Yönetilen Paket Çerçevesi (MPF) dil sınıfları, görüntülenen kod hakkında bilgi seçmek için bir dil ayrıştırıcı gerektirir. Ayrıştırıcı, metni sözcük belirteçlerine ayırarak bu belirteçleri türe ve işlevlere göre tanımlar.

## <a name="discussion"></a>Tartışma
 Aşağıdaki bir C# yöntemidir.

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

 Bu örnekte belirteçler sözcükler ve noktalama işaretleridir. Belirteç türleri aşağıdaki gibidir.

|Belirteç Adı|Belirteç Türü|
|----------------|----------------|
|namespace, class, public, void, int|Anahtar kelime|
|=|işleç|
|{ } ( ) ;|sınırlayıcı|
|MyNamespace, MyClass, MyFunction, arg1, var1|tanımlayıcı|
|MyNamespace|ad alanı|
|Myclass|sınıf|
|Myfunction|method|
|arg1|parametre|
|var1|yerel değişken|

 Ayrıştırıcının rolü belirteçleri tanımlamaktır. Bazı belirteçlerin birden fazla türü olabilir. Ayrıştırıcı belirteçleri belirledikten sonra dil hizmeti söz dizimi vurgulama, küme ayracı eşleştirme ve IntelliSense işlemleri gibi yararlı özellikler sağlamak için bilgileri kullanabilir.

## <a name="types-of-parsers"></a>Ayrıştırıcı türleri
 Dil hizmeti ayrıştırıcısı, derleyicinin parçası olarak kullanılan ayrıştırıcıyla aynı değildir. Ancak, bu tür ayrıştırıcının derleyici ayrıştırıcısı ile aynı şekilde hem tarayıcı hem de ayrıştırıcı kullanması gerekir.

- Belirteç türlerini tanımlamak için bir tarayıcı kullanılır. Bu bilgiler söz dizimi vurgulaması ve küme ayracı eşleştirme gibi diğer işlemleri tetikley uyan belirteç türlerini hızlı bir şekilde tanımlamak için kullanılır. Bu tarayıcı arabirimi tarafından temsil <xref:Microsoft.VisualStudio.Package.IScanner> edildi.

- Ayrıştırıcı, belirteçlerin işlevlerini ve kapsamını açıklamak için kullanılır. Bu bilgiler IntelliSense işlemlerinde yöntemler, değişkenler, parametreler ve bildirim gibi dil öğelerini tanımlamak ve bağlama göre üye ve yöntem imzalarının listelerini sağlamak için kullanılır. Bu ayrıştırıcı ayraçlar ve parantezler gibi eşleşen dil öğesi çiftlerini bulmak için de kullanılır. Bu ayrıştırıcıya sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi aracılığıyla <xref:Microsoft.VisualStudio.Package.LanguageService> erişilir.

  Dil hizmetiniz için tarayıcı ve ayrıştırıcı uygulamanız size bağlı. Ayrıştırıcıların nasıl çalışa ve kendi ayrıştırıcınızı nasıl yazacaklarını açıklayan çeşitli kaynaklar mevcuttur. Ayrıca ayrıştırıcı oluşturmaya yardımcı olan çeşitli ücretsiz ve ticari ürünler de mevcuttur.

### <a name="the-parsesource-parser"></a>ParseSource Ayrıştırıcısı
 Derleyicinin bir parçası olarak kullanılan ayrıştırıcıdan (belirteçlerin bir yürütülebilir kod biçimine dönüştürülmesi) farklı olarak dil hizmeti ayrıştırıcısı birçok farklı nedenle ve birçok farklı bağlamda çağrılabilir. sınıfındaki yönteminde bu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yaklaşımı nasıl <xref:Microsoft.VisualStudio.Package.LanguageService> uygulayacakları size göredir. Yöntemin bir arka plan iş <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parçacığında çağrıl olabileceğini unutmayın.

> [!CAUTION]
> Yapı, <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesine bir başvuru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> içerir. Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne arka plan iş parçacığında kullanılamaz. Aslında, temel MPF sınıflarının çoğu arka plan iş parçacığında kullanılamaz. Bunlar , , sınıfları ve görünümle doğrudan veya dolaylı olarak iletişim <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> kuran diğer sınıfları içerir.

 Bu ayrıştırıcı genellikle kaynak dosyanın tamamını ilk çağrıldık veya ayrıştırma nedeni değeri verildi olduğunda <xref:Microsoft.VisualStudio.Package.ParseReason> ayrıştırır. Yöntemine yapılan sonraki çağrılar ayrıştıran kodun küçük bir kısmını işler ve önceki tam ayrıştırma işlemi sonuçları kullanılarak <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> çok daha hızlı yürütülebilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>yöntemi, ayrıştırma işlemi sonuçlarını ve nesneleri aracılığıyla <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> iletir. nesnesi, belirli bir ayrıştırma nedeni için bilgi toplamak için kullanılır; örneğin, eşleşen küme ayraçlarının veya parametre listelerine sahip yöntem imzalarının <xref:Microsoft.VisualStudio.Package.AuthoringSink> yayılmaları hakkında bilgi. , bildirimlerin ve yöntem imzalarının koleksiyonlarını sağlar ve gelişmiş düzenleme seçeneğine git ( Tanıma Git , Bildirime Git , Başvuruya <xref:Microsoft.VisualStudio.Package.AuthoringScope> **Git) için de destek sağlar.** 

### <a name="the-iscanner-scanner"></a>IScanner Tarayıcısı
 ayrıca uygulayan bir tarayıcı da <xref:Microsoft.VisualStudio.Package.IScanner> uygulamalısiniz. Ancak, bu tarayıcı sınıf aracılığıyla satır satır çalışır, <xref:Microsoft.VisualStudio.Package.Colorizer> genellikle daha kolay uygulanır. Her satırın başında, MPF sınıfına tarayıcıya geçirilen bir durum değişkeni olarak <xref:Microsoft.VisualStudio.Package.Colorizer> kullanmak üzere bir değer verir. Tarayıcı, her satırın sonunda güncelleştirilmiş durum değişkenlerini döndürür. MPF, tarayıcının kaynak dosyanın başlangıcından başlamak zorunda kalmadan herhangi bir satırdan ayrıştırmaya başlay önbelleğe almak için bu durum bilgilerini her satır için önbelleğe almaktadır. Tek bir satırın bu hızlı taraması, düzenleyicinin kullanıcıya hızlı geri bildirim sağlamalarını sağlar.

## <a name="parsing-for-matching-braces"></a>Eşleşen Küme Ayraçları için Ayrıştırma
 Bu örnek, kullanıcının yazarak bir kapatma ayracı eşleştirmek için denetim akışını gösterir. Bu işlemde, renklendirme için kullanılan tarayıcı ayrıca belirteci türünü ve belirteci bir eşleşme ayracı işlemini tetikleyip tetikleye olmadığını belirlemek için kullanılır. Tetikleyici bulunursa, eşleşen <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> küme ayracı bulmak için yöntemi çağrılır. Son olarak, iki ayraç vurgulanır.

 Küme ayraçları tetikleyicilerin ve ayrıştırma nedenlerinin adlarında kullanılıyor olsa da, bu işlem gerçek küme ayraçları ile sınırlı değildir. Eşleşen bir çift olarak belirtilen herhangi bir karakter çifti de desteklene. Örnek olarak ( ve ), \< and > , ve [ ve ].

 Dil hizmetinin eşleşen ayraçları desteklediğini varsayalım.

1. Kullanıcı kapanış küme ayracı (}) türüne sahip.

2. Küme ayracı, kaynak dosyada imlecin üzerine eklenir ve imleç tek tek gelişmiştir.

3. sınıfındaki <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> yöntemi, türü verilen kapanış ayracı ile çağrılır.

4. yöntemi, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> geçerli <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> imleç <xref:Microsoft.VisualStudio.Package.Source> konumundan hemen önce konumdaki belirteci almak için sınıfındaki yöntemini arar. Bu belirteç, türü yazmalı kapanış ayracına karşılık gelen).

    1. yöntemi, <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> geçerli <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> satırda tüm <xref:Microsoft.VisualStudio.Package.Colorizer> belirteçleri almak için nesne üzerinde yöntemini çağırıyor.

    2. yöntemi, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> geçerli <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> satırın <xref:Microsoft.VisualStudio.Package.IScanner> metniyle nesnesinde yöntemini arar.

    3. yöntemi, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> geçerli satırdan <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> tüm belirteçleri toplamak için nesne üzerinde yöntemini <xref:Microsoft.VisualStudio.Package.IScanner> tekrar tekrar çağırıyor.

    4. yöntemi, istenen konumu içeren belirteci almak için sınıfındaki özel bir yöntemi çağırarak yönteminden alınan <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> <xref:Microsoft.VisualStudio.Package.Source> belirteçler <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> listesinden geçer.

5. yöntemi, yönteminden döndürülen belirteçte bir belirteç tetikleyici bayrağını, yani kapanış ayracı <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.TokenTriggers> temsil eden <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> belirteci) ayalar.

6. tetikleyici bayrağı <xref:Microsoft.VisualStudio.Package.TokenTriggers> bulunursa <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> sınıfındaki yöntemi <xref:Microsoft.VisualStudio.Package.Source> çağrılır.

7. yöntemi, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> ayrıştırma nedeni değeriyle bir ayrıştırma işlemi <xref:Microsoft.VisualStudio.Package.ParseReason> başlatır. Bu işlem sonunda sınıfında <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService> çağırtır. Zaman uyumsuz ayrıştırma etkinse, yöntemine yapılan bu çağrı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bir arka plan iş parçacığında gerçekleşir.

8. Ayrıştırma işlemi tamamlandığında sınıfında adlı bir iç tamamlama işleyicisi (geri çağırma yöntemi `HandleMatchBracesResponse` olarak da bilinir) <xref:Microsoft.VisualStudio.Package.Source> çağrılır. Bu çağrı ayrıştırıcı tarafından <xref:Microsoft.VisualStudio.Package.LanguageService> değil, temel sınıf tarafından otomatik olarak yapılır.

9. `HandleMatchBracesResponse`yöntemi, nesnesinde depolanan nesneden <xref:Microsoft.VisualStudio.Package.AuthoringSink> yayılanların listesini <xref:Microsoft.VisualStudio.Package.ParseRequest> elde eder. (Yayma, <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> kaynak dosyada satır ve karakter aralığını belirten bir yapıdır.) Bu yayma listesi genellikle açma ve kapatma küme ayraçları için bir tane olmak için iki aralık içerir.

10. yöntemi, `HandleBracesResponse` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> nesnesinde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> depolanan nesnesinde yöntemini <xref:Microsoft.VisualStudio.Package.ParseRequest> arar. Bu, verilen aralıkları vurgular.

11. Özelliğin etkinleştirilmesi durumunda yöntemi eşleşen aralığın kapsamış olduğu metni elde edilir ve durum çubuğunda bu aralığın <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> ilk `HandleBracesResponse` 80 karakteri görüntülenir. Yöntem eşleşen <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> çifte eşlik ediyor dil öğesini içerirse bu en iyi şekilde çalışır. Daha fazla bilgi için özelliğine <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> bakın.

12. Bitti.

### <a name="summary"></a>Özet
 Eşleşen küme ayraçları işlemi genellikle basit dil öğeleri çiftleri ile sınırlıdır. Üçlüleri eşleştirme gibi daha karmaşık öğeler (" `if(...)` ", `{` " " ve " `}` " ", veya " ", " " ve " "), sözcük tamamlama işlemi kapsamında `else` `{` `}` vurgulanır. Örneğin, "Else" sözcüğü bittiğinde, eşleşen " `if` " ifadesini vurgulanabilir. Bir dizi `if` / `else if` deyim varsa, bunların hepsi eşleşen küme ayraçları ile aynı mekanizmaya göre vurgulanacaktır. <xref:Microsoft.VisualStudio.Package.Source>Temel sınıf, bunu aşağıdaki şekilde zaten destekler: tarayıcı, <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> imleç konumundan önce olan belirtecin tetikleyici değeriyle birleştirilmiş belirteç tetikleyici değerini döndürmelidir.

 Daha fazla bilgi için bkz. [eski dil hizmetinde küme ayracı eşleme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Renklendirme için ayrıştırma
 Kaynak kodu renklendirme basittir, belirtecin türünü ve bu türle ilgili dönüş renk bilgilerini belirlemeniz yeterlidir. <xref:Microsoft.VisualStudio.Package.Colorizer>Sınıfı, her belirteçle ilgili renk bilgilerini sağlamak için düzenleyici ve tarayıcı arasında aracı işlevi görür. <xref:Microsoft.VisualStudio.Package.Colorizer>Sınıfı, <xref:Microsoft.VisualStudio.Package.IScanner> bir satırı renklendirime ve ayrıca kaynak dosyadaki tüm satırların durum bilgilerini toplama konusunda yardımcı olmak için nesnesini kullanır. MPF dil hizmeti sınıflarında, <xref:Microsoft.VisualStudio.Package.Colorizer> yalnızca arabirim aracılığıyla tarayıcıyla iletişim kurduğu için sınıfın geçersiz kılınması gerekmez <xref:Microsoft.VisualStudio.Package.IScanner> . <xref:Microsoft.VisualStudio.Package.IScanner>Sınıfında yöntemini geçersiz kılarak arabirimini uygulayan nesneyi sağlarsınız <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> .

 <xref:Microsoft.VisualStudio.Package.IScanner>Tarayıcıya, yöntemi aracılığıyla bir kaynak kodu satırı verilir <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> . Yöntemine yapılan çağrılar, satır <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> belirteçlerin tükenene kadar satırdaki bir sonraki belirteci almak için yinelenir. Renklendirme için MPF tüm kaynak kodlarını satır dizisi olarak değerlendirir. Bu nedenle, tarayıcı, kaynak olarak bu kaynağa gelen kaynak ile Cope sağlamalıdır. Bunlara ek olarak, herhangi bir zamanda tarayıcıya herhangi bir zaman geçirilebilir ve tek garanti, tarayıcının durum değişkenini taranmadan önceki satırdan almasını sağlar.

 <xref:Microsoft.VisualStudio.Package.Colorizer>Sınıf, belirteç tetikleyicilerini belirlemek için de kullanılır. Bu Tetikleyiciler, MPF 'ye belirli bir belirtecin sözcük tamamlama veya eşleşen küme ayraçları gibi daha karmaşık bir işlem başlatabileceğini söyler. Bu tür Tetikleyiciler hızlı olması ve herhangi bir konumda gerçekleşmesi gerektiğinden, tarayıcı bu görev için en uygun seçenektir.

 Daha fazla bilgi için, bkz. [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Işlevsellik ve kapsam için ayrıştırma
 İşlevsellik ve kapsam için ayrıştırma, yalnızca karşılaşılan belirteç türlerini tanımlamaya kıyasla daha fazla çaba gerektirir. Ayrıştırıcının yalnızca belirteç türünü değil, belirtecin kullanıldığı işlevselliği de belirlemesi gerekir. Örneğin, bir tanımlayıcı yalnızca bir addır, ancak dilinizde bir tanımlayıcı, içeriğe bağlı olarak bir sınıf, ad alanı, yöntem veya değişkenin adı olabilir. Belirtecin genel türü bir tanımlayıcı olabilir, ancak tanımlayıcı ne olduğuna ve nerede tanımlandığına bağlı olarak başka anlamlara da sahip olabilir. Bu kimlik, ayrıştırıcısının ayrıştırılmakta olan dil hakkında daha kapsamlı bilgi sahibi olmasını gerektirir. Bu, <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfının içinde geldiği yerdir. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Sınıfı tanımlayıcılar, Yöntemler, eşleşen dil çiftleri (küme ayraçları ve parantezler gibi) ve dil Üçlü (örneğin, "" "" `foreach()` `{` ve "") gibi üç bölüm olması dışında dil çiftlerine benzer bilgiler toplar `}` . Ayrıca, <xref:Microsoft.VisualStudio.Package.AuthoringSink> bir programın hata ayıklaması yapıldığında otomatik olarak yerel değişkenleri ve parametreleri gösteren ve ayrıştırıcıların hata **ayıklamasına** ek olarak uygun yerel değişkenleri ve parametreleri belirlemesine olanak tanımak için, kesme noktalarının erken doğrulanmasında kullanılan kod kimliğini desteklemek için sınıfını geçersiz kılabilirsiniz.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Nesne, nesnenin bir parçası olarak ayrıştırıcıya geçirilir <xref:Microsoft.VisualStudio.Package.ParseRequest> ve <xref:Microsoft.VisualStudio.Package.AuthoringSink> her yeni nesne oluşturulduğunda yeni bir nesne oluşturulur <xref:Microsoft.VisualStudio.Package.ParseRequest> . Ayrıca, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemin <xref:Microsoft.VisualStudio.Package.AuthoringScope> çeşitli IntelliSense işlemlerini işlemek için kullanılan bir nesnesi döndürmesi gerekir. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Nesnesi bildirimler için bir liste ve ayrıştırma nedenine bağlı olarak, her biri doldurulmuş yöntemler için bir liste tutar. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Sınıfın uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
