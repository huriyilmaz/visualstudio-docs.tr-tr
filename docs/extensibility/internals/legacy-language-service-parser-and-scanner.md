---
title: Eski dil hizmeti ayrıştırıcısı ve tarayıcısı | Microsoft Docs
description: Görüntülenen kodla ilgili bilgileri seçerek eski dil hizmeti ayrıştırıcısı ve tarayıcısı hakkında bilgi edinin.
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

|Belirteç Adı|Belirteç türü|
|----------------|----------------|
|Namespace, Class, Public, void, int|sözcükle|
|=|işleç|
|{ } ( ) ;|sınırlayıcı|
|MyNamespace, MyClass, MyFunction, arg1, var1|tanımlayıcı|
|MyNamespace|ad alanı|
|Sınıfım|sınıf|
|MyFunction|method|
|arg1|parametre|
|var1|Yerel değişken|

 Ayrıştırıcısının rolü belirteçleri belirlemektir. Bazı belirteçlerin birden fazla türü olabilir. Ayrıştırıcı belirteçleri tanımladıktan sonra dil hizmeti, söz dizimi vurgulaması, küme ayracı eşleştirme ve IntelliSense işlemleri gibi yararlı özellikler sağlamak için bu bilgileri kullanabilir.

## <a name="types-of-parsers"></a>Ayrıştırıcıları türleri
 Dil hizmeti ayrıştırıcısı, bir derleyicinin parçası olarak kullanılan bir ayrıştırıcıyla aynı değildir. Ancak, bu tür bir ayrıştırıcıda bir derleyici ayrıştırıcıyla aynı şekilde hem tarayıcı hem de ayrıştırıcı kullanması gerekir.

- Bir tarayıcı, belirteç türlerini belirlemek için kullanılır. Bu bilgiler, söz dizimi vurgulaması için ve diğer işlemleri tetikleyebilecek (ayraç eşleştirme gibi) belirteç türlerini hızlı bir şekilde tanımlamak için kullanılır. Bu tarayıcı arabirim tarafından temsil edilir <xref:Microsoft.VisualStudio.Package.IScanner> .

- Bir Ayrıştırıcı, belirteçlerin işlevlerini ve kapsamını tanımlamakta kullanılır. Bu bilgiler, IntelliSense işlemlerinde Yöntemler, değişkenler, parametreler ve bildirimler gibi dil öğelerini tanımlamak ve bağlam temelinde üye ve yöntem imzaları listeleri sağlamak için kullanılır. Bu ayrıştırıcı Ayrıca, parantez ve parantezler gibi eşleşen dil öğesi çiftlerini bulmak için de kullanılır. Bu ayrıştırıcıya <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sınıfındaki yöntemi aracılığıyla erişilir <xref:Microsoft.VisualStudio.Package.LanguageService> .

  Dil hizmetiniz için bir tarayıcıyı ve ayrıştırıcısı nasıl uygulayacağınızı öğrenin. Çözümleyicilerin nasıl çalıştığını ve kendi ayrıştırıcılarınızın nasıl yazılacağını betimleyen birkaç kaynak vardır. Ayrıca, bir Ayrıştırıcı oluşturmaya yardımcı olan çeşitli ücretsiz ve ticari ürünler de mevcuttur.

### <a name="the-parsesource-parser"></a>ParseSource ayrıştırıcısı
 Bir derleyicinin parçası olarak kullanılan bir Ayrıştırıcıdan farklı olarak (belirteçlerin bazı yürütülebilir kod biçimine dönüştürülebildiği) farklı nedenlerden dolayı bir dil hizmeti ayrıştırıcısı çağrılabilir ve birçok farklı bağlamda. Bu yaklaşımı, sınıfındaki yönteminde nasıl uygulayacağınızı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> görürsünüz. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntemin bir arka plan iş parçacığında çağrılabilir olabileceğini aklınızda bulundurmanız önemlidir.

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest>Yapı, nesnesine bir başvuru içerir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne arka plan iş parçacığında kullanılamaz. Aslında, temel MPF sınıflarının birçoğu arka plan iş parçacığında kullanılamaz. Bunlar,, <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> sınıfları ve görünümle doğrudan veya dolaylı olarak iletişim kuran diğer herhangi bir sınıfı içerir.

 Bu ayrıştırıcı genellikle ilk kez çağrıldığında veya ayrıştırma neden değeri verildiğinde kaynak dosyanın tamamını ayrıştırır <xref:Microsoft.VisualStudio.Package.ParseReason> . Yöntemine yapılan sonraki çağrılar, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırılmış kodun küçük bir kısmını işler ve önceki tam Ayrıştırma işleminin sonuçları kullanılarak çok daha hızlı yürütülebilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntemi, ve nesneleri aracılığıyla ayrıştırma işleminin sonuçlarını iletişim kurar <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> . <xref:Microsoft.VisualStudio.Package.AuthoringSink>Nesnesi, belirli bir ayrıştırma nedenine ilişkin bilgileri toplamak için kullanılır; Örneğin, eşleşen küme ayraçları veya parametre listelerine sahip Yöntem imzalarının yayılmaları hakkındaki bilgiler. , <xref:Microsoft.VisualStudio.Package.AuthoringScope> Bildirim ve yöntem imzaları koleksiyonlarını sağlar ve ayrıca gelişmiş Düzenle git seçeneği için de destek sağlar (**tanıma** git, **bildirime** git, **başvuruya git**).

### <a name="the-iscanner-scanner"></a>IScanner tarayıcısı
 Ayrıca, uygulayan bir tarayıcı uygulamalısınız <xref:Microsoft.VisualStudio.Package.IScanner> . Bununla birlikte, bu tarayıcı sınıfı aracılığıyla bir satır temelinde çalıştığından <xref:Microsoft.VisualStudio.Package.Colorizer> , genellikle daha kolay bir şekilde uygulanır. Her satırın başlangıcında MPF, <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfa, tarayıcıya geçirilen bir durum değişkeni olarak kullanılacak bir değer verir. Her satırın sonunda, tarayıcı güncelleştirilmiş durum değişkenini döndürür. MPF bu durum bilgilerini her satır için önbelleğe alır, böylece tarayıcı kaynak dosyanın başlangıcında başlatmaya gerek kalmadan herhangi bir satırdan ayrıştırmaya başlayabilir. Tek bir satırın hızlı taraması, düzenleyicinin kullanıcıya hızlı geri bildirim sağlamasına olanak tanır.

## <a name="parsing-for-matching-braces"></a>Eşleşen küme ayraçları için ayrıştırma
 Bu örnek, kullanıcının yazdığı bir kapanış ayracı ile eşleşen denetim akışını gösterir. Bu süreçte, belirtecin türünü ve belirtecin bir eşleştirme ayracı işlemini tetikleyemeyeceğini anlamak için renklendirme için kullanılan tarayıcı da kullanılır. Tetikleyici bulunursa, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> eşleşen küme ayracını bulmak için yöntemi çağırılır. Son olarak, iki küme ayracı vurgulanır.

 Küme ayraçları Tetikleyiciler ve ayrıştırma nedenlerinin adlarında kullanılmasına karşın, bu işlem gerçek küme ayraçları ile sınırlı değildir. Eşleşen bir çift olarak belirtilen tüm karakter çiftleri desteklenir. Örnekler şunlardır (ve), \< and > , ve [ve].

 Dil hizmetinin eşleşen ayraçları desteklediğini varsayın.

1. Kullanıcı bir kapanış küme ayracı (}).

2. Küme ayracı, kaynak dosyadaki imlece eklenir ve imleç bir tarafından ilerlemiş olur.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Sınıfındaki yöntemi, <xref:Microsoft.VisualStudio.Package.Source> türü belirlenmiş kapanış ayracı ile çağırılır.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Yöntemi, <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> <xref:Microsoft.VisualStudio.Package.Source> geçerli imleç konumundan hemen önceki konumda belirteci almak için sınıfındaki yöntemini çağırır. Bu belirteç, türü belirlenmiş kapanış ayracı ' ne karşılık gelir).

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Yöntemi, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> <xref:Microsoft.VisualStudio.Package.Colorizer> geçerli satırdaki tüm belirteçleri almak için nesnesine yöntemini çağırır.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Yöntemi <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> nesne üzerindeki yöntemini <xref:Microsoft.VisualStudio.Package.IScanner> geçerli satırın metniyle çağırır.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Yöntemi, <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> <xref:Microsoft.VisualStudio.Package.IScanner> geçerli satırdaki tüm belirteçleri toplamak için nesne üzerinde yöntemi tekrar tekrar çağırır.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Yöntemi, <xref:Microsoft.VisualStudio.Package.Source> istenen konumu içeren belirteci almak için sınıfında özel bir yöntemi çağırır ve yönteminden edinilen belirteçleri listesinde geçirir <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> .

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Yöntemi, yönteminden döndürülen belirteçte belirteç tetikleyici bayrağını arar <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> ; diğer bir deyişle, kapatma küme ayracını temsil eden belirteç).

6. Tetikleyici bayrağı <xref:Microsoft.VisualStudio.Package.TokenTriggers> bulunursa, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.Source> sınıfındaki yöntemi çağrılır.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>Yöntemi ayrıştırma nedeni değeri ile bir ayrıştırma işlemi başlatır <xref:Microsoft.VisualStudio.Package.ParseReason> . Bu işlem, sonuç <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olarak sınıfında yöntemini çağırır <xref:Microsoft.VisualStudio.Package.LanguageService> . Zaman uyumsuz ayrıştırma etkinse yöntemine bu çağrı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bir arka plan iş parçacığında gerçekleşir.

8. Ayrıştırma işlemi bittiğinde sınıfında adlı bir iç tamamlama işleyicisi (geri çağırma yöntemi olarak da bilinir) `HandleMatchBracesResponse` çağırılır <xref:Microsoft.VisualStudio.Package.Source> . Bu çağrı, <xref:Microsoft.VisualStudio.Package.LanguageService> ayrıştırıcının değil, temel sınıf tarafından otomatik olarak yapılır.

9. `HandleMatchBracesResponse`Yöntemi, <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesinde depolanan nesneden yayılmalar listesini alır <xref:Microsoft.VisualStudio.Package.ParseRequest> . (Span, <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> kaynak dosyadaki bir dizi satırı ve karakteri belirten bir yapıdır.) Bu yayılmalar, genellikle her biri açma ve kapatma ayraçları için olmak üzere iki yayılma içerir.

10. `HandleBracesResponse`Yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesnesinde depolanan nesnesi üzerinde yöntemini çağırır <xref:Microsoft.VisualStudio.Package.ParseRequest> . Bu, verilen yayılmaları vurgular.

11. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>Özellik <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> etkinleştirilirse, `HandleBracesResponse` yöntemi, eşleşen yayılma tarafından dahil edilen metni alır ve durum çubuğunda o yayılma alanının ilk 80 karakterini görüntüler. Bu, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi, eşleşen çifte eşlik eden dil öğesini içeriyorsa en iyi şekilde geçerlidir. Daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> . özelliği.

12. Bitti.

### <a name="summary"></a>Özet
 Eşleşen küme ayraçları işlemi, genellikle basit dil öğesi çiftleri ile sınırlıdır. Eşleşen Üçlü öğeler (" `if(...)` ", " `{` " ve "" `}` veya " `else` ", " `{` " ve "") gibi daha karmaşık öğeler `}` , bir sözcük tamamlama işleminin parçası olarak vurgulanabilir. Örneğin, "else" sözcüğü tamamlandığında eşleşen " `if` " deyimi vurgulanmış olabilir. Bir dizi deyim varsa, bunların hepsi eşleşen küme ayraçları ile aynı `if` / `else if` mekanizma kullanılarak vurgulanır. Temel sınıf bunu şu şekilde zaten destekler: Tarayıcı, belirteç tetikleyici değerini, imleç konumundan önceki belirteç tetikleyici <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> değeriyle birleştirilmiş olarak iade eder.

 Daha fazla bilgi için [bkz. Eski Dil Hizmeti'de Küme Ayracı Eşleştirme.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

## <a name="parsing-for-colorization"></a>Renklendirme için Ayrıştırma
 Kaynak kodu renklendirme basit bir işlemdir, yalnızca belirteci türünü tanımlamanız ve bu türle ilgili renk bilgilerini iade edin. sınıfı, her belirteç hakkında renk bilgisi sağlamak için düzenleyici ile <xref:Microsoft.VisualStudio.Package.Colorizer> tarayıcı arasında aracı olarak davranır. sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> bir satırı renklendirmeye yardımcı olmak ve ayrıca kaynak dosyada tüm satırlar için durum bilgilerini <xref:Microsoft.VisualStudio.Package.IScanner> toplamak için nesnesini kullanır. MPF dil hizmeti sınıflarında, tarayıcıyla yalnızca arabirim üzerinden iletişim kura olduğundan sınıfın <xref:Microsoft.VisualStudio.Package.Colorizer> geçersiz kılınmalarına gerek <xref:Microsoft.VisualStudio.Package.IScanner> olmaz. sınıfında yöntemini geçersiz karak <xref:Microsoft.VisualStudio.Package.IScanner> arabirimini uygulayan <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> nesnesini <xref:Microsoft.VisualStudio.Package.LanguageService> sağlar.

 Tarayıcıya <xref:Microsoft.VisualStudio.Package.IScanner> yöntemi aracılığıyla bir kaynak kodu satırı <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> verilir. yöntemine <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> yapılan çağrılar, satırda belirteçler tükenene kadar sonraki belirteci almak için yinelenir. Renklendirme için, MPF tüm kaynak kodu satır dizisi olarak davranır. Bu nedenle tarayıcının, satır olarak gelen kaynakla başa çıkabilecek olması gerekir. Ayrıca, herhangi bir satır tarayıcıya herhangi bir zamanda geçirebilirsiniz ve tek garanti tarayıcının taranacak satırdan önceki satırdan durum değişkenlerini aldığıdır.

 sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> belirteç tetikleyicilerini tanımlamak için de kullanılır. Bu tetikleyiciler MPF'ye belirli bir belirteci sözcük tamamlama veya eşleşen küme ayraçları gibi daha karmaşık bir işlem başlatamaz. Bu tür tetikleyicileri tanımlamanın hızlı olması ve herhangi bir konumda gerçekleşmesi gereken bir durum olduğundan tarayıcı bu görev için en uygun olandır.

 Daha fazla bilgi için bkz. [Eski Dil Hizmeti'de Söz Dizimi Renklendirme.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

## <a name="parsing-for-functionality-and-scope"></a>İşlevsellik ve Kapsam için Ayrıştırma
 İşlevsellik ve kapsam için ayrıştırmak, yalnızca karşılaşılan belirteç türlerini tanımlamaktan daha fazla çaba gerektirir. Ayrıştırıcının yalnızca belirteç türünü değil aynı zamanda belirteci kullandığı işlevselliği de tanımlaması gerekir. Örneğin, tanımlayıcı yalnızca bir addır, ancak sizin dilinize göre tanımlayıcı bağlama bağlı olarak bir sınıfın, ad alanının, yöntemin veya değişkenin adı olabilir. Belirteci genel türü bir tanımlayıcı olabilir, ancak tanımlayıcının ne olduğu ve nerede tanımlandığına bağlı olarak başka anlamları da olabilir. Bu belirleme için ayrıştırıcının ayrıştıran dil hakkında daha kapsamlı bilgi sahibi olması gerekir. Sınıfı bu <xref:Microsoft.VisualStudio.Package.AuthoringSink> noktada devreye gelir. sınıfı tanımlayıcılar, yöntemler, eşleşen dil çiftleri (ayraçlar ve parantezler gibi) ve üç dil çifti (üç parça olması dışında dil çiftlerine benzer şekilde, örneğin, " " " " ve " ") hakkında bilgi <xref:Microsoft.VisualStudio.Package.AuthoringSink> `foreach()` `{` `}` toplar. Ayrıca, hata ayıklayıcının yüklenmek zorunda olmadığının erken doğrulanmasında kullanılan kod tanımlamasını desteklemek için sınıfını geçersiz kılabilirsiniz ve bir program hata ayıklarken yerel değişkenleri ve parametreleri otomatik olarak gösteren Otomatik hata ayıklama penceresi ile ayrıştırıcının hata ayıklayıcının ortaya attıklarına ek olarak uygun yerel değişkenleri ve parametreleri tanımlamasını <xref:Microsoft.VisualStudio.Package.AuthoringSink> gerektirir. 

 Nesnesi ayrıştırıcıya nesnesinin bir parçası olarak geçirildi ve yeni bir nesne her oluşturulduğunda <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> yeni bir nesne <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> oluşturulur. Ayrıca yöntemi, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> çeşitli <xref:Microsoft.VisualStudio.Package.AuthoringScope> IntelliSense işlemlerini işlemek için kullanılan bir nesnesi de getirmektedir. nesnesi, ayrıştırmanın nedene bağlı olarak her biri doldurulmuş olan yöntemler için bir liste ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> bildirimlerin listesini sürdürür. <xref:Microsoft.VisualStudio.Package.AuthoringScope>sınıfının uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
