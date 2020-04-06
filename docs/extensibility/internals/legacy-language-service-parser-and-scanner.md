---
title: Eski Dil Servisi Parser ve Tarayıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707322"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı
Ayrıştırıcı, dil servisinin kalbidir. Yönetilen Paket Çerçevesi (MPF) dil sınıfları, görüntülenen kod hakkında bilgi seçmek için bir dil parer gerektirir. Bir ayrıştırıcı metni sözlü belirteçlere ayırır ve sonra bu belirteçleri türüne ve işlevselliğe göre tanımlar.

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

 Bu örnekte, belirteçleri sözcükler ve noktalama işaretleri vardır. Belirteçleri türleri aşağıdaki gibidir.

|Belirteç Adı|Belirteç Türü|
|----------------|----------------|
|ad alanı, sınıf, genel, geçersiz, int|Anahtar kelime|
|=|operator|
|{ } ( ) ;|sınırlayıcı|
|MyNamespace, MyClass, MyFunction, arg1, var1|tanımlayıcı|
|MyNamespace|ad alanı|
|Myclass|sınıf|
|Myfunction|method|
|arg1|parametre|
|var1|yerel değişken|

 Ayrıştırıcının rolü belirteçleri tanımlamaktır. Bazı belirteçlerin birden fazla türü olabilir. Parser belirteçleri tanımladıktan sonra, dil hizmeti sözdizimi vurgulama, ayraç eşleştirme ve IntelliSense işlemleri gibi yararlı özellikler sağlamak için bilgileri kullanabilirsiniz.

## <a name="types-of-parsers"></a>Ayrışdırıcı Çeşitleri
 Dil hizmeti ayırıcısı, derleyicinin bir parçası olarak kullanılan bir parçalayıcıyla aynı değildir. Ancak, bu tür bir ayrıştırıcı, derleyici parleyici olarak aynı şekilde, hem bir tarayıcı ve bir ayrıştırıcı kullanmanız gerekir.

- Bir tarayıcı belirteçleri türlerini tanımlamak için kullanılır. Bu bilgiler sözdizimi vurgulama ve diğer işlemleri tetikleyebilir belirteç türlerini hızlı bir şekilde tanımlamak için kullanılır( örneğin, ayraç eşleme. Bu tarayıcı <xref:Microsoft.VisualStudio.Package.IScanner> arabirim tarafından temsil edilir.

- Belirteçlerin işlevlerini ve kapsamını tanımlamak için bir parser kullanılır. Bu bilgiler IntelliSense işlemlerinde yöntemler, değişkenler, parametreler ve bildirimler gibi dil öğelerini tanımlamak ve içeriğe dayalı üye ve yöntem imzaları listelerini sağlamak için kullanılır. Bu ayrıştırıcı, ayraçlar ve parantezler gibi eşleşen dil öğesi çiftleri bulmak için de kullanılır. Bu ayrıştırıcı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfta yöntem üzerinden erişilir.

  Dil hizmetiniz için tarayıcı ve ayrıştırıcıyı nasıl uygulayacağınız size kalmış. Ayrıştırıcıların nasıl çalıştığını ve kendi parer'inizi nasıl yazılanızı açıklayan çeşitli kaynaklar mevcuttur. Ayrıca, birkaç ücretsiz ve ticari ürünler bir parser oluşturmada yardımcı mevcuttur.

### <a name="the-parsesource-parser"></a>The ParseSource Parser
 Bir derleyicinin parçası olarak kullanılan (belirteçlerin bir tür yürütülebilir kodbiçimine dönüştürüldüğü) bir arayıcısının aksine, bir dil hizmeti aralayıcısı birçok farklı nedenden ve birçok farklı bağlamda çağrılabilir. <xref:Microsoft.VisualStudio.Package.LanguageService> Sınıfta yöntembu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yaklaşımı nasıl uygularsanız size kalmış. Yöntemin <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> bir arka plan iş parçacığı üzerinde çağrılabileceğini akılda tutmak önemlidir.

> [!CAUTION]
> Yapı <xref:Microsoft.VisualStudio.Package.ParseRequest> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesneye bir başvuru içerir. Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne arka plan iş parçacığı kullanılamaz. Aslında, temel MPF sınıflarının çoğu arka plan iş parçacığı nda kullanılamaz. Bunlar, <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , sınıflar ve doğrudan veya dolaylı olarak görünümü ile iletişim kurar başka bir sınıf içerir.

 Bu ayrıştırıcı genellikle ilk çağrıldığında veya ayrıştırıcı neden değeri <xref:Microsoft.VisualStudio.Package.ParseReason> verildiğinde tüm kaynak dosyasını ayrıştırır. Yönteme <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sonraki çağrılar ayrıştırılmış kodun küçük bir bölümünü işler ve önceki tam ayrıştırıcı işleminin sonuçlarını kullanarak çok daha hızlı bir şekilde yürütülebilir. Yöntem, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştma işleminin sonuçlarını nesneler <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> aracılığıyla ileter. Nesne, <xref:Microsoft.VisualStudio.Package.AuthoringSink> belirli bir ayrıştırma nedeni için bilgi toplamak için kullanılır, örneğin, eşleşen ayraçların veya parametre listeleri olan yöntem imzalarının yayılma ları hakkında bilgi. Bildirimlerin <xref:Microsoft.VisualStudio.Package.AuthoringScope> ve yöntem imzalarının koleksiyonlarını sağlar ve ayrıca Gelişmiş Edit e git seçeneği **(Tanıya Git**, **Bildirgeye Git**, **Başvuruya Git**) için destek sağlar.

### <a name="the-iscanner-scanner"></a>iScanner Tarayıcı
 Ayrıca uygulayan bir tarayıcı uygulamanız <xref:Microsoft.VisualStudio.Package.IScanner>gerekir. Ancak, bu tarayıcı <xref:Microsoft.VisualStudio.Package.Colorizer> sınıf boyunca satır satır çalıştığından, uygulanması genellikle daha kolaydır. Her satırın başında, MPF <xref:Microsoft.VisualStudio.Package.Colorizer> sınıftarayıcıya geçirilen bir durum değişkeni olarak kullanılacak bir değer verir. Her satırın sonunda, tarayıcı güncelleştirilmiş durum değişkenini döndürür. MPF, tarayıcının kaynak dosyanın başında niçin başlamak zorunda kalmadan herhangi bir satırdan ayrıştırmaya başlayabilmeleri için her satır için bu durum bilgilerini önbelleğe alar. Tek bir satırın bu hızlı taranması, düzenleyicinin kullanıcıya hızlı geri bildirim sağlamasına olanak tanır.

## <a name="parsing-for-matching-braces"></a>Eşleşen Ayraçlar için Ayrışma
 Bu örnek, kullanıcının yazdığı bir kapanış ayracıyla eşleştirme için denetim akışını gösterir. Bu işlemde, renklendirme için kullanılan tarayıcı da belirteç türünü belirlemek için kullanılır ve belirteç bir eşleştirme ayraç işlemi tetikleyebilir. Tetikleyici bulunursa, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> eşleşen ayraç bulmak için yöntem çağrılır. Son olarak, iki parantez vurgulanır.

 Ayraçlar tetikleyiciler ve ayrıştırma nedenlerinin adlarında kullanılsa da, bu işlem gerçek ayraçlarla sınırlı değildir. Eşleşen bir çift olarak belirtilen herhangi bir karakter çifti desteklenir. Örnekler şunlardır \< ( ve ), ve >, ve [ ve ].

 Dil hizmetinin eşleşen ayraçları desteklediğini varsayalım.

1. Kullanıcı kapanış kıvırcık ayracı (}) olarak yıtipler.

2. Kıvırcık ayraç, kaynak dosyadaki imleçten eklenir ve imleç bir kişi tarafından ilerletilir.

3. Sınıftaki <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> yöntem, yazılan kapanış ayracıyla çağrılır.

4. Yöntem, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> geçerli <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> imleç <xref:Microsoft.VisualStudio.Package.Source> konumundan hemen önce belirteç leri konumda niçin elde etmek için sınıftaki yöntemi çağırır. Bu belirteç, yazılan kapanış ayracına karşılık gelir).

    1. Yöntem, <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> geçerli <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> satırdaki <xref:Microsoft.VisualStudio.Package.Colorizer> tüm belirteçleri elde etmek için nesne üzerindeki yöntemi çağırır.

    2. Yöntem, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> geçerli <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> satırın <xref:Microsoft.VisualStudio.Package.IScanner> metniyle nesne üzerindeki yöntemi çağırır.

    3. Yöntem, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> geçerli satırdaki <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> <xref:Microsoft.VisualStudio.Package.IScanner> tüm belirteçleri toplamak için nesne üzerindeki yöntemi art arda çağırır.

    4. Yöntem, <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> istenen konumu içeren <xref:Microsoft.VisualStudio.Package.Source> belirteci elde etmek için sınıfta özel bir yöntem çağırır ve <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yöntemden elde edilen belirteçler listesinde geçer.

5. Yöntem, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yöntemden döndürülen belirteç üzerinde bir belirteç tetikleyici bayrağı arar; diğer bir şey, kapanış ayracını temsil eden belirteçtir).

6. Tetikleyici bayrağı <xref:Microsoft.VisualStudio.Package.TokenTriggers> bulunursa, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> sınıftaki <xref:Microsoft.VisualStudio.Package.Source> yöntem çağrılır.

7. Yöntem <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> ayrıştırma neden değeri ile ayrıştırma işlemi <xref:Microsoft.VisualStudio.Package.ParseReason>başlar. Bu işlem sonuçta <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfta yöntem çağırır. Eşzamanlı ayrıştırma etkinleştirilmişse, yönteme <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yapılan bu çağrı bir arka plan iş parçacığı üzerinde gerçekleşir.

8. Ayrıştırma işlemi tamamlandığında, `HandleMatchBracesResponse` <xref:Microsoft.VisualStudio.Package.Source> sınıfta adı geçen bir iç tamamlama işleyicisi (geri arama yöntemi olarak da bilinir) çağrılır. Bu arama, ayrıştırıcı tarafından değil, <xref:Microsoft.VisualStudio.Package.LanguageService> taban sınıf tarafından otomatik olarak yapılır.

9. Yöntem, `HandleMatchBracesResponse` <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnede depolanan nesneden bir yayılma listesi alır. (Yayılma alanı, <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> kaynak dosyadaki satır ve karakter aralığını belirten bir yapıdır.) Bu yayılma listesi genellikle açılış ve kapanış ayraçları için birer tane olmak üzere iki açıklık içerir.

10. Yöntem, `HandleBracesResponse` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnede depolanan nesne üzerinde yöntem çağırır. Bu, verilen yayılma açıklıklarını vurgular.

11. <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Özellik <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> etkinse, `HandleBracesResponse` yöntem eşleşen açıktarafından kapsanan metni alır ve durum çubuğunda bu açıklının ilk 80 karakterini görüntüler. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntem eşleşen çifti eşlik eden dil öğesi içeriyorsa bu en iyi şekilde çalışır. Daha fazla bilgi <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> için tesise bakın.

12. Bitti.

### <a name="summary"></a>Özet
 Eşleşen ayraçişlemi genellikle basit dil öğeleri çiftleri ile sınırlıdır. Üçlü eşleştirme`if(...)`(" ", " "`{`ve "`}`",`else`" "`{`"`}`" ve " ") gibi daha karmaşık öğeler, sözcük tamamlama işleminin bir parçası olarak vurgulanabilir. Örneğin, "else" sözcüğü tamamlandığında , eşleşen`if`" " ifadesi vurgulanabilir. Bir dizi `if` / `else if` deyim olsaydı, bunların tümü eşleç ayraçlarla aynı mekanizma kullanılarak vurgulanabilir. Taban sınıf zaten aşağıdaki gibi bunu destekler: Tarayıcı imleç <xref:Microsoft.VisualStudio.Package.TokenTriggers> konumundan önce <xref:Microsoft.VisualStudio.Package.TokenTriggers> belirteç için tetikleme değeri ile birlikte belirteç tetikleme değerini döndürmelidir. <xref:Microsoft.VisualStudio.Package.Source>

 Daha fazla bilgi için, [Eski Dil Hizmetinde Ayraç Eşleştirme'ye](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)bakın.

## <a name="parsing-for-colorization"></a>Renklendirme için ayrışma
 Kaynak kodunu renklendirmek basittir, yalnızca belirteç türünü tanımlayın ve bu türle ilgili renk bilgilerini döndürün. Sınıf, <xref:Microsoft.VisualStudio.Package.Colorizer> her belirteç hakkında renk bilgisi sağlamak için düzenleyici ve tarayıcı arasında aracı görevi görür. Sınıf, <xref:Microsoft.VisualStudio.Package.Colorizer> bir <xref:Microsoft.VisualStudio.Package.IScanner> satırı renklendirmeye yardımcı olmak ve kaynak dosyadaki tüm satırlar için durum bilgilerini toplamak için nesneyi kullanır. MPF dil hizmeti sınıflarında, <xref:Microsoft.VisualStudio.Package.Colorizer> tarayıcıyla yalnızca <xref:Microsoft.VisualStudio.Package.IScanner> arabirim üzerinden iletişim kurduğundan sınıfın geçersiz kılınması gerekmez. Sınıfta yöntemi geçersiz kılarak <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> arabirimi uygulayan nesneyi sağlarsınız. <xref:Microsoft.VisualStudio.Package.LanguageService>

 Tarayıcı <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> yöntemi ile kaynak kodu bir satır verilir. <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Satır belirteçleri tükenene kadar satırdaki sonraki belirteci elde etmek için yönteme yapılan çağrılar yinelenir. Renklendirme için, MPF tüm kaynak kodunu bir satır dizisi olarak ele alar. Bu nedenle, tarayıcı satır olarak gelen kaynak ile başa çıkmak gerekir. Buna ek olarak, herhangi bir satır herhangi bir zamanda tarayıcıya geçirilebilir ve tek garanti tarayıcı nın taranmak üzere olan satırdan önce satırdan durum değişkenini almasıdır.

 Sınıf, <xref:Microsoft.VisualStudio.Package.Colorizer> belirteç tetikleyicilerini tanımlamak için de kullanılır. Bu tetikleyiciler MPF'ye belirli bir belirtecisözcük tamamlama veya eşleme ayraçları gibi daha karmaşık bir işlem başlatabileceğini söyler. Bu tür tetikleyicileri tanımlamahızlı olmalı ve herhangi bir konumda gerçekleşmesi gerekir, tarayıcı bu görev için en uygun.

 Daha fazla bilgi için, [Eski Dil Hizmetinde Sözdizimi Renklendirme'ye](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)bakın.

## <a name="parsing-for-functionality-and-scope"></a>İşlevsellik ve Kapsam Ayrıştisı
 İşlevsellik ve kapsam ayrıştMası, karşılaşılan belirteç türlerini tanımlamaktan daha fazla çaba gerektirir. Parser yalnızca belirteç türünü değil, aynı zamanda belirteci kullanılan işlevselliği tanımlamak zorundadır. Örneğin, tanımlayıcı sadece bir addır, ancak dilinizde bir tanımlayıcı içeriğe bağlı olarak bir sınıfın, ad alanının, yöntemin veya değişkenin adı olabilir. Belirteç genel türü bir tanımlayıcı olabilir, ancak tanımlayıcı da ne olduğuna ve nerede tanımlandığına bağlı olarak başka anlamları olabilir. Bu tanımlama, ayrıştırılan dil hakkında daha kapsamlı bilgiye sahip olması için ayrıştırıcıyı gerektirir. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Burası sınıfın devreye girdiği yer. Sınıf <xref:Microsoft.VisualStudio.Package.AuthoringSink> tanımlayıcılar, yöntemler, eşleşen dil çiftleri (parantez ler ve parantezler gibi) ve dil üçlüsü (dil çiftlerine benzer, örneğin " "`foreach()`"`{`"`}`ve " ") gibi üç bölüm dışında bilgi toplar. Buna ek olarak, hata <xref:Microsoft.VisualStudio.Package.AuthoringSink> ayıklayıcının yüklenmesi gerekmemesi için kesme noktalarının erken doğrulamasında kullanılan kod tanımlamasını ve bir program hata ayıklanırken yerel değişkenleri ve parametreleri otomatik olarak gösteren ve hata ayıklayıcının sunduğuna ek olarak uygun yerel değişkenleri ve parametreleri tanımlamasını gerektiren **Otomatik hata** ayıklama penceresini desteklemek için sınıfı geçersiz kılabilirsiniz.

 Nesne, <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnenin bir parçası olarak ayrıştırıcıya <xref:Microsoft.VisualStudio.Package.AuthoringSink> aktarılır ve her yeni <xref:Microsoft.VisualStudio.Package.ParseRequest> nesne oluşturulduğunda yeni bir nesne oluşturulur. Buna ek <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olarak, yöntem <xref:Microsoft.VisualStudio.Package.AuthoringScope> çeşitli IntelliSense işlemleri işlemek için kullanılan bir nesne döndürmeniz gerekir. Nesne, <xref:Microsoft.VisualStudio.Package.AuthoringScope> ayrıştırma nedenine bağlı olarak, bildirimler için bir liste ve her ikisi de doldurulan yöntemler için bir liste tutar. Sınıf <xref:Microsoft.VisualStudio.Package.AuthoringScope> uygulanmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
