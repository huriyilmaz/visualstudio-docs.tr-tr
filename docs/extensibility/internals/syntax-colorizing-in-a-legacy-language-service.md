---
title: Eski Dil Hizmetinde Sözdizimi Renklendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704702"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
Sözdizimi renklendirme, bir programlama dilinin farklı öğelerinin kaynak dosyada farklı renk ve stillerde görüntülenmesine neden olan bir özelliktir. Bu özelliği desteklemek için, dosyadaki sözlü öğe veya belirteç türlerini tanımlayabilecek bir ayrıştırıcı veya tarayıcı sağlamanız gerekir. Birçok dil, anahtar kelimeleri, sınır aşanları (parantez ler veya ayraçlar gibi) ve yorumları farklı şekillerde renklendirerek ayırır.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Editör ve Dil Hizmetlerini Genişletme'ye](../../extensibility/extending-the-editor-and-language-services.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Renklendirmeyi desteklemek için yönetilen paket çerçevesi (MPF), <xref:Microsoft.VisualStudio.Package.Colorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi uygulayan sınıfı içerir. Bu sınıf belirteç ve renkleri belirlemek için bir <xref:Microsoft.VisualStudio.Package.IScanner> etkileşim. Tarayıcılar hakkında daha fazla bilgi [için, Bkz. Eski Dil Hizmeti Parser ve Tarayıcı.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) Sınıf <xref:Microsoft.VisualStudio.Package.Colorizer> daha sonra belirteçteki her karakteri renk bilgileriyle işaretler ve bu bilgileri kaynak dosyayı görüntüleyen düzenleyiciye döndürür.

 Düzenleyiciye döndürülen renk bilgileri, renklendirilebilir öğeler listesine dizindir. Her renklendirilebilir öğe, kalın veya vurucu gibi bir renk değeri ve yazı tipi öznitelikleri kümesi belirtir. Düzenleyici, dil hizmetinizin kullanabileceği varsayılan renklenebilir öğeler kümesi sağlar. Tek yapmanız gereken, her belirteç türü için uygun renk dizini belirtmektir. Ancak, belirteçler için sağladığınız özel renklendirilebilir öğeler ve endeksler kümesi sağlayabilir ve varsayılan liste yerine kendi renklenebilir öğeler listenize başvurun. `RequestStockColors` Ayrıca, özel renkleri desteklemek için kayıt defteri girişini `RequestStockColors` 0 olarak ayarlamanız (veya girişi hiç belirtmemeniz) gerekir. Bu kayıt defteri <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> girişini, kullanıcı tanımlı öznitelik için adlandırılmış bir parametreyle ayarlayabilirsiniz. Bir dil hizmetini kaydetme ve seçeneklerini ayarlama hakkında daha fazla bilgi için [bkz.](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler
 Kendi özel renklenebilir öğeleri sağlamak için, <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfta <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> ve yöntem geçersiz kılmanız gerekir. İlk yöntem, dil hizmetinin desteklediği özel renklenebilir öğelerin sayısını döndürür ve ikinci yöntem dizin tarafından özel renklendirilebilir öğeyi alır. Özel renklendirilebilir öğelerin varsayılan listesini oluşturursunuz. Dil hizmetinizin oluşturucusunda, tek yapmanız gereken her renklendirilebilir öğeye bir ad sağlamaktır. Visual Studio, kullanıcının farklı renklendirilebilir öğeler kümesi seçtiği kılıfı otomatik olarak işler. Bu ad, **Seçenekler** iletişim kutusundaki **Yazı Tipleri ve Renkler** özelliği sayfasında görünen (Visual Studio **Tools** menüsünden kullanılabilir) ve bu ad, kullanıcının hangi rengi geçersiz kıldığı belirler. Kullanıcının seçimleri kayıt defterindeki bir önbellekte depolanır ve renk adı tarafından erişilir. **Yazı Tipleri ve Renkler** özelliği sayfası tüm renk adlarını alfabetik sıraya göre listeler, böylece özel renklerinizi her renk adını dil adınız ile önce gruplayabilirsiniz; örneğin, "**TestLanguage- Comment**" ve "**TestLanguage- Anahtar Kelime**". Veya renklenebilir öğelerinizi türüne göre gruplayabilirsin, "**Yorum (TestDili)**" ve "**Anahtar Kelime (TestDili) "** Dil adına göre gruplandırma tercih edilir.

> [!CAUTION]
> Varolan renklendirilebilir öğe adlarıyla çakışmayı önlemek için dil adını renklendirilebilir öğe adına eklemeniz önerilir.

> [!NOTE]
> Geliştirme sırasında renklerinizden birinin adını değiştirirseniz, Visual Studio'nun renklerinize ilk erişiğinde oluşturduğu önbelleği sıfırlamanız gerekir. Bunu Visual Studio SDK program menüsünden **Deneysel Kovan Sıfırlama** komutunu çalıştırarak yapabilirsiniz.

 Renklenebilir öğeler listenizdeki ilk öğeye hiçbir zaman başvurulmadı. Visual Studio her zaman varsayılan metin renklerini ve özniteliklerini o öğe için sağlar. Bununla başa çıkmanın en kolay yolu, ilk öğe olarak bir yer tutucu renklendirilebilir madde sağlamaktır.

### <a name="high-color-colorable-items"></a>Yüksek Renkli Renklendirilebilir Öğeler
 Renklendirilebilir öğeler de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirim üzerinden 24 bit veya yüksek renk değerlerini destekleyebilir. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi destekler ve 24 bit renkler normal renklerle birlikte oluşturucuda belirtilir. Daha <xref:Microsoft.VisualStudio.Package.ColorableItem> fazla ayrıntı için sınıfa bakın. Aşağıdaki örnekte, anahtar kelimeler ve yorumlar için 24 bit renklerin nasıl ayarlanıliz gösterilmektedir. 24 bit renkler kullanıcının masaüstünde 24 bit renk desteklendiğinde kullanılır; aksi takdirde, normal metin renkleri kullanılır.

 Unutmayın, bunlar dilinizin varsayılan renkleridir; kullanıcı bu renkleri istedikleri şekilde değiştirebilir.

### <a name="example"></a>Örnek
 Bu örnek, sınıfı kullanarak bir dizi özel renklendirilebilir <xref:Microsoft.VisualStudio.Package.ColorableItem> öğeyi bildirmenin ve doldurmanın bir yolunu gösterir. Bu örnek, 24 bit renkleri kullanarak anahtar kelime ve yorum renklerini ayarlar.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Colorizer sınıf ve Tarayıcı
 Taban <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı anında ani yapan bir yöntemi vardır. <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Yöntemden döndürülen tarayıcı sınıf oluşturucuya <xref:Microsoft.VisualStudio.Package.Colorizer> geçirilir.

 Yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> kendi sürümünde uygulamanız gerekir. Sınıf, <xref:Microsoft.VisualStudio.Package.Colorizer> tüm belirteç renk bilgilerini elde etmek için tarayıcıyı kullanır.

 Tarayıcının bulduğu her <xref:Microsoft.VisualStudio.Package.TokenInfo> belirteç için bir yapı doldurması gerekiyor. Bu yapı, belirteç kaplar span, kullanılacak renk dizini, belirteç ne tür ve belirteç tetikleyicileri gibi bilgileri içerir (bkz. <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıf tarafından renklendirme için yalnızca açıklık ve renk dizini gereklidir.

 <xref:Microsoft.VisualStudio.Package.TokenInfo> Yapıda depolanan renk dizini genellikle numaralandırmadan <xref:Microsoft.VisualStudio.Package.TokenColor> gelen bir değerdir ve anahtar kelimeler ve işleçler gibi çeşitli dil öğelerine karşılık gelen bir dizi adlandırılmış indeks sağlar. Özel renklendirilebilir öğeler listeniz numaralandırmada <xref:Microsoft.VisualStudio.Package.TokenColor> sunulan öğelerle eşleşiyorsa, numaralandırmayı her belirteç için renk olarak kullanabilirsiniz. Ancak, ek renklendirilebilir öğeleriniz varsa veya varolan değerleri bu sırada kullanmak istemiyorsanız, gereksinimlerinize uyacak şekilde özel renklenebilir öğeler listenizi düzenleyebilir ve uygun dizini bu listeye döndürebilirsiniz. Sadece <xref:Microsoft.VisualStudio.Package.TokenInfo> yapıda depolarken bir <xref:Microsoft.VisualStudio.Package.TokenColor> dizin döküm emin olun; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] yalnızca dizini görür.

### <a name="example"></a>Örnek
 Aşağıdaki örnek, tarayıcının üç belirteç türünü nasıl tanımlayabileceğini gösterir: sayılar, noktalama işaretleri ve tanımlayıcılar (sayı veya noktalama işareti olmayan herhangi bir şey). Bu örnek yalnızca açıklayıcı amaçlar içindir ve kapsamlı bir ayrıştırıcı ve tarayıcı uygulamasını temsil etmez. Bir dize döndüren bir `GetNextToken()` yönteme sahip bir `Lexer` sınıf olduğunu varsayar.

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
