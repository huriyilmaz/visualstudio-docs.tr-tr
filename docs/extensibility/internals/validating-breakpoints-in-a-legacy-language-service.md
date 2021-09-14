---
title: Eski Dil Hizmeti hizmetlerinde Kesme Noktaları | Microsoft Docs
description: Hata ayıklayıcı başlamadan önce kesme noktaları doğrulamak için eski bir dil hizmetinde ValidateBreakpointLocation yöntemini geçersiz kılmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627284"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kesme Noktalarını Doğrulama
Kesme noktası, bir hata ayıklayıcıda çalışırken program yürütmenin belirli bir noktada durdurulacak olduğunu gösterir. Düzenleyici, kesme noktası için geçerli bir konum oluşturan değer hakkında bilgi sahibi olmadığınız için kullanıcı kaynak dosyanın herhangi bir satırına kesme noktası yer almaktadır. Hata ayıklayıcısı çalıştırıldıklarında, işaretlenmiş tüm kesme noktaları (bekleyen kesme noktaları olarak da adlandırılan) çalışan programda uygun konuma bağlı olur. Aynı zamanda kesme noktaları doğrulanır ve geçerli kod konumlarını işaretlemelerini sağlar. Örneğin, bir açıklamanın kesme noktası geçerli değildir çünkü kaynak kodda o konumda kod yoktur. Hata ayıklayıcısı geçersiz kesme noktaları devre dışı bırakıyor.

 Dil hizmeti görüntülenen kaynak kodu bildiği için hata ayıklayıcı başlamadan önce kesme noktaları doğrulanabilir. Kesme noktası için <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> geçerli bir konum belirten bir aralık dönmek üzere yöntemini geçersiz kılabilirsiniz. Kesme noktası konumu, hata ayıklayıcı başlatılana kadar doğrulanır, ancak hata ayıklayıcının yüklemesi beklenmeden kullanıcıya geçersiz kesme noktaları bildirilecek.

## <a name="implementing-support-for-validating-breakpoints"></a>Kesme Noktaları Doğrulama Desteği Uygulama

- yöntemine <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> kesme noktası konumu verilir. Uygulamanız konumun geçerli olup olmadığına karar vermeli ve kesme noktasıyla ilişkilendirilmiş kodu tanımlayan bir metin aralığı döndürerek bunu belirtsin.

- Konum <xref:Microsoft.VisualStudio.VSConstants.S_OK> geçerli ise veya geçerli değilse geri <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> dön.

- Kesme noktası geçerli ise metin aralığı kesme noktasıyla birlikte vurgulanır.

- Kesme noktası geçersizse durum çubuğunda bir hata iletisi görüntülenir.

### <a name="example"></a>Örnek
 Bu örnek, belirtilen konumdaki kodun (varsa) yayma süresi elde etmek için <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> ayrıştırıcıyı çağıran yönteminin uygulamasını gösterir.

 Bu örnekte, sınıfına metin yayma süresi doğrulayan ve geçerli bir kesme noktası konumu ise döndüren `GetCodeSpan` <xref:Microsoft.VisualStudio.Package.AuthoringSink> bir yöntem `true` ekleyebilirsiniz.

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
