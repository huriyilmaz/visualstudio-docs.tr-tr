---
title: Eski Dil Hizmetinde AnaHat | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706804"
---
# <a name="outlining-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Ana Hat Oluşturma
Anahat oluşturma, karmaşık bir programı genel bir bakış veya anahat olarak daraltmayı mümkün kılar. Örneğin, C#'da tüm yöntemler yalnızca yöntem imzasını göstererek tek bir satıra daraltılabilir. Buna ek olarak, yapılar ve sınıflar yalnızca yapıların ve sınıfların adlarını göstermek için daraltılabilir. Tek bir yöntem içinde, karmaşık mantık gibi ifadelerin yalnızca ilk satırı göstererek `foreach`genel `if`akışı `while`göstermek için daraltılabilir , ve .

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Walkthrough: Anahat'](../../extensibility/walkthrough-outlining.md)a bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="enabling-support-for-outlining"></a>AnaHat Desteği etkinleştirme
 Kayıt `AutoOutlining` defteri girişi otomatik anahat oluşturmayı etkinleştirmek için 1 olarak ayarlanır. Otomatik anahat, gizli bölgeleri tanımlamak ve anahat glifleri göstermek için bir dosya yüklendiğinde veya değiştirildiğinde tüm kaynağın ayrıştırMasını ayarlar. Anahat oluşturma da kullanıcı tarafından el ile kontrol edilebilir.

 Kayıt defteri `AutoOutlining` girişinin değeri <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıf üzerindeki <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> özellik üzerinden elde edilebilir. Kayıt `AutoOutlining` defteri girişi öznitelik için adlandırılmış bir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> parametre ile baş harfe olarak verilebilir (ayrıntılar için [Eski Dil Hizmeti Kaydetme'ye](../../extensibility/internals/registering-a-legacy-language-service1.md) bakınız).

## <a name="the-hidden-region"></a>Gizli Bölge
 Anahat sağlamak için dil hizmetinizin gizli bölgeleri desteklemesi gerekir. Bunlar genişletilebilen veya daraltılmış metin aralıklarıdır. Gizli bölgeler, kıvırcık ayraçlar gibi standart dil sembolleri veya özel sembollerle sınırlandırılabilir. Örneğin, C#'ın `#region` / `#endregion` gizli bir bölgeyi sınırlandıran bir çifti vardır.

 Gizli bölgeler, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> arabirim olarak ortaya çıkarılan gizli bir bölge yöneticisi tarafından yönetilir.

 Anahat, gizli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> bölgeleri arabirimi kullanır ve gizli bölgenin açıklarını, geçerli görünür durumu ve yayılma çöktüğünde gösterilecek banner'ı içerir.

 Dil hizmeti arayıcı, gizli bölgeler için varsayılan davranışiçeren yeni bir gizli bölge eklemek için <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> yöntemi kullanırken, <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> yöntem anahattın görünümünü ve davranışını özelleştirmenize olanak tanır. Gizli bölgeler gizli bölge oturumuna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verildikten sonra, dil hizmeti için gizli bölgeleri yönetir.

 Gizli bölge oturumunun ne zaman yok edildiğini belirlemeniz gerekiyorsa, gizli bir bölge değiştirilir veya belirli bir gizli bölgenin görünür olduğundan emin olmanız gerekir; sınıftan bir sınıf türetmeli ve uygun yöntemleri <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>geçersiz kılmanız gerekir, , , ve, <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>sırasıyla. <xref:Microsoft.VisualStudio.Package.Source>

### <a name="example"></a>Örnek
 Burada kıvırcık parantez tüm çiftleri için gizli bölgeler oluşturma basitleştirilmiş bir örnektir. Dilin ayraç eşleştirmesi sağladığı ve eşleşecek ayraçların en azından kıvırcık ayraçları ({ ve }) içerdiği varsayılır. Bu yaklaşım yalnızca açıklayıcı amaçlar içindir. Tam bir uygulama durumlarda tam bir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>işleme olurdu. Bu örnek, tercihin <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> `true` geçici olarak nasıl ayarlanını da gösterir. Alternatif olarak, dil `AutoOutlining` paketinizdeki öznitelikte `ProvideLanguageServiceAttribute` adlandırılmış parametrebelirtilir.

 Bu örnek, yorumlar, dizeleri ve literals için C# kuralları varsayar.

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
