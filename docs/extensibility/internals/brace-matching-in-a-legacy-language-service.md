---
title: Eski Dil Hizmetinde Ayraç Eşleştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709814"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Eski bir dil hizmetinde ayraç eşleştirme
Ayraç eşleştirme, geliştiricinin parantez ler ve kıvırcık ayraçlar gibi birlikte gerçekleşmesi gereken dil öğelerini izlemesine yardımcı olur. Bir geliştirici bir kapanış ayracı girdiğinde, açılış ayracı vurgulanır.

 Çiftler ve üçlüler olarak adlandırılan iki veya üç birlikte oluşan öğeleri eşleştirebilirsiniz. Üçlüler üç birlikte oluşan elementkümesidir. Örneğin, `foreach` C#'da, ifade üçlü `foreach()`oluşturur: , , `{`ve `}`. Kapanış ayracı yazıldığında üç öğe de vurgulanır.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Ayraç eşleştirmesini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Bkz. Walkthrough: Ekran eşleştirme ayraçları.](../../extensibility/walkthrough-displaying-matching-braces.md)

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Sınıf <xref:Microsoft.VisualStudio.Package.AuthoringSink> hem çiftleri hem de <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> üçe katları ve <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metotlarla destekler.

## <a name="implementation"></a>Uygulama
 Dil hizmetinin dildeki tüm eşleşen öğeleri tanımlaması ve ardından eşleşen tüm çiftleri bulması gerekir. Bu genellikle eşleşen bir dili <xref:Microsoft.VisualStudio.Package.IScanner> algılamak için uygulayarak ve <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> daha sonra öğeleri eşleştirmek için yöntemi kullanarak gerçekleştirilir.

 Yöntem, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> satırı tokenize etmek ve belirteci bakımdan hemen önce döndürmek için tarayıcıyı çağırır. Tarayıcı, geçerli belirteç <xref:Microsoft.VisualStudio.Package.TokenTriggers> üzerinde bir belirteç tetikleyici değeri ayarlayarak bir dil öğesi çifti bulunduğunu gösterir. Yöntem, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> eşleşen <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> dil öğesini <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> bulmak <xref:Microsoft.VisualStudio.Package.ParseReason> için ayrışdırış neden değeri ile yöntemi çağıran yöntemi çağırır. Eşleşen dil öğesi bulunduğunda, her iki öğe vurgulanır.

 Ayraç yazmanın ayraç vurgulamayı nasıl tetiklediğinitam bir açıklama için, Eski [dil hizmeti parer ve tarayıcı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)makalesindeki *Örnek ayrıştırma işlemi* bölümüne bakın.

## <a name="enable-support-for-brace-matching"></a>Ayraç eşleştirme desteği etkinleştirme
 Öznitelik <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> **MatchBraces**ayarlayabilirsiniz , **MatchBracesAtCaret**, ve **ShowMatchingBrace** kayıt defteri <xref:Microsoft.VisualStudio.Package.LanguagePreferences> girişleri sınıfın ilgili özelliklerini ayarlayın. Dil tercihi özellikleri de kullanıcı tarafından ayarlanabilir.

|Kayıt defteri girişi|Özellik|Açıklama|
|--------------------|--------------|-----------------|
|Eşleştirme Ayraçları|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Ayraç eşleştirmesini sağlar.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Caret hareket ettikçe ayraç eşleştirmesini sağlar.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Eşleşen ayraç vurgular.|

## <a name="match-conditional-statements"></a>Koşullu ifadeleri eşleştir
 Koşullu ifadeleri eşleştirebilirsiniz, `if` `else if`örneğin `else`, `#if`, `#elif` `#else`veya `#endif`, , , , , , sınır layıcıları eşleştirdiği gibi. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Sınıfı alt sınıflayabilir ve eşleşen öğelerin iç dizine metin yayılmalarının yanı sıra sınırlayıcılar ekleyebileceğiniz bir yöntem sağlayabilirsiniz.

## <a name="set-the-trigger"></a>Tetiği ayarlama
 Aşağıdaki örnek, eşleşen parantezleri, kıvırcık ayraçları ve kare ayraçları nasıl algılayabildiğini ve tarayıcıda tetikleyicinin nasıl ayarlanışacağını gösterir. Sınıftaki <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> yöntem tetikleyiciyi algılar ve eşleşen çifti bulmak için ayrıştırıcıyı çağırır (bu *makaledeki eşleşmeyi bulma bölümüne* bakın). Bu örnek yalnızca açıklayıcı amaçlar içindir. Tarayıcınızın bir metin satırından `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Ayraçları eşleştirin
 Burada dil `{ }`öğeleri eşleştirme için basitleştirilmiş `( )`bir `[ ]`örnektir , , , <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve , , ve nesneye onların yayılmaları ekleme. Bu yaklaşım, kaynak kodu ayrıştırmak için önerilen bir yaklaşım değildir; sadece açıklayıcı amaçlar içindir.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski dil hizmeti parser ve tarayıcı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
