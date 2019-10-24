---
title: Eski dil hizmetinde ana hat oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726170"
---
# <a name="outlining-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Ana Hat Oluşturma
Anahat oluşturma karmaşık bir programı bir genel bakış veya anahatta daraltmak mümkün kılar. Örneğin, C# tüm yöntemlerde tek bir satıra daraltılabilir ve yalnızca Yöntem imzası gösteriliyor. Ayrıca, yapılar ve sınıflar yalnızca yapıların ve sınıfların adlarını gösterecek şekilde daraltılabilirler. Tek bir yöntemin içinde, karmaşık mantık, yalnızca `foreach`, `if` ve `while` gibi yalnızca ilk satırı göstererek genel akışı göstermek için daraltılabilirler.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [Izlenecek yol: Ana hat](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="enabling-support-for-outlining"></a>Ana hat desteğini etkinleştirme
 @No__t_0 kayıt defteri girişi, otomatik anahat oluşturmayı etkinleştirmek için 1 olarak ayarlanır. Otomatik anahat oluşturma, gizli bölgeleri tanımlamak ve anahat oluşturma gliflerini göstermek için bir dosya yüklendiğinde veya değiştirildiğinde kaynağın tamamına bir ayrıştırmaya ayarlanır. Ayrıca, ana hat Kullanıcı tarafından el ile denetlenebilir.

 @No__t_0 kayıt defteri girişinin değeri, <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> özelliği aracılığıyla elde edilebilir. @No__t_0 kayıt defteri girişi, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> özniteliğine adlandırılmış bir parametre ile başlatılabilir (Ayrıntılar için [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) konusuna bakın).

## <a name="the-hidden-region"></a>Gizli bölge
 Ana hat sağlamak için dil hizmetinizin gizli bölgeleri desteklemesi gerekir. Bunlar, genişletilebilen veya daraltılabilen metnin yayılmıştır. Gizli bölgeler, küme ayraçları veya özel semboller gibi standart dil sembolleri ile sınırlandırılabilir. Örneğin, C# gizli bir bölgeyi sınırlandıran bir `#region` / `#endregion` çifti vardır.

 Gizli bölgeler, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> arabirimi olarak kullanıma sunulan gizli bir bölge yöneticisi tarafından yönetilir.

 Ana hat, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> arabiriminin gizli bölgelerini kullanır ve gizli bölgenin yayılımını, geçerli görünür durumu ve yayılma daraltıldığında görüntülenecek olan başlığı içerir.

 Dil hizmeti ayrıştırıcısı, gizli bölgeler için varsayılan davranışa sahip yeni bir gizli bölge eklemek için <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> yöntemini kullanır, ancak <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> yöntemi ana hattın görünüm ve davranışını özelleştirmenize olanak tanır. Gizli bölgeler gizli bölge oturumuna verildiğinde, dil hizmetinin gizli bölgelerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetir.

 Gizli bölge oturumunun ne zaman yok edildiğini, gizli bir bölgenin değiştirildiğini veya belirli bir gizli bölgenin görünür olduğundan emin olmanız gerekiyorsa, <xref:Microsoft.VisualStudio.Package.Source> sınıfından bir sınıf türetmeniz ve sırasıyla uygun yöntemleri, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> ve <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> geçersiz kılmanız gerekir.

### <a name="example"></a>Örnek
 Tüm küme ayraçları çiftleri için gizli bölgeler oluşturmaya yönelik basitleştirilmiş bir örnek aşağıda verilmiştir. Dilin ayraç eşleştirme sağladığı ve eşleştirilecek ayraçların en azından küme ayraçları ({ve}) içerdiğinden varsayılır. Bu yaklaşım yalnızca tanım amaçlıdır. Tam bir uygulama <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> durumlarının eksiksiz bir şekilde işlenmesini içermelidir. Bu örnek ayrıca <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> tercih `true` geçici olarak nasıl ayarlanacağını gösterir. Alternatif olarak, dil paketinizin `ProvideLanguageServiceAttribute` özniteliğinde adlandırılmış parametre `AutoOutlining` belirtmektir.

 Bu örnekte açıklamalar C# , dizeler ve değişmez değerler için kurallar varsayılır.

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