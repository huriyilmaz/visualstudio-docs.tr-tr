---
title: Eski dil hizmetinde söz dizimi renklendirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19561363affada05154e15142bd32a30a5d051d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722827"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
Sözdizimi renklendirme, farklı renklerde ve stillerde bir programlama dilinin farklı öğelerinin bir kaynak dosyada görüntülenmesine neden olan bir özelliktir. Bu özelliği desteklemek için, dosyadaki sözcük öğelerinin veya belirteçlerin türlerini belirleyebilen bir Ayrıştırıcı veya tarayıcı sağlamanız gerekir. Birçok dil, anahtar sözcükleri, sınırlayıcıları (parantezler veya küme ayraçları gibi) ve açıklamaları farklı yollarla renklendirileyerek yorumlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Renklendirme desteği için, yönetilen paket çerçevesi (MPF), <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini uygulayan <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfını içerir. Bu sınıf, belirteç ve renkleri belirlemede bir <xref:Microsoft.VisualStudio.Package.IScanner> etkileşimde bulunur. Tarayıcılar hakkında daha fazla bilgi için bkz. [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, belirtecin her karakterini renk bilgileriyle işaretler ve kaynak dosyayı görüntüleyen düzenleyiciye bu bilgileri döndürür.

 Düzenleyiciye döndürülen renk bilgileri, renklenebilir öğeler listesinin bir dizinidir. Renklenebilir her öğe, bir renk değeri ve kalın veya üstü çizili gibi bir yazı tipi öznitelikleri kümesi belirtir. Düzenleyici, dil hizmetinizin kullanabileceği bir varsayılan renklenebilir öğeler kümesi sağlar. Yapmanız gereken tek şey, her belirteç türü için uygun renk dizinini belirtmektir. Ancak, özel renklenebilir öğeler ve belirteçler için sağladığınız dizinler kümesi sağlayabilir ve varsayılan liste yerine kendi renklenebilir öğeler listesine başvurabilirsiniz. Ayrıca, özel renkleri desteklemek için `RequestStockColors` kayıt defteri girişini 0 olarak ayarlamanız gerekir (veya hiçbir `RequestStockColors` girdisi belirtmemelidir). Bu kayıt defteri girişini, Kullanıcı tanımlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> özniteliğe adlandırılmış bir parametre ile ayarlayabilirsiniz. Bir dil hizmetini kaydetme ve seçeneklerini ayarlama hakkında daha fazla bilgi için bkz. [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler
 Kendi özel renklenebilir öğelerinizi sağlamak için <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfında <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> ve <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> yöntemini geçersiz kılmanız gerekir. İlk yöntem, dil hizmetinizin desteklediği özel renklenebilir öğelerin sayısını döndürür ve ikincisi dizine göre özel renklenebilir öğeyi alır. Özel renklenebilir öğelerin varsayılan listesini oluşturabilirsiniz. Dil hizmetinizin oluşturucusunda, tek yapmanız gereken, renklenebilir her öğe için bir ad sağlar. Visual Studio, kullanıcının farklı renklenebilir bir öğe kümesi seçtiği durumu otomatik olarak işler. Bu ad, **Seçenekler** iletişim kutusundaki (Visual Studio **Araçlar** menüsünden kullanılabilir) **yazı tipi ve renkler** Özellik sayfasında görünür ve bu ad, kullanıcının hangi renge geçersiz kılındığını belirler. Kullanıcının seçimleri, kayıt defterindeki bir önbellekte depolanır ve renk adından erişilir. **Yazı tipleri ve renkler** Özellik sayfası tüm renk adlarını alfabetik sırada listeler, böylece özel renklerinizi her renk adından önce dil adınızla gruplandırabilirsiniz; Örneğin, "**TestLanguage-Comment**" ve "**TestLanguage-anahtar sözcüğü**". Ya da renklenebilir öğelerinizi "**Comment (TestLanguage)** " ve "**anahtar sözcüğü (TestLanguage)** " türüne göre gruplandırabilirsiniz. Dil adına göre gruplandırma tercih edilir.

> [!CAUTION]
> Var olan renklenebilir öğe adlarıyla çarpışmalardan kaçınmak için, dil adını renklendirilebilir öğe adına eklemeniz önemle tavsiye edilir.

> [!NOTE]
> Geliştirme sırasında renklerinizin birinin adını değiştirirseniz, renklerinizin ilk kez eriştiği Visual Studio 'nun oluşturduğu önbelleği sıfırlamanız gerekir. Bunu, Visual Studio SDK program menüsünden **deneysel Hive komutunu sıfırlayın** komutunu çalıştırarak yapabilirsiniz.

 Renklenebilir öğeler listenizdeki ilk öğenin hiçbir şekilde başvurulmadığını unutmayın. Visual Studio her zaman bu öğe için varsayılan metin renklerini ve özniteliklerini sağlar. Bunu yapmanın en kolay yolu, ilk öğe olarak yer tutucu renklenebilir bir öğe sağlamadır.

### <a name="high-color-colorable-items"></a>Yüksek renk Renklenebilir öğeler
 Renklenebilir öğeler, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi aracılığıyla 24 bit veya yüksek renk değerlerini de destekleyebilir. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimini destekler ve 24 bit renkler, normal renklerle birlikte oluşturucuda belirtilir. Daha fazla ayrıntı için <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfına bakın. Aşağıdaki örnekte, anahtar sözcükler ve açıklamalar için 24 bit renklerin nasıl ayarlanacağı gösterilmektedir. 24 bit renkler, kullanıcının masaüstünde 24 bit renk desteklenmiş olduğunda kullanılır; Aksi takdirde, normal metin renkleri kullanılır.

 Bunların diliniz için varsayılan renkler olduğunu unutmayın; Kullanıcı bu renkleri istedikleri şeyle değiştirebilir.

### <a name="example"></a>Örnek
 Bu örnek, <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfını kullanarak özel renklenebilir öğelerin dizisini bildirmek ve doldurmak için bir yol gösterir. Bu örnekte, anahtar sözcüğü ve açıklama renkleri 24 bit renkler kullanılarak ayarlanır.

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
 Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfına instantiantes bir <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> yöntemine sahiptir. <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yönteminden döndürülen tarayıcı <xref:Microsoft.VisualStudio.Package.Colorizer> sınıf oluşturucusuna geçirilir.

 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfının kendi sürümünüze uygulamanız gerekir. <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, tüm belirteç renk bilgilerini almak için tarayıcıyı kullanır.

 Tarayıcının bulduğu her belirteç için bir <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısını doldurması gerekir. Bu yapı, belirtecin kapladığı yayılma, kullanılacak renk dizini, hangi tür belirteç ve belirteç Tetikleyicileri gibi bilgileri içerir (bkz. <xref:Microsoft.VisualStudio.Package.TokenTriggers>). <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı tarafından renklendirme için yalnızca span ve Color dizini gereklidir.

 <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısında depolanan renk dizini genellikle, anahtar sözcükler ve işleçler gibi çeşitli dil öğelerine karşılık gelen bir dizi adlandırılmış dizin sağlayan <xref:Microsoft.VisualStudio.Package.TokenColor> numaralandırmasındaki bir değerdir. Özel renklenebilir öğeler listeniz <xref:Microsoft.VisualStudio.Package.TokenColor> numaralandırmada sunulan öğelerle eşleşiyorsa, numaralandırmayı her belirtecin rengi olarak kullanabilirsiniz. Ancak, daha fazla renklenebilir öğeleriniz varsa veya var olan değerleri bu sırada kullanmak istemiyorsanız, özel renklenebilir öğeler listenizi gereksinimlerinize uyacak şekilde düzenleyebilir ve ilgili dizini bu listeye döndürebilirsiniz. Dizini <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısında depolarken bir <xref:Microsoft.VisualStudio.Package.TokenColor> dönüştürmeyi unutmayın; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] yalnızca dizini görür.

### <a name="example"></a>Örnek
 Aşağıdaki örnek, tarayıcının üç belirteç türünü nasıl tanımlayabileceğini gösterir: sayılar, noktalama işaretleri ve tanımlayıcılar (sayı veya noktalama olmayan herhangi bir şey). Bu örnek yalnızca tanım amaçlıdır ve kapsamlı bir Ayrıştırıcı ve tarayıcı uygulamasını temsil etmez. Bir dize döndüren bir `GetNextToken()` yöntemi olan `Lexer` bir sınıf olduğunu varsayar.

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