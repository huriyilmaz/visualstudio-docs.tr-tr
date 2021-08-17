---
title: Eski Dil Hizmeti hizmetlerinde | Microsoft Docs
description: Eski bir dil hizmetine gizli bölgelerin uygulanmasıyla ilgili nasıl bir açıklama yapmayı destekley öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c9a4906b500d7c073f3f17d06e04b656f27be1fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049798"
---
# <a name="outlining-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Ana Hat Oluşturma
Ana hatlama, karmaşık bir programı genel bakış veya ana hat olarak daraltabilirsiniz. Örneğin, C# içinde tüm yöntemler tek bir satıra daraltarak yalnızca yöntem imzasını gösterebilirsiniz. Ayrıca yapılar ve sınıflar yalnızca yapıların ve sınıfların adlarını gösterecek şekilde daraltılmış olabilir. Tek bir yöntemin içinde, yalnızca , ve gibi deyimlerin ilk satırı göstererek genel akışı göstermek için `foreach` karmaşık mantık `if` daraltılmış `while` olabilir.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için bkz. [Adım adım kılavuz: Açıklama.](../../extensibility/walkthrough-outlining.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="enabling-support-for-outlining"></a>Outlining için Desteği Etkinleştirme
 Kayıt `AutoOutlining` defteri girişi, otomatik açıklamayı etkinleştirmek için 1 olarak ayarlanır. Otomatik açıklama, bir dosya yüklendiğinde veya değiştirerek gizli bölgeleri tanımlamak ve altı çizili glyph'leri göstermek için kaynağın tamamının ayrıştırıcılarını ayarlar. Outlining kullanıcı tarafından el ile de denetlenebilir.

 Kayıt defteri `AutoOutlining` girişinin değeri, sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> özelliği aracılığıyla elde <xref:Microsoft.VisualStudio.Package.LanguagePreferences> edilir. Kayıt `AutoOutlining` defteri girdisi özniteliğine adlandırılmış bir parametreyle <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> başlatabilirsiniz (ayrıntılar [için bkz. Eski Dil Hizmeti Kaydetme).](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="the-hidden-region"></a>Gizli Bölge
 Açıklama sağlamak için dil hizmetinizin gizli bölgeleri desteklemesi gerekir. Bunlar, genişletilen veya daraltılmış metin aralıklarıdır. Gizli bölgeler küme ayraçları gibi standart dil sembolleri veya özel sembollerle sınırlandırılmış olabilir. Örneğin, C# gizli `#region` / `#endregion` bir bölgeyi sınırlayıcı bir çifte sahip.

 Gizli bölgeler, arabirim olarak açık olan gizli bölge yöneticisi tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> yönetilir.

 Ana açıklama, arabiriminde gizli bölgeleri kullanır ve gizli bölgenin, geçerli görünür durumunun ve aralığın daraltılmış olduğu zaman <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> gösterilecek başlığı içerir.

 Dil hizmeti ayrıştırıcısı, gizli bölgeler için varsayılan davranışla yeni bir gizli bölge eklemek için yöntemini kullanır, yöntem ise ana hat görünümünü ve <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> davranışını özelleştirmenize olanak sağlar. Gizli bölgeler gizli bölge oturumuna verildiktan sonra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dil hizmeti için gizli bölgeleri yönetir.

 Gizli bölge oturumunun ne zaman yok olduğunu belirlemeniz gerekirse, gizli bir bölge değiştirilir veya belirli bir gizli bölgenin görünür olduğundan emin olun; sınıfından bir sınıf türetmeli ve sırasıyla uygun yöntemleri <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> , ve geçersiz <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> kılmanız gerekir.

### <a name="example"></a>Örnek
 Tüm küme ayraçları çiftleri için gizli bölgeler oluşturmaya örnek olarak basitleştirilmiş bir örnek verilmektedir. Dilin küme ayracı eşleştirme sağladığı varsayılır ve eşleştirilen küme ayraçları en azından küme ayraçlarını ({ ve }) içerir. Bu yaklaşım yalnızca açıklayıcı amaçlara yöneliktir. Tam bir uygulama, içinde durumların eksiksiz bir şekilde işlenmesine sahip <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> olur. Bu örnek ayrıca tercihin geçici olarak <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> nasıl `true` ayarlandırıldığını da gösterir. Alternatif olarak, dil `AutoOutlining` paketinizin özniteliğinde `ProvideLanguageServiceAttribute` adlandırılmış parametreyi belirtabilirsiniz.

 Bu örnekte açıklamalar, dizeler ve değişmez dizeler için C# kuralları varsayılmıştır.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
