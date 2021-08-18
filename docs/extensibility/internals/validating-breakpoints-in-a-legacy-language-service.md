---
title: Eski dil hizmetinde kesme noktaları doğrulanıyor | Microsoft Docs
description: Hata ayıklayıcı başlamadan önce kesme noktalarını doğrulamak için bir eski dil hizmetindeki ValidateBreakpointLocation metodunu nasıl geçersiz kılabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 29ab2cc7d33dc4ec94759fce2ddb9d2335688ed4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034545"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kesme Noktalarını Doğrulama
Bir kesme noktası, program yürütmenin bir hata ayıklayıcıda çalıştırılırken belirli bir noktada durması gerektiğini belirtir. Düzenleyici, bir kesme noktası için geçerli bir konum oluşturduğunu hiçbir bilgisine sahip olmadığından, bir Kullanıcı, kaynak dosyadaki herhangi bir satıra bir kesme noktası yerleştirebilir. Hata ayıklayıcı başlatıldığında, işaretlenmiş kesme noktaları (bekleyen kesme noktaları olarak adlandırılır), çalışan programdaki uygun konuma bağlanır. Aynı zamanda, kesme noktaları geçerli kod konumlarını işaretdıklarından emin olmak için onaylanır. Örneğin, kaynak kodda bu konumda kod bulunmadığından, bir yorum üzerinde bir kesme noktası geçerli değildir. Hata ayıklayıcı geçersiz kesme noktalarını devre dışı bırakır.

 Dil hizmeti, görüntülenmekte olan kaynak kodu öğrendiğinden, hata ayıklayıcı başlatılmadan önce kesme noktalarını doğrulayabilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Bir kesme noktası için geçerli bir konum belirten bir span döndürmek için yöntemini geçersiz kılabilirsiniz. Hata ayıklayıcı başlatıldığında kesme noktası konumu hala doğrulanıyor, ancak kullanıcıya hata ayıklayıcının yüklenmesini beklemeden geçersiz kesme noktaları bildirilir.

## <a name="implementing-support-for-validating-breakpoints"></a>Kesme noktalarını doğrulama desteği uygulama

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Yöntemine, kesme noktasının konumu verilir. Uygulamanızın, konumun geçerli olup olmadığına karar vermeniz ve bu işlemi, kesme noktası konumuyla ilişkili kodu tanımlayan bir metin yayılımını belirterek göstermek gerekir.

- <xref:Microsoft.VisualStudio.VSConstants.S_OK>Konum geçerliyse veya <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> geçerli değilse döndürün.

- Kesme noktası geçerliyse, metin aralığı kesme noktasıyla birlikte vurgulanır.

- Kesme noktası geçersizse durum çubuğunda bir hata iletisi görüntülenir.

### <a name="example"></a>Örnek
 Bu örnek, <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> belirtilen konumdaki kodun (varsa) yayılmasını elde etmek için Ayrıştırıcıyı çağıran metodun bir uygulamasını gösterir.

 Bu örnek `GetCodeSpan` <xref:Microsoft.VisualStudio.Package.AuthoringSink> , sınıfa metin yayılımını doğrulayan ve `true` geçerli bir kesme noktası konumu ise döndüren bir yöntem eklediğinizi varsayar.

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
