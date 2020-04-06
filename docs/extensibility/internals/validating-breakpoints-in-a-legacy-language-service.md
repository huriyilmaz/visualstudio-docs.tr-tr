---
title: Eski Dil Hizmetinde Kesme Noktalarını Doğrulama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704089"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kesme Noktalarını Doğrulama
Kesme noktası, hata ayıklamada çalıştırılırken program yürütmenin belirli bir noktada durdurulması gerektiğini gösterir. Düzenleyicinin kesme noktası için geçerli bir konum teşkil ettiği hakkında hiçbir bilgisi olmadığından, kullanıcı kaynak dosyadaki herhangi bir satıra bir kesme noktası yerleyebilir. Hata ayıklayıcı başlatıldığında, işaretli kesme noktalarının tümü (bekleyen kesme noktaları olarak adlandırılır) çalışan programdaki uygun konuma bağlanır. Aynı zamanda kesme noktaları, geçerli kod konumlarını işaretlediğinden emin olmak için doğrulanır. Örneğin, kaynak kodunda bu konumda kod olmadığından, bir açıklama üzerindeki kesme noktası geçerli değildir. Hata ayıklayıcı geçersiz kesme noktalarını devre dışı kılabilir.

 Dil hizmeti görüntülenen kaynak kodu bildiğinden, hata ayıklama başlatılmadan önce kesme noktalarını doğrulayabilir. Kesme noktası için <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> geçerli bir konum belirten bir yayılma alanı döndürmek için yöntemi geçersiz kılabilirsiniz. Hata ayıklayıcısı başlatıldığında kesme noktası konumu yine de doğrulanır, ancak kullanıcı hata ayıklayıcının yüklenmesini beklemeden geçersiz kesme noktaları bildirilir.

## <a name="implementing-support-for-validating-breakpoints"></a>Kesme Noktalarını Doğrulama desteği uygulama

- Yöntem, <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> kesme noktasının konumu verilir. Uygulamanız, konumun geçerli olup olmadığına karar vermeli ve kesme noktasıyla ilişkili kodu tanımlayan bir metin açıklığı döndürerek bunu belirtmelidir.

- Konum <xref:Microsoft.VisualStudio.VSConstants.S_OK> geçerliyse veya <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> geçerli değilse iade edin.

- Kesme noktası geçerliyse, metin açıklığı kesme noktasıyla birlikte vurgulanır.

- Kesme noktası geçersizse, durum çubuğunda bir hata iletisi görüntülenir.

### <a name="example"></a>Örnek
 Bu örnek, belirtilen <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> konumda kod açıklığı (varsa) elde etmek için ayrıştırıcı çağıran yöntemin bir uygulama gösterir.

 Bu örnek, `GetCodeSpan` <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfa metin açıklığı doğrulayan ve geçerli bir `true` kesme noktası konumu ysa döndüren bir yöntem eklediğinizi varsayar.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
