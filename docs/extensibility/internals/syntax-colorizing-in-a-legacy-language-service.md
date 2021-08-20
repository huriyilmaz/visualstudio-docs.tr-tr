---
title: Eski Dil Hizmeti Hizmet HizmetLerinde Söz Dizimi Renklendirmesi | Microsoft Docs
description: Eski dil hizmetlerinde söz dizimi renklendirmeyi desteklemek için sözcük öğelerinin veya belirteçlerin türlerini belirleyen bir ayrıştırıcı veya tarayıcıyı nasıl destekleyebilirsiniz?
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158846"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
Söz dizimi renklendirme, bir programlama dilinin farklı öğelerinin bir kaynak dosyada farklı renkler ve stiller olarak görüntülenebilir. Bu özelliği desteklemek için, dosyada sözcük sözcük öğelerinin veya belirteçlerin türlerini belirleyen bir ayrıştırıcı veya tarayıcı belirtebilirsiniz. Birçok dil anahtar sözcükleri, sınırlayıcıları (parantezler veya ayraçlar gibi) ve yorumları farklı şekillerde renklendirmek için ayırt ediyor.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Düzenleyiciyi ve Dil Hizmetlerini Genişletme.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementation"></a>Uygulama
 Renklendirmeyi desteklemek için yönetilen paket çerçevesi (MPF), <xref:Microsoft.VisualStudio.Package.Colorizer> arabirimini uygulayan sınıfını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> içerir. Bu sınıf, belirteci ve <xref:Microsoft.VisualStudio.Package.IScanner> renkleri belirlemek için ile etkileşime alır. Tarayıcılar hakkında daha fazla bilgi için [bkz. Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcı.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) Ardından sınıfı belirteci renk bilgileriyle işaretler ve bu bilgileri kaynak dosyayı <xref:Microsoft.VisualStudio.Package.Colorizer> görüntüleyen düzenleyiciye döndürür.

 Düzenleyiciye döndürülen renk bilgileri, renklenebilir öğeler listesinde yer alan bir dizindir. Renkleştirilebilir her öğe bir renk değeri ve kalın veya üzerinde çizili gibi bir dizi yazı tipi özniteliği belirtir. Düzenleyici, dil hizmetinizin kullanabileceği bir dizi varsayılan renkleştirilebilir öğe sağlar. Tek ihtiyacınız olan her belirteç türü için uygun renk dizinini belirtmektir. Ancak, belirteçler için temin edersiniz ve varsayılan liste yerine kendi renklenebilir öğeler listeniz başvurur ve özel renkleştirilebilir öğeler kümesi ve dizinler sekleyebilirsiniz. Ayrıca, özel renkleri desteklemek `RequestStockColors` için kayıt defteri girişini 0 olarak ayarlay(veya hiç `RequestStockColors` belirtmezseniz) gerekir. Bu kayıt defteri girdisini adlandırılmış bir parametreyle kullanıcı tanımlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> özniteliğine ayarlayın. Dil hizmetini kaydetme ve seçeneklerini ayarlama hakkında daha fazla bilgi için bkz. [Eski Dil Hizmeti Kaydetme.](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler
 Kendi özel renkleştirilebilir öğelerinizi sağlamak için sınıfında ve yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> geçersiz kılmanız <xref:Microsoft.VisualStudio.Package.LanguageService> gerekir. İlk yöntem, dil hizmetinizin desteklediği özel renklenebilir öğe sayısını döndürür ve ikinci yöntem dizine göre özel renklenebilir öğeyi alır. Özel renklenebilir öğelerin varsayılan listesini oluşturun. Dil hizmetinizin oluşturucusnda tek gereken renklendirilebilir her öğeyi bir adla sağlamaktır. Visual Studio, kullanıcının farklı bir renklenebilir öğe kümesi seçmesi durumunda otomatik olarak işlemesi gerekir. Bu ad, Seçenekler iletişim kutusundaki Yazı Tipleri  ve Renkler özellik sayfasında görünen  addır (Visual Studio Araçları menüsünden kullanılabilir) ve bu ad kullanıcının hangi rengi geçersiz k olduğunu belirler.  Kullanıcının seçimleri kayıt defterindeki bir önbellekte depolanır ve renk adıyla erişilir. Yazı **Tipleri ve Renkler** özellik sayfasında tüm renk adları alfabetik sırada listelemektedir. Bu nedenle, her renk adının öncesini dil adınızla yazarak özel renklerinizi gruplayabilirsiniz; örneğin, "**TestLanguage- Comment**" ve "**TestLanguage- Keyword**". Veya renkleştirilebilir öğelerinizi " Açıklama **(TestLanguage)**" ve " Anahtar Sözcük **(TestLanguage) " türüne göre gruplandırabilirsiniz.** Dil adına göre gruplama tercih edilir.

> [!CAUTION]
> Mevcut renkleştirilebilir öğe adlarında çakışmaları önlemek için dil adını renklendirmeli öğe adına dahil etmek kesinlikle önerilir.

> [!NOTE]
> Geliştirme sırasında renklerinden birinin adını değiştirirsanız, renklerinize ilk erişil Visual Studio oluşturulan önbelleği sıfırlamanız gerekir. Bunu yapmak için Visual Studio SDK programı menüsünden Deneysel **Hive'Visual Studio** sıfırla komutunu çalıştırabilirsiniz.

 Renkleştirilebilir öğeler listenizdeki ilk öğeye hiçbir zaman başvurulmay olduğunu unutmayın. Visual Studio her zaman bu öğe için varsayılan metin renklerini ve özniteliklerini sağlar. Bunu yapmanın en kolay yolu, ilk öğe olarak renklenebilir bir yer tutucu sağlamaktır.

### <a name="high-color-colorable-items"></a>Yüksek Renk Renklendirmeli Öğeler
 Renkleştirilebilir öğeler, arabirim aracılığıyla 24 bit veya yüksek renk değerlerini de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> desteklenebilir. MPF sınıfı arabirimini destekler ve oluşturucuda normal renklerle birlikte <xref:Microsoft.VisualStudio.Package.ColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 24 bit renkleri belirtilir. Daha fazla <xref:Microsoft.VisualStudio.Package.ColorableItem> ayrıntı için sınıfına bakın. Aşağıdaki örnekte anahtar sözcükler ve açıklamalar için 24 bit renklerin nasıl ayarlandır olduğu gösterilmiştir. 24 bit renkler, kullanıcının masaüstünde 24 bit renk destekleninken kullanılır; aksi takdirde, normal metin renkleri kullanılır.

 Bunların diliniz için varsayılan renkler olduğunu unutmayın; kullanıcı bu renkleri istediğiniz gibi değiştirebilir.

### <a name="example"></a>Örnek
 Bu örnek, sınıfını kullanarak bir dizi özel renklendirmeyi ve doldurmak için bir yol <xref:Microsoft.VisualStudio.Package.ColorableItem> gösterir. Bu örnek, 24 bit renkleri kullanarak anahtar sözcüğü ve açıklama renklerini ayarlar.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Colorizer sınıfı ve Tarayıcı
 Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın, <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> sınıfını örnek alan bir yöntemi <xref:Microsoft.VisualStudio.Package.Colorizer> vardır. yönteminden döndürülen tarayıcı <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> sınıf oluşturucuya <xref:Microsoft.VisualStudio.Package.Colorizer> geçir edilir.

 yöntemini sınıfının <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> kendi sürümüne uygulamanız <xref:Microsoft.VisualStudio.Package.LanguageService> gerekir. sınıfı, <xref:Microsoft.VisualStudio.Package.Colorizer> tüm belirteç renk bilgilerini almak için tarayıcıyı kullanır.

 Tarayıcının bulduğu her belirteç <xref:Microsoft.VisualStudio.Package.TokenInfo> için bir yapıyı doldurmak gerekir. Bu yapı, belirteci kapladığı süre, kullanmak için renk dizini, belirteç türü ve belirteç tetikleyicileri gibi bilgileri içerir (bkz. <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Sınıf tarafından renklendirme için yalnızca yayılma ve renk dizini <xref:Microsoft.VisualStudio.Package.Colorizer> gereklidir.

 Yapıda depolanan renk dizini genellikle, anahtar sözcükler ve işleçler gibi çeşitli dil öğelerine karşılık gelen bir dizi adlandırılmış dizin sağlayan numaralama <xref:Microsoft.VisualStudio.Package.TokenInfo> <xref:Microsoft.VisualStudio.Package.TokenColor> değeridir. Özel renklendirmeli öğeler listeniz, numaralamada sunulan öğelerle eşleştirilebilirse, her belirteci renk olarak yalnızca <xref:Microsoft.VisualStudio.Package.TokenColor> numaralama kullanabilirsiniz. Ancak, ek renklenebilir öğeleriniz varsa veya mevcut değerleri bu sırada kullanmak istemiyorsanız, özel renkleştirilebilir öğeler listenizi ihtiyaçlarınıza uyacak şekilde ayarlayabilir ve uygun dizini bu listeye geri getirebilirsiniz. Yalnızca dizinin yapısının içinde depolanması için dizinin bir dizinine at olduğundan <xref:Microsoft.VisualStudio.Package.TokenColor> <xref:Microsoft.VisualStudio.Package.TokenInfo> emin [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] olun.

### <a name="example"></a>Örnek
 Aşağıdaki örnekte, tarayıcının üç belirteç türü nasıl tanımlay olabileceği gösterir: sayılar, noktalama işaretleri ve tanımlayıcılar (sayı veya noktalama işareti değil her şey). Bu örnek yalnızca açıklayıcı amaçlara yöneliktir ve kapsamlı bir ayrıştırıcı ve tarayıcı uygulamasını temsil etmemektedir. Bir dize döndüren `Lexer` yöntemine sahip bir `GetNextToken()` sınıf olduğunu varsayıyor.

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
