---
title: Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705917"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme

Kaynak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kod girintiler ve beyaz boşluk kullanımını normalleştirerek yeniden biçimlendirilebilir. Bu, her satırın başına boşluk veya sekme eklemeyi veya kaldırmayı, satırlar arasına yeni satırlar eklemeyi veya boşlukları sekmelerle veya sekmelerle boşluklarla değiştirmeyi içerebilir.

> [!NOTE]
> Yeni çizgi karakterleri eklemek veya silerek kesme noktaları ve yer imleri gibi belirteçler etkileyebilir, ancak boşluk veya sekme eklemek veya kaldırmak işaretçileri etkilemez.

Kullanıcılar, **Düzenleme** menüsündeki **Gelişmiş** menüden **Biçim Seçimi** veya **Biçim Belgesi'ni** seçerek yeniden biçimlendirme işlemine başlayabilirler. Bir kod parçacığı veya belirli bir karakter eklendiğinde bir yeniden biçimlendirme işlemi de tetiklenebilir. Örneğin, C#'da bir kapanış ayracı yazdığınızda, eşleşen açık ayraç ile kapanış ayracı arasındaki her şey otomatik olarak uygun düzeye girintili.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Belgeyi Biçimle'yi** dil hizmetine biçimlendirme <xref:Microsoft.VisualStudio.Package.ViewFilter> **kattığında,** sınıf <xref:Microsoft.VisualStudio.Package.Source> sınıftaki <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> yöntemi çağırır. Biçimlendirmeyi desteklemek için yöntemi <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> geçersiz kılmanız ve kendi biçimlendirme kodunuzu sağlamanız gerekir.

## <a name="enabling-support-for-reformatting"></a>Yeniden Biçimlendirme ye Destek Sağlama

Biçimlendirmeyi desteklemek `EnableFormatSelection` için, VSPackage'ınızı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` kaydederken parametrenin ayarlanabilmesi gerekir. Bu <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> `true`özellik. Yöntem, <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> bu özelliğin değerini döndürür. Eğer doğru döndürürse, <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>sınıf .

## <a name="implementing-reformatting"></a>Yeniden Biçimlendirmenin Uygulanması

Yeniden biçimlendirmeyi uygulamak için <xref:Microsoft.VisualStudio.Package.Source> sınıftan bir sınıf türetmeniz ve yöntemi geçersiz kılmanız <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> gerekir. Nesne <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> biçime yayılma açıklanır <xref:Microsoft.VisualStudio.Package.EditArray> ve nesne açıklık üzerinde yapılan düzenleri tutar. Bu yayılma alanının belgenin tamamı olabileceğini unutmayın. Ancak, açıklıkta birden çok değişiklik yapılması olası olduğundan, tüm değişiklikler tek bir eylemde geri döndürülebilir olmalıdır. Bunu yapmak için, bir <xref:Microsoft.VisualStudio.Package.CompoundAction> nesnedeki tüm değişiklikleri sarın (bu konudaki "Bileşik Eylem Sınıfını Kullanma" bölümüne bakın).

### <a name="example"></a>Örnek

Aşağıdaki örnek, virgül bir sekme tarafından takip edilmedikçe veya satırın sonunda olmadığı sürece, seçimdeki her virgülden sonra tek bir boşluk olmasını sağlar. Bir satırdaki son virgülden sonra son daki boşluklar silinir. Bu yöntemin yöntemden nasıl çağrıldığını görmek için bu konudaki <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> "Bileşik Eylem Sınıfını Kullanma" bölümüne bakın.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>CompoundAction Sınıfını Kullanma

Kodun bir bölümünde yapılan tüm yeniden biçimlendirme tek bir eylemde geri döndürülebilir olmalıdır. Bu bir <xref:Microsoft.VisualStudio.Package.CompoundAction> sınıf kullanılarak gerçekleştirilebilir. Bu sınıf, metin arabelleği üzerinde bir dizi edit işlemleri tek bir bir edit işlemi içine sarar.

### <a name="example"></a>Örnek

Aşağıda sınıfın nasıl kullanılacağına <xref:Microsoft.VisualStudio.Package.CompoundAction> bir örnek verilmiştir. `DoFormatting` Yöntemörneği için bu konudaki "Biçimlendirme Desteği Uygulama" bölümündeki örneğe bakın.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Eski Dil Hizmeti Özellikleri](legacy-language-service-features1.md)
