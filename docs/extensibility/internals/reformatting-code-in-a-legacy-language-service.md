---
title: Eski Dil Hizmeti Hizmet Paketinde Kodu Yeniden | Microsoft Docs
description: Eski dil hizmeti için kaynak kodu yeniden Visual Studio etkinleştirme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2d0778b5f60abe8c72e12783fa65017d86c11aa7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159078"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kodu Yeniden Biçimlendirme

Kaynak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kodunda girintiler ve boşluk kullanımını normalleştirerek yeniden biçimlendirebilirsiniz. Bu, her satırın başına boşluk veya sekme eklemeyi, satırların arasına yeni satırlar eklemeyi veya boşlukları sekmeler veya sekmelerle boşluklarla değiştirmeyi içerebilir.

> [!NOTE]
> Yeni satır karakterleri eklemek veya silmek, kesme noktaları ve yer işaretleri gibi işaretçileri etkileyebilir, ancak boşluk veya sekme ekleme veya kaldırma, işaretçileri etkilemez.

Kullanıcılar, Düzenle menüsündeki Gelişmiş menüden Seçimi **Biçimlendir** veya **Belgeyi** Biçimlendir'i **seçerek** yeniden biçimlendirme **işlemi** başlatabilirsiniz. Bir kod parçacığı veya belirli bir karakter eklendiğinde yeniden düzenleme işlemi de tetiklenir. Örneğin, C# içinde bir kapanış ayracı yazarak eşleşen açık küme ayracı ile kapatma ayracı arasındaki her şey otomatik olarak uygun düzeyde girintilenir.

Dil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **hizmetine Biçim** Seçimi **veya** Belgeyi Biçimlendir komutunu gönderdiğinde, sınıfı sınıfında <xref:Microsoft.VisualStudio.Package.ViewFilter> yöntemini <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> <xref:Microsoft.VisualStudio.Package.Source> çağıran. Biçimlendirmeyi desteklemek için yöntemini geçersiz <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> kılmanız ve kendi biçimlendirme kodunuzu sağlamak gerekir.

## <a name="enabling-support-for-reformatting"></a>Yeniden Düzenleme desteğini etkinleştirme

Biçimlendirmeyi desteklemek `EnableFormatSelection` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` için, VSPackage'nızı kaydedirken parametresi olarak ayar olmalıdır. Bu, özelliğini <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> olarak `true` ayarlar. yöntemi <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> bu özelliğin değerini döndürür. True döndürürse, <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı çağrılır. <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>

## <a name="implementing-reformatting"></a>Yeniden Düzenlemeyi Uygulama

Yeniden düzenlemeyi uygulamak için sınıfından bir sınıf türetmeniz ve <xref:Microsoft.VisualStudio.Package.Source> yöntemini geçersiz kılmaniz <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> gerekir. nesnesi <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> biçimlendirilen aralığı açıklar ve nesne, zaman aralığı <xref:Microsoft.VisualStudio.Package.EditArray> üzerinde yapılan düzenlemeleri tutar. Bu aralığın belgenin tamamı olduğunu unutmayın. Ancak, süre içinde büyük olasılıkla birden çok değişiklik yapılmış olabilir, tüm değişiklikler tek bir eylemde geri alınamaz. Bunu yapmak için nesnesinde yapılan tüm değişiklikleri <xref:Microsoft.VisualStudio.Package.CompoundAction> sarmala (bu konudaki "CompoundAction Sınıfını Kullanma" bölümüne bakın).

### <a name="example"></a>Örnek

Aşağıdaki örnek, virgülden sonra bir sekme veya satırın sonunda yer almadıkça, seçimde her virgülden sonra tek bir boşluk olduğunu sağlar. Satırda son virgülden sonra gelen boşluklar silinir. Bu yöntemin yönteminden nasıl çağrıldılarını görmek için bu konudaki "CompoundAction Sınıfını Kullanma" bölümüne <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> bakın.

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

Kodun bir bölümünde yapılan tüm yeniden düzenleme işlemi tek bir eylemde geri alınamaz. Bu bir sınıf kullanılarak gerçek <xref:Microsoft.VisualStudio.Package.CompoundAction> olabilir. Bu sınıf, metin arabelleği üzerinde bir dizi düzenleme işlemi tek bir düzenleme işlemi içine sarmalar.

### <a name="example"></a>Örnek

Sınıfı nasıl kullanabileceğiniz hakkında bir örnek burada <xref:Microsoft.VisualStudio.Package.CompoundAction> vetir. Yönteminin bir örneği için bu konudaki "Biçimlendirme için Destek Uygulama" bölümündeki örneğine `DoFormatting` bakın.

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
