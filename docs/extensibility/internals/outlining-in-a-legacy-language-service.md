---
title: Eski dil hizmetinde ana hat oluşturma | Microsoft Docs
description: Eski dil hizmetindeki gizli bölgelerin uygulanmasıyla ana hattı oluşturmayı nasıl destekleyeceğinizi öğrenin.
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
ms.openlocfilehash: 73b2adbc6dbaab22d5d1888b42db3c0256e31846dcd1633241c6faae7b74a3ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414642"
---
# <a name="outlining-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Ana Hat Oluşturma
Anahat oluşturma karmaşık bir programı bir genel bakış veya anahatta daraltmak mümkün kılar. Örneğin, C# ' de tüm yöntemler tek bir satıra daraltılabilir ve yalnızca Yöntem imzası gösteriliyor. Ayrıca, yapılar ve sınıflar yalnızca yapıların ve sınıfların adlarını gösterecek şekilde daraltılabilirler. Tek bir yöntemin içinde,, ve gibi yalnızca ilk bir deyim göstererek genel akışı göstermek için karmaşık mantık daraltılabilir `foreach` `if` `while` .

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [Izlenecek yol: Ana hat](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="enabling-support-for-outlining"></a>Ana hat desteğini etkinleştirme
 `AutoOutlining`Otomatik anahat oluşturmayı etkinleştirmek için kayıt defteri girdisi 1 olarak ayarlanır. Otomatik anahat oluşturma, gizli bölgeleri tanımlamak ve anahat oluşturma gliflerini göstermek için bir dosya yüklendiğinde veya değiştirildiğinde kaynağın tamamına bir ayrıştırmaya ayarlanır. Ayrıca, ana hat Kullanıcı tarafından el ile denetlenebilir.

 `AutoOutlining`Kayıt defteri girişinin değeri, sınıfındaki özelliği aracılığıyla elde edilebilir <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . `AutoOutlining`Kayıt defteri girişi, özniteliğe adlandırılmış bir parametre ile başlatılabilir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (Ayrıntılar Için [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) konusuna bakın).

## <a name="the-hidden-region"></a>Gizli bölge
 Ana hat sağlamak için dil hizmetinizin gizli bölgeleri desteklemesi gerekir. Bunlar, genişletilebilen veya daraltılabilen metnin yayılmıştır. Gizli bölgeler, küme ayraçları veya özel semboller gibi standart dil sembolleri ile sınırlandırılabilir. Örneğin, C# ' ın `#region` / `#endregion` gizli bir bölgeyi sınırlandıran bir çifti vardır.

 Gizli bölgeler, arabirim olarak ortaya çıkarılan bir gizli bölge yöneticisi tarafından yönetilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> .

 Ana hat, gizli bölgeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> arabirimini kullanır ve gizli bölge, geçerli görünür durum ve yayılma daraltıldığında görüntülenecek olan başlığı içerir.

 Dil hizmeti ayrıştırıcısı, <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Gizli bölgeler için varsayılan davranışa sahip yeni bir gizli bölge eklemek için yöntemini kullanır, ancak <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Yöntem anahattın görünümünü ve davranışını özelleştirmenize olanak sağlar. Gizli bölgeler gizli bölge oturumuna verildiğinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dil hizmetinin gizli bölgelerini yönetir.

 Gizli bölge oturumunun ne zaman yok edildiğini, gizli bir bölgenin değiştirildiğini veya belirli bir gizli bölgenin görünür olduğundan emin olmanız gerekiyorsa, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.Source> ve sırasıyla uygun yöntemleri,,, ve geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> .

### <a name="example"></a>Örnek
 Tüm küme ayraçları çiftleri için gizli bölgeler oluşturmaya yönelik basitleştirilmiş bir örnek aşağıda verilmiştir. Dilin ayraç eşleştirme sağladığı ve eşleştirilecek ayraçların en azından küme ayraçları ({ve}) içerdiğinden varsayılır. Bu yaklaşım yalnızca tanım amaçlıdır. Tam bir uygulama, içindeki servis taleplerinin eksiksiz bir şekilde işlenmesini içermelidir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Bu örnek ayrıca <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> tercihi geçici olarak nasıl ayarlayagösterdiğini gösterir `true` . Alternatif olarak, `AutoOutlining` dil paketinizin özniteliğinde adlandırılmış parametresini belirtmektir `ProvideLanguageServiceAttribute` .

 Bu örnekte, açıklamalar, dizeler ve değişmez değerler için C# kuralları varsayılır.

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
