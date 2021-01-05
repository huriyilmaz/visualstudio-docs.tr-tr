---
title: Eski dil hizmetinde kodu yeniden biçimlendirme | Microsoft Docs
description: Visual Studio eski dil hizmeti için kaynak kodu yeniden biçimlendirme desteğini etkinleştirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3fcd9871cb0eeec69b98ada83af15f0daa624cb4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875368"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kaynak kodunda, girintili ve boşluk kullanımı normalleştirilerek yeniden biçimlendirilmesi yapılabilir. Bu, her satırın başlangıcında boşluk veya sekme ekleme veya kaldırma, satırlar arasına yeni satır ekleme veya boşluk içeren sekmeler veya sekmeler ile boşluk değiştirme içerebilir.

> [!NOTE]
> Yeni satır karakterlerini ekleme veya silme kesme noktaları ve yer işaretleri gibi işaretçileri etkileyebilir, ancak boşluk veya sekme ekleme veya kaldırma işaretçileri etkilemez.

Kullanıcılar **düzenleme** menüsündeki **Gelişmiş** menüsünden **seçimi Biçimlendir** veya **belgeyi Biçimlendir** ' i seçerek yeniden biçimlendirme işlemi başlatabilir. Bir kod parçacığı veya belirli bir karakter eklendiğinde yeniden biçimlendirme işlemi de tetiklenebilir. Örneğin, C# ' de bir kapanış küme ayracı yazdığınızda, eşleşen açma ayracı ve kapatma küme ayracı arasındaki her şey otomatik olarak uygun düzeye girintilenir.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Biçim Seçimi** veya biçim **belgesi** komutunu dil hizmetine gönderdiğinde, <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> sınıfındaki yöntemini çağırır <xref:Microsoft.VisualStudio.Package.Source> . Biçimlendirmeyi desteklemek için yöntemini geçersiz kılmanız <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> ve kendi biçimlendirme kodunuzu sağlamanız gerekir.

## <a name="enabling-support-for-reformatting"></a>Yeniden biçimlendirme desteğini etkinleştirme

Biçimlendirmeyi desteklemek için, `EnableFormatSelection` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> VSPackage 'u kaydettiğinizde parametresinin parametresi olarak ayarlanması gerekir `true` . Bu, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> özelliğini olarak ayarlar `true` . <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>Yöntemi bu özelliğin değerini döndürür. True döndürürse, <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı öğesini çağırır <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

## <a name="implementing-reformatting"></a>Yeniden biçimlendirme uygulama

Yeniden biçimlendirme uygulamak için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.Source> ve yöntemi geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>Nesnesi biçimlendirilecek yayılımı açıklar ve <xref:Microsoft.VisualStudio.Package.EditArray> nesne, yayılma üzerinde yapılan düzenlemeleri içerir. Bu yayılımın tüm belge olabileceğini unutmayın. Ancak, yayılmak için birden fazla değişiklik yapılması olası olduğundan, tüm değişiklikler tek bir eylemde geri alınamaz. Bunu yapmak için, bir nesnedeki tüm değişiklikleri sarmalayın <xref:Microsoft.VisualStudio.Package.CompoundAction> (Bu konunun "Compoundavction sınıfını kullanma" bölümüne bakın).

### <a name="example"></a>Örnek

Aşağıdaki örnek, virgülden sonra bir sekme izlenmediği veya satırın sonunda olmadığından, seçimdeki her virgülden sonra tek bir boşluk olmasını sağlar. Satırdaki son virgülden sonra sondaki boşluklar silinir. Bu yöntemin yöntemden nasıl çağrıldığını görmek için, bu konunun "Compoundadction sınıfını kullanma" bölümüne bakın <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .

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

## <a name="using-the-compoundaction-class"></a>Compoundadction sınıfını kullanma

Kodun bir bölümünde yapılan yeniden biçimlendirme işlemi, tek bir eylemde geri alınamaz. Bu, bir sınıf kullanılarak gerçekleştirilebilir <xref:Microsoft.VisualStudio.Package.CompoundAction> . Bu sınıf, metin arabelleğindeki bir düzenleme işlemleri kümesini tek bir düzenleme işleminde kaydırır.

### <a name="example"></a>Örnek

Sınıfının nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir <xref:Microsoft.VisualStudio.Package.CompoundAction> . Yöntemine bir örnek için, bu konunun "biçimlendirme için destek uygulama" bölümündeki örneğe bakın `DoFormatting` .

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
