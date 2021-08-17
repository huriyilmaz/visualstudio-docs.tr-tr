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
ms.openlocfilehash: 6ac6c0a4a0facc68496a2d51b23b6979ba8d9359
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110481"
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

- Belirteç türlerini tanımlamak için bir tarayıcı kullanılır. Bu bilgiler söz dizimi vurgulama ve diğer işlemleri tetikley uyan belirteç türlerini (örneğin, küme ayracı eşleştirme) hızla tanımlamak için kullanılır. Bu tarayıcı arabirimi tarafından temsil <xref:Microsoft.VisualStudio.Package.IScanner> edildi.

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
 Bu örnek, kullanıcının yazarak bir kapatma ayracı eşleştirmek için denetim akışını gösterir. Bu işlemde, renklendirme için kullanılan tarayıcı belirteci türünü ve belirteci bir eşleşme ayracı işlemi tetikleyenin olup olmadığını belirlemek için de kullanılır. Tetikleyici bulunursa eşleşen küme <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayracı bulmak için yöntemi çağrılır. Son olarak, iki ayraç vurgulanır.

 Küme ayraçları tetikleyicilerin ve ayrıştırma nedenlerinin adlarında kullanılıyor olsa da, bu işlem gerçek küme ayraçları ile sınırlı değildir. Eşleşen bir çift olarak belirtilen herhangi bir karakter çifti de desteklene. Örnekler arasında ( ve ), \< and > , ve [ ve ].

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
 Eşleşen küme ayraçları işlemi genellikle basit dil öğeleri çiftleri ile sınırlıdır. Üçlüleri eşleştirme gibi daha karmaşık öğeler (" `if(...)` ", " `{` " ve " `}` " ", veya " ", " " ve " "), sözcük tamamlama işlemi kapsamında `else` `{` `}` vurgulanır. Örneğin, "else" sözcüğü tamamlandığında eşleşen " `if` " deyimi vurgulanmış olabilir. Bir dizi deyim varsa, bunların hepsi eşleşen küme ayraçları ile aynı `if` / `else if` mekanizma kullanılarak vurgulanır. Temel sınıf bunu şu şekilde zaten destekler: Tarayıcı, belirteç tetikleyici değerini, imleç konumundan önce olan belirteci tetikleyici <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> değeriyle birlikte iade eder.

 Daha fazla bilgi için [bkz. Eski Dil Hizmeti'de Küme Ayracı Eşleştirme.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

## <a name="parsing-for-colorization"></a>Renklendirme için Ayrıştırma
 Kaynak kodu renklendirme basittir, yalnızca belirteci türünü tanımlamanız ve bu türle ilgili renk bilgilerini iade edin. sınıfı, her belirteç hakkında renk bilgisi sağlamak için düzenleyici ile <xref:Microsoft.VisualStudio.Package.Colorizer> tarayıcı arasında aracı olarak davranır. sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> bir satırı renklendirmeye yardımcı olmak ve ayrıca kaynak dosyada tüm satırlar için durum bilgilerini <xref:Microsoft.VisualStudio.Package.IScanner> toplamak için nesnesini kullanır. MPF dil hizmeti sınıflarında, tarayıcıyla yalnızca arabirim üzerinden iletişim kura olduğundan sınıfın <xref:Microsoft.VisualStudio.Package.Colorizer> geçersiz kılınmalarına gerek <xref:Microsoft.VisualStudio.Package.IScanner> olmaz. sınıfında yöntemini geçersiz karak <xref:Microsoft.VisualStudio.Package.IScanner> arabirimini uygulayan <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> nesnesini <xref:Microsoft.VisualStudio.Package.LanguageService> sağlar.

 Tarayıcıya <xref:Microsoft.VisualStudio.Package.IScanner> yöntemi aracılığıyla bir kaynak kodu satırı <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> verilir. yöntemine <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> yapılan çağrılar, satırda belirteçler tükenene kadar sonraki belirteci almak için yinelenir. Renklendirme için, MPF tüm kaynak kodu satır dizisi olarak davranır. Bu nedenle tarayıcının, satır olarak gelen kaynakla başa çıkabilecek olması gerekir. Ayrıca, herhangi bir satır tarayıcıya herhangi bir zamanda geçirebilirsiniz ve tek garanti tarayıcının taranacak satırdan önceki satırdan durum değişkenlerini aldığıdır.

 sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> belirteç tetikleyicilerini tanımlamak için de kullanılır. Bu tetikleyiciler MPF'ye belirli bir belirteci sözcük tamamlama veya eşleşen küme ayraçları gibi daha karmaşık bir işlem başlatamaz. Bu tür tetikleyicileri tanımlamanın hızlı olması ve herhangi bir konumda gerçekleşmesi gereken bir durum olduğundan tarayıcı bu görev için en uygun olandır.

 Daha fazla bilgi için bkz. [Eski Dil Hizmeti'de Söz Dizimi Renklendirme.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

## <a name="parsing-for-functionality-and-scope"></a>İşlevsellik ve Kapsam için Ayrıştırma
 İşlevsellik ve kapsam için ayrıştırmak, yalnızca karşılaşılan belirteç türlerini tanımlamaktan daha fazla çaba gerektirir. Ayrıştırıcının yalnızca belirteç türünü değil aynı zamanda belirteci kullandığı işlevselliği de tanımlaması gerekir. Örneğin, tanımlayıcı yalnızca bir addır, ancak sizin dilinize göre tanımlayıcı bağlama bağlı olarak bir sınıfın, ad alanının, yöntemin veya değişkenin adı olabilir. Belirteci genel türü bir tanımlayıcı olabilir, ancak tanımlayıcının ne olduğu ve nerede tanımlandığına bağlı olarak başka anlamları da olabilir. Bu belirleme, ayrıştırıcının ayrıştırilen dil hakkında daha kapsamlı bilgi sahibi olması gerekir. Sınıfı bu <xref:Microsoft.VisualStudio.Package.AuthoringSink> noktada devreye gelir. sınıfı tanımlayıcılar, yöntemler, eşleşen dil çiftleri (ayraçlar ve parantezler gibi) ve üç dil çifti (üç parça olması dışında dil çiftlerine benzer şekilde, örneğin, " " " " ve " ") hakkında bilgi <xref:Microsoft.VisualStudio.Package.AuthoringSink> `foreach()` `{` `}` toplar. Ayrıca, hata ayıklayıcının yüklenmek zorunda olmadığının erken doğrulanmasında kullanılan kod tanımlamasını desteklemek için sınıfını geçersiz kılabilirsiniz ve bir program hata ayıklarken yerel değişkenleri ve parametreleri otomatik olarak gösteren Otomatik hata ayıklama penceresi ile ayrıştırıcının hata ayıklayıcının ortaya attıklarına ek olarak uygun yerel değişkenleri ve parametreleri tanımlamasını <xref:Microsoft.VisualStudio.Package.AuthoringSink> gerektirir. 

 Nesnesi ayrıştırıcıya nesnesinin bir parçası olarak geçirildi ve yeni bir nesne her oluşturulduğunda <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> yeni bir nesne <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> oluşturulur. Ayrıca yöntemi, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> çeşitli <xref:Microsoft.VisualStudio.Package.AuthoringScope> IntelliSense işlemlerini işlemek için kullanılan bir nesnesi de getirmektedir. nesnesi, ayrıştırmanın nedene bağlı olarak her ikisinde de doldurulan yöntemler için bir liste ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> bildirimlerin listesini sürdürür. <xref:Microsoft.VisualStudio.Package.AuthoringScope>sınıfının uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
