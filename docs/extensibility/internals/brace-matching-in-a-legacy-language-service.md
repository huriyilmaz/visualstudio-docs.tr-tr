---
title: Eski dil hizmetinde küme ayracı eşleştirme | Microsoft Docs
description: Parantez ve küme ayraçları gibi, birlikte oluşması gereken dil öğelerini izlemenize yardımcı olan eski dil hizmetinde küme ayracı eşleştirmesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a92a3ca34e6314463bbfecbd8c4236789f213635
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086111"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Eski dil hizmetindeki küme ayracı eşleştirme
Ayraç eşleştirme, geliştiricinin parantez ve küme ayraçları gibi bir arada gerçekleşmesi gereken dil öğelerini izlemesine yardımcı olur. Bir geliştirici bir kapanış ayracı girdiğinde, açma küme ayracı vurgulanır.

 Çiftler ve üçlü olarak adlandırılan iki veya üç birlikte bulunan öğeyi eşleştirebilirsiniz. Üçlü, üç ortak bulunan öğe kümeleridir. Örneğin, C# ' de, `foreach` ifadeyi Üçlü: `foreach()` , `{` ve olarak oluşturur `}` . Kapanış ayracı yazıldığında, üç öğe de vurgulanır.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Ayraç eşleştirmeyi kullanmanın yeni yolu hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: eşleşen ayraçları görüntüleme](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Sınıfı, ve yöntemleriyle hem çiftleri hem de engelleri destekler <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> .

## <a name="implementation"></a>Uygulama
 Dil hizmetinin, dildeki tüm eşleşen öğeleri tanımlaması ve ardından eşleşen tüm çiftleri bulması gerekir. Bu, genellikle <xref:Microsoft.VisualStudio.Package.IScanner> eşleşen bir dili tespit etmek ve daha sonra <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> öğeleri eşlemek için metodunu kullanarak gerçekleştirilir.

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Yöntemi, satırı simgeleştirmek için tarayıcıyı çağırır ve yalnızca giriş işaretinden önce belirteci döndürür. Tarayıcı, geçerli belirteçte bir belirteç tetikleyici değeri ayarlanarak bir dil öğesi çiftinin bulunduğunu gösterir <xref:Microsoft.VisualStudio.Package.TokenTriggers> . <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Yöntemi, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> eşleşen dil öğesini bulmak için yöntemi ayrıştırma neden değeri ile çağıran yöntemi çağırır. Eşleşen dil öğesi bulunduğunda her iki öğe de vurgulanır.

 Küme ayracı yazmanın, küme ayracı vurgulamasını nasıl tetiklediği hakkında ayrıntılı bir açıklama için, [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)makalesindeki *örnek ayrıştırma işlemi* bölümüne bakın.

## <a name="enable-support-for-brace-matching"></a>Küme ayracı eşleştirmesi desteğini etkinleştir
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>Özniteliği, sınıfının karşılık gelen özelliklerini ayarlayarak **matchayraçları**, **matchbracesatını** ve **showmatchingayraç** kayıt defteri girişlerini ayarlayabilir <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . Dil tercihi özellikleri Kullanıcı tarafından da ayarlanabilir.

|Kayıt defteri girdisi|Özellik|Açıklama|
|--------------------|--------------|-----------------|
|Matchparantezleri|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Küme ayracı eşleştirmeyi izin vermez.|
|Matchbracesatşapka|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Giriş işareti ile eşleşen küme ayracı eşleşmesini izin eder.|
|Showmatchingayracın|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Eşleşen küme ayracını vurgular.|

## <a name="match-conditional-statements"></a>Koşullu deyimleri Eşleştir
 ,,, Veya,,,, ve gibi koşullu deyimleri `if` `else if` `else` `#if` `#elif` `#else` `#endif` eşleşen sınırlayıcılarla aynı şekilde eşleştirebilirsiniz. Sınıfının sınıfını oluşturabilir <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve metin yayılmaları ve eşleşen öğelerin iç dizisine sınırlayıcılar eklemek için bir yöntem sağlayabilirsiniz.

## <a name="set-the-trigger"></a>Tetikleyiciyi ayarla
 Aşağıdaki örnek, eşleşen parantezler, küme ayraçları ve kare ayracın nasıl algılanacağını ve tarayıcıda onun için tetikleyiciyi ayarlamayı gösterir. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> Sınıftaki yöntem tetikleyiciyi algılar ve eşleşen çifti bulmak için ayrıştırıcısı çağırır (Bu makaledeki *eşleştirmeyi bulma* bölümüne bakın). Bu örnek yalnızca tanım amaçlıdır. Tarayıcınızın bir `GetNextToken` metin satırından belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayar.

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

## <a name="match-the-braces"></a>Küme ayraçlarını Eşleştir
 İşte,, ve ' dil öğelerini eşleştirmek için basitleştirilmiş bir örnek, `{ }` `( )` ve bu nesnelerin içine `[ ]` yayılmaları ekleniyor <xref:Microsoft.VisualStudio.Package.AuthoringSink> . Bu yaklaşım, kaynak kodu ayrıştırmak için önerilen bir yaklaşım değildir; yalnızca tanım amaçlıdır.

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
- [Eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
