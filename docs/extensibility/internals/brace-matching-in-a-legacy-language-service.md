---
title: Eski Dil Hizmeti Hizmet HizmetLerinde Küme Ayracı Eşleştirme | Microsoft Docs
description: Parantezler ve küme ayraçları gibi birlikte gerçekleşmesi gereken dil öğelerini izlemenizi yardımcı olan eski dil hizmetlerinde küme ayracı eşleştirme hakkında bilgi edinmek.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e63f9c065e629d768e73cc0c9433c4467883597f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159158"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Eski dil hizmetlerinde küme ayracı eşleştirme
Küme ayracı eşleştirme, geliştiricinin parantezler ve küme ayraçları gibi birlikte gerçekleşmesi gereken dil öğelerini izlemesine yardımcı olur. Bir geliştirici kapanış ayracı girdiği zaman açılış ayracı vurgulanır.

 Çiftler ve üçlüler olarak adlandırılan iki veya üç birlikte oluşan öğeleri eşlersiniz. Üçlüler, birlikte oluşan üç öğeden oluşan kümelerdir. Örneğin, C# içinde deyimi `foreach` üçlü oluşturur: `foreach()` , ve `{` `}` . Kapanış ayracı yazılıyorken üç öğe de vurgulanır.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Küme ayracı eşleştirmeyi uygulamanın yeni yolu hakkında daha fazla bilgi için bkz. [Kılavuz: Eşleşen küme ayraçlarını görüntüleme.](../../extensibility/walkthrough-displaying-matching-braces.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 sınıfı, <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve yöntemleriyle hem çiftleri hem de <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> üçlüleri destekler.

## <a name="implementation"></a>Uygulama
 Dil hizmetinin, dille eşleşen tüm öğeleri tanımlaması ve ardından eşleşen tüm çiftleri bulması gerekir. Bu genellikle, eşanlı bir dili <xref:Microsoft.VisualStudio.Package.IScanner> algılamak için uygulama uygulanarak ve ardından öğeleriyle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> eşleşmek için yöntemi kullanılarak uygulanır.

 yöntemi, <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> satırı belirteçleştirmek ve belirteci caret'in hemen öncesinde geri almak için tarayıcıyı arar. Tarayıcı, geçerli belirteçte bir belirteç tetikleyici değeri ayar tarafından dil öğesi <xref:Microsoft.VisualStudio.Package.TokenTriggers> çiftinin bulun olduğunu gösterir. yöntemi, eşleşen dil öğesini bulmak için ayrıştırma nedeni değeriyle yöntemini <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> çağıran yöntemini çağırmıştır. Eşleşen dil öğesi bulunca her iki öğe de vurgulanır.

 Küme ayracı yazmanın küme ayracı vurgulamayı  tetiklemesine ilişkin eksiksiz bir açıklama için Eski dil hizmeti ayrıştırıcısı ve tarayıcısı makalesinde Örnek ayrıştırma [işlemi bölümüne bakın.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

## <a name="enable-support-for-brace-matching"></a>Küme ayracı eşleştirme desteğini etkinleştirme
 özniteliği, sınıfın karşılık gelen özelliklerini ayarlayan <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> **MatchBraces**, **MatchBracesAtCaret** ve **ShowMatchingBrace** kayıt defteri girdilerini <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ayarlayın. Dil tercihi özellikleri kullanıcı tarafından da ayarlandırabilirsiniz.

|Kayıt defteri girişi|Özellik|Açıklama|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Küme ayracı eşleştirmeyi sağlar.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Küme ayracı hareket etti olarak küme ayracı eşleştirmeyi sağlar.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Eşleşen küme ayracı vurgular.|

## <a name="match-conditional-statements"></a>Koşullu deyimleri eşleşme
 , ve veya , gibi koşullu deyimleri sınırlayıcıları `if` `else if` `else` `#if` `#elif` `#else` `#endif` eşleştirmeyle aynı şekilde eşleştirin. sınıfını alt sınıfa ekleyebilir ve eşleşen öğelerin iç dizisine metin aralıklarının yanı sıra <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınırlayıcılar ek bir yöntem sebilirsiniz.

## <a name="set-the-trigger"></a>Tetikleyiciyi ayarlama
 Aşağıdaki örnekte eşleşen parantezleri, küme ayraçlarını ve kare ayraçları algılama ve tarayıcıda bunun tetikleyicisi ayarlama işlemi gösterir. sınıfındaki yöntemi tetikleyiciyi algılar ve eşleşen çifti bulmak için ayrıştırıcıyı <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> çağırıyor *(bu makaledeki Eşleşmeyi* bulma bölümüne bakın). Bu örnek yalnızca açıklayıcı amaçlara yöneliktir. Tarayıcınızın, bir metin satırına göre `GetNextToken` belirteçleri tanımlayan ve döndüren bir yöntem içerdiğini varsayıyor.

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

## <a name="match-the-braces"></a>Küme ayraçlarını eşleşme
 Burada , ve dil öğelerini eşleştirmek ve bunların yayılmalarını nesnesine `{ }` `( )` eklemek için `[ ]` basitleştirilmiş bir örnek ve ardından yer <xref:Microsoft.VisualStudio.Package.AuthoringSink> almaktadır. Bu yaklaşım, kaynak kodu ayrıştırmak için önerilen bir yaklaşım değildir; Yalnızca açıklayıcı amaçlara yöneliktir.

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
