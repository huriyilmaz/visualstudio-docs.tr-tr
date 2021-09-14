---
title: Eski dil hizmetinde söz dizimi renklendirme | Microsoft Docs
description: Sözcük temelli öğelerin veya belirteçlerin türlerini belirleyebilen bir Ayrıştırıcı veya tarayıcı sağlayarak eski dil hizmetinde söz dizimi renklendirmesi desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 906f144c6414d5af9483b046f49e3f911b30d0c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626037"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
Sözdizimi renklendirme, farklı renklerde ve stillerde bir programlama dilinin farklı öğelerinin bir kaynak dosyada görüntülenmesine neden olan bir özelliktir. Bu özelliği desteklemek için, dosyadaki sözcük öğelerinin veya belirteçlerin türlerini belirleyebilen bir Ayrıştırıcı veya tarayıcı sağlamanız gerekir. Birçok dil, anahtar sözcükleri, sınırlayıcıları (parantezler veya küme ayraçları gibi) ve açıklamaları farklı yollarla renklendirileyerek yorumlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Renklendirme desteği için, yönetilen paket çerçevesi (MPF), <xref:Microsoft.VisualStudio.Package.Colorizer> arabirimini uygulayan sınıfını içerir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . Bu sınıf <xref:Microsoft.VisualStudio.Package.IScanner> , belirteç ve renklerin belirlenmesi için ile etkileşime girer. Tarayıcılar hakkında daha fazla bilgi için bkz. [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer>Bu sınıf, belirtecin her karakterini renk bilgileriyle işaretler ve kaynak dosyayı görüntüleyen düzenleyiciye bu bilgileri döndürür.

 Düzenleyiciye döndürülen renk bilgileri, renklenebilir öğeler listesinin bir dizinidir. Renklenebilir her öğe, bir renk değeri ve kalın veya üstü çizili gibi bir yazı tipi öznitelikleri kümesi belirtir. Düzenleyici, dil hizmetinizin kullanabileceği bir varsayılan renklenebilir öğeler kümesi sağlar. Yapmanız gereken tek şey, her belirteç türü için uygun renk dizinini belirtmektir. Ancak, özel renklenebilir öğeler ve belirteçler için sağladığınız dizinler kümesi sağlayabilir ve varsayılan liste yerine kendi renklenebilir öğeler listesine başvurabilirsiniz. Ayrıca, `RequestStockColors` özel renkleri desteklemek için kayıt defteri girişini 0 olarak ayarlamanız gerekir (veya herhangi bir girişi belirtmeniz gerekmez `RequestStockColors` ). Bu kayıt defteri girişini, Kullanıcı tanımlı özniteliğe adlandırılmış bir parametre ile ayarlayabilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Bir dil hizmetini kaydetme ve seçeneklerini ayarlama hakkında daha fazla bilgi için bkz. [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler
 Kendi özel renksiz öğelerinizi sağlamak için <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> sınıfında ve metodunu geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . İlk yöntem, dil hizmetinizin desteklediği özel renklenebilir öğelerin sayısını döndürür ve ikincisi dizine göre özel renklenebilir öğeyi alır. Özel renklenebilir öğelerin varsayılan listesini oluşturabilirsiniz. Dil hizmetinizin oluşturucusunda, tek yapmanız gereken, renklenebilir her öğe için bir ad sağlar. Visual Studio, kullanıcının farklı renklenebilir bir öğe kümesi seçtiği durumu otomatik olarak işler. bu ad, **seçenekler** iletişim kutusundaki (Visual Studio **araçlar** menüsünden kullanılabilir) **yazı tipi ve renkler** özellik sayfasında görünür ve bu ad, kullanıcının hangi renge geçersiz kılındığını belirler. Kullanıcının seçimleri, kayıt defterindeki bir önbellekte depolanır ve renk adından erişilir. **Yazı tipleri ve renkler** Özellik sayfası tüm renk adlarını alfabetik sırada listeler, böylece özel renklerinizi her renk adından önce dil adınızla gruplandırabilirsiniz; Örneğin, "**TestLanguage-Comment**" ve "**TestLanguage-anahtar sözcüğü**". Ya da renklenebilir öğelerinizi "**Comment (TestLanguage)**" ve "**anahtar sözcüğü (TestLanguage)**" türüne göre gruplandırabilirsiniz. Dil adına göre gruplandırma tercih edilir.

> [!CAUTION]
> Var olan renklenebilir öğe adlarıyla çarpışmalardan kaçınmak için, dil adını renklendirilebilir öğe adına eklemeniz önemle tavsiye edilir.

> [!NOTE]
> geliştirme sırasında renklerinizin birinin adını değiştirirseniz, renklerinizin ilk kez erişildiği Visual Studio oluşturulan önbelleği sıfırlamanız gerekir. bunu, Visual Studio SDK program menüsünden **deneysel Hive komutunu sıfırlayın** komutunu çalıştırarak yapabilirsiniz.

 Renklenebilir öğeler listenizdeki ilk öğenin hiçbir şekilde başvurulmadığını unutmayın. Visual Studio her zaman bu öğe için varsayılan metin renklerini ve özniteliklerini sağlar. Bunu yapmanın en kolay yolu, ilk öğe olarak yer tutucu renklenebilir bir öğe sağlamadır.

### <a name="high-color-colorable-items"></a>Yüksek renk Renklenebilir öğeler
 Renklenebilir öğeler, arabirim aracılığıyla 24 bit veya yüksek renk değerlerini de destekleyebilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> . MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimini destekler ve 24 bit renkler, Oluşturucu içinde normal renklerle birlikte belirtilir. <xref:Microsoft.VisualStudio.Package.ColorableItem>Daha fazla ayrıntı için sınıfına bakın. Aşağıdaki örnekte, anahtar sözcükler ve açıklamalar için 24 bit renklerin nasıl ayarlanacağı gösterilmektedir. 24 bit renkler, kullanıcının masaüstünde 24 bit renk desteklenmiş olduğunda kullanılır; Aksi takdirde, normal metin renkleri kullanılır.

 Bunların diliniz için varsayılan renkler olduğunu unutmayın; Kullanıcı bu renkleri istedikleri şeyle değiştirebilir.

### <a name="example"></a>Örnek
 Bu örnek, sınıfını kullanarak özel renklenebilir öğelerin dizisini bildirmek ve doldurmak için bir yol gösterir <xref:Microsoft.VisualStudio.Package.ColorableItem> . Bu örnekte, anahtar sözcüğü ve açıklama renkleri 24 bit renkler kullanılarak ayarlanır.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Colorizer sınıfı ve tarayıcı
 Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın, <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> sınıfı instantiantes bir yöntemi vardır <xref:Microsoft.VisualStudio.Package.Colorizer> . Yönteminden döndürülen tarayıcı <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.Colorizer> sınıf oluşturucusuna geçirilir.

 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>Yöntemi sınıfının kendi sürümüne uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService> . <xref:Microsoft.VisualStudio.Package.Colorizer>Sınıfı, tüm belirteç renk bilgilerini almak için tarayıcıyı kullanır.

 Tarayıcının <xref:Microsoft.VisualStudio.Package.TokenInfo> bulduğu her belirteç için bir yapıyı doldurması gerekir. Bu yapı, belirtecin kapladığı yayılma, kullanılacak renk dizini, hangi tür belirteci ve belirteç Tetikleyicileri gibi bilgiler içerir (bkz <xref:Microsoft.VisualStudio.Package.TokenTriggers> .). Sınıf tarafından renklendirme için yalnızca span ve Color dizini gereklidir <xref:Microsoft.VisualStudio.Package.Colorizer> .

 Yapıda depolanan renk dizini <xref:Microsoft.VisualStudio.Package.TokenInfo> genellikle <xref:Microsoft.VisualStudio.Package.TokenColor> Numaralandırmadaki bir değerdir ve bu, anahtar sözcükler ve işleçler gibi çeşitli dil öğelerine karşılık gelen bir dizi adlandırılmış dizin sağlar. Özel renklenebilir öğeler listeniz, numaralandırmada sunulan öğelerle eşleşiyorsa <xref:Microsoft.VisualStudio.Package.TokenColor> , numaralandırmayı her belirtecin rengi olarak kullanabilirsiniz. Ancak, daha fazla renklenebilir öğeleriniz varsa veya var olan değerleri bu sırada kullanmak istemiyorsanız, özel renklenebilir öğeler listenizi gereksinimlerinize uyacak şekilde düzenleyebilir ve ilgili dizini bu listeye döndürebilirsiniz. <xref:Microsoft.VisualStudio.Package.TokenColor>Yalnızca dizini yapıda depolarken dizini bir öğesine atamalısınız <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] .

### <a name="example"></a>Örnek
 Aşağıdaki örnek, tarayıcının üç belirteç türünü nasıl tanımlayabileceğini gösterir: sayılar, noktalama işaretleri ve tanımlayıcılar (sayı veya noktalama olmayan herhangi bir şey). Bu örnek yalnızca tanım amaçlıdır ve kapsamlı bir Ayrıştırıcı ve tarayıcı uygulamasını temsil etmez. Bir `Lexer` dize döndüren bir yöntem içeren bir sınıf olduğunu varsayar `GetNextToken()` .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
